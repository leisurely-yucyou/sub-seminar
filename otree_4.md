# サブゼミ oTree勉強会　第四回

## 本日の内容

- [囚人のジレンマゲームの作成](#囚人のジレンマゲームの作成)

### 前回の内容
- アンケートの作成

## 囚人のジレンマゲームの作成

#### アプリの作成
```cd D:\otree_sub_semi\subsemi_1```
- コマンドプロンプトの現在のディレクトリをotreeの作業ディレクトリにします。  

```otree startapp prisoners_dilemma```
- prisoners_dilemmaというアプリフォルダを作成します。  

### 今回のアプリ作成の手順
1. \_\_init__.py 内のmodels
2. HTMLファイル
3. \_\_init__.py 内のpages
4. アプリの登録

### models

#### Constantsクラスの定義
- prisoners_dilemmaフォルダ内の\_\_init__.pyを開きます。

```
class C(BaseConstants):
    NAME_IN_URL = 'prisoners_dilemma'
    PLAYERS_PER_GROUP = 2 # 2人一組でおこなう
    NUM_ROUNDS = 1 # 1ラウンドのみ
    INSTRUCTIONS_TEMPLATE = 'prisoner/instructions.html'
    PAYOFF_A = 2000 # 自分が裏切り、あいては協力
    PAYOFF_B = 1000 # 2人とも協力
    PAYOFF_C = 500  # 2人とも裏切り
    PAYOFF_D = 0    # 自分が協力、あいては裏切り
```


#### Playerクラスの定義

```
class Player(BasePlayer):
    cooperate = models.BoolenField(
        choices=[[True, '協力する'], [False,'裏切る']],
        widget=wigets.RadioSelect,
    )
```

___
- choicesは```[value, display]```というリストを用いることで表示する名前と使う値を違うものに設定することができます。
- 詳しくは[oTree公式マニュアル](https://otree.readthedocs.io/en/latest/forms.html#choices)
___

#### Groupクラスの定義
- このアプリではプレイヤー同士の活動・やりとりはないので特に定義しません。

```
class Group(BaseGroup):
    pass
```

#### Subsessionクラスの定義
- このアプリではプレイヤー同士の活動・やりとりがないので特に定義しません。

```
class Subsession(BaseSubsession):
    pass
```

#### 計算に用いる関数の定義
- other_playerでは相手となるプレイヤーのIDを取得します。
```
def other_player(player: Player):
    return player.get_others_in_group()[0]
```

- set_payoffではプレイヤーの利得の計算をおこないます。
```
def set_payoff(player: Player):
    payoff_matrix = {
        (False, True): C.PAYOFF_A,
        (True, True): C.PAYOFF_B,
        (True, False): C.PAYOFF_C,
        (False, False): C.PAYOFF_D,
    }
    other = other_player(player)
    player.payoff = payoff_matrix[(player.cooperate, other.cooperate)]
```

- set_payoffsでは各プレイヤーの利得の計算をおこないます。
```
def set_payoffs(group: Group):
    for p in group.get_players():
        set_payoff(p)
```

### pagesの定義

#### Introductionについて
```
class Introduction(Page):
    timeout_seconds = 100
```

- ```timeout_seconds = ```でそのページの制限時間を設定します。

#### Desicionについて
```
class Decision(Page):
    form_model = 'player'
    form_fields = ['cooperate']
```

- formmodelとform_fieldsを設定します。  
  これでプレイヤーの選択の入力を受け取ります。

#### ResultsWaitPageについて
```
class ResultsWaitPage(WaitPage):
    after_all_players_arrive = set_payoffs # 両プレイヤーが選択後に関数を実行
```

- ```after_all_players_arrive = set_payoffs``` では両プレイヤーが行動を選択したあとにset_payoffs関数を呼び出し利得を計算します。

#### Resultsについて
```
class Results(Page):
    @staticmethod # 誰か使い方を教えて下さい
    def vars_for_template(player: Player):
        opponent = other_player(player)
        return dict(
            opponent=opponent,
            same_choice=player.cooperate == opponent.cooperate,
            my_decision=player.field_display('cooperate'),
            opponent_decision=opponent.field_display('cooperate'),
        )
```

- @staticmethod ：勉強不足のためあまりわかりません。
- vars_for_template: Results.htmlで使用する変数を定義します。

#### ページの表示する順番を設定する
```
page_sequence = [Introduction, Decision, ResultsWaitPage, Results]
```

### HTMLの定義
- HTMLでは表示するページの内容を作成します。
- prisoners_dilemmaの中に
  - Introduction.html
  - instructions.html
  - Decision.html
  - Results.html  

  というhtmlファイルを作成します。



##### Introduction.html

- ```{{ include C.INSTRUCTIONS_TEMPLATE }}```によってinstructions.htmlを呼び出します。

```
{{ block title }}実験説明{{ endblock }}
{{ block content }}

    {{ include C.INSTRUCTIONS_TEMPLATE }}

    {{ next_button }}

{{ endblock }}

```

##### instructions.html

```
<div class="card bg-light m-3">
    <div class="card-body">

    <h3>
        インストラクション
    </h3>

    <p>
      この実験ではあなたは無作為かつ匿名で他の参加者とペアを組むことになります。<br />
      各参加者は同時に「協力する」もしくは「裏切る」のどちらかを選択します。<br />
      あなたの利得は次の利得表に従います。
    </p>

    <p>各セルにおいて、左の数字があなたの利得、右の数字が相手の利得となっています。</p>

    <table class='table table-bordered text-center'
           style='width: auto; margin: auto'>
        <tr>
            <th colspan=2 rowspan=2></th>
            <th colspan=2>あいて</th>
        </tr>
        <tr>
            <th>協力する</th>
            <th>裏切る</th>
        </tr>
        <tr>
            <th rowspan=2><span style="transform: rotate(-90deg);">あなた</span></th>
            <th>協力する</th>
            <td>{{ C.PAYOFF_B }}, {{ C.PAYOFF_B }}</td>
            <td>0, {{ C.PAYOFF_A }}</td>
        </tr>
        <tr>
            <th>裏切る</th>
            <td>{{ C.PAYOFF_A }}, 0</td>
            <td>{{ C.PAYOFF_C }}, {{ C.PAYOFF_C }}</td>
        </tr>
    </table>

    </div>
</div>
```

- ```<div>...</div>```で...に記述されるグループ化します.　また、classによって命名しCSSで見た目を変更することができます。
- ```<h3>...</h3>```はサイズが3番目に大きい見出しタグです。
- ```<p>...</p>```は段落を指定するタグです。
- ```<tale>...</table>```は表を作成するタグです。  
  ```<tr>...</tr>```で行を設定し  
  ```<td>...</td>```で列を設定し  
  ```<th>...</th>```で見出しを設定します。
  - 詳しくは[こちら](http://www.htmq.com/html/table.shtml)を参照


#### Desicion.html

```
{{ block title }}行動の選択{{ endblock }}
{{ block content }}

    <div class="form-group required">
        <table class="table table-bordered text-center" style="width: auto; margin: auto">
            <tr>
                <th colspan="2" rowspan="2"></th>
                <th colspan="2">相手</th>
            </tr>
            <tr>
                <th>協力する</th>
                <th>裏切る</th>
            </tr>
            <tr>
                <th rowspan="2"><span>あなた</span></th>
                <td><button name="cooperate" value="True" class="btn btn-primary btn-large">協力する</button></td>
                <td>{{C.PAYOFF_B}}, {{C.PAYOFF_B}}</td>
                <td>{{ C.PAYOFF_D }}, {{C.PAYOFF_A}}</td>
            </tr>
            <tr>
                <td><button name="cooperate" value="False" class="btn btn-primary btn-large">裏切る</button></td>
                <td>{{C.PAYOFF_A}}, {{ C.PAYOFF_D }}</td>
                <td>{{C.PAYOFF_C}}, {{C.PAYOFF_C}}</td>
            </tr>
        </table>
    </div>

    <p>相手プレイヤーとチャットが出来ます。</p>

    {{ chat }}


    {{ include C.INSTRUCTIONS_TEMPLATE }}

{{ endblock }}
```

- ```rowspan, colspan```ではセルを結合することができます。
- ```<button name="cooperate">...</button>```ではボタンを設定できます。  
  ```name="cooperate"```でPage'sで定義する```form_fields = ['cooperate']```を参照し  
  Player modelで定義した```cooperate = models.BooleanField(...)```に値を格納します。
- ```{{ chat }}```でチャットボックスを追加できます。

#### Results.html
```
{{ block title }}結果{{ endblock }}
{{ block content }}

    <p>
        {{ if same_choice }}
            あなたと相手の選択は {{ my_decision }}　でした。
        {{ else }}
            あなたは {{ my_decision }} を、相手は {{ opponent_decision }}　を選択しました。
        {{ endif }}
    </p>

    <p>
        結果として、 あなたは {{ player.payoff }}　を得ました。
    </p>

    実験は以上となります。<br />
    ご協力ありがとうございました。

    {{ include C.INSTRUCTIONS_TEMPLATE }}

{{ endblock }}
```
- {{ ... }} でPagesのResultsで定義した変数を参照します。


### settingにおけるsession configsの設定
- 作成したアプリを実際に動かすには、settings.pyの中のSESSION_CONFIGSにアプリを登録する必要があります。

```
SESSION_CONFIGS = [
    dict(
        name='prisoners_dilemma',
        display_name="囚人のジレンマ",
        num_demo_participants=2, # ここでデモ用の参加人数を設定します
        app_sequence=['prisoners_dilemma']
    ),
]
```

### 実際に動かしてみよう
- コマンドプロンプトで```otree devserver```と打ち込みます。
- http://localhost:8000/ にアクセスしてください。


## 参考資料
- 2022oTree春合宿資料(URLの記載がOKかわからないのでここでは貼っていません)
