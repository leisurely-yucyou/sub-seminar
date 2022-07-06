# サブゼミ oTree勉強会　第三回

## 本日の内容

- [アンケートの作成](#アンケートの作成)

### 前回の内容
- テキストエディタの導入
- HTMLを触ってみる

## アンケートの作成

#### アプリの作成
```cd D:\otree_sub_semi\subsemi_1```
- コマンドプロンプトの現在のディレクトリをotreeの作業ディレクトリにします。  

```otree startapp questionnaire```
- questionnaireというアプリフォルダを作成します。  
___
アプリフォルダの中身の説明
- \_\_pycache\_\_：キャッシュファイルの保管場所。基本的に触りません。
- \_\_init\_\_.py：アプリの内容・機能をここで作っていきます。
- MyPage.html, Results.html：アプリのページ画面として表示されるhmtlファイルです。
___

### 今回のアプリ作成の手順
1. \_\_init__.py 内のmodels
2. HTMLファイル
3. \_\_init__.py 内のpages
4. アプリの登録

### modelsについて
- modelsではアプリの動作を作っていきます。
- modelsにはConstantsクラス, Subsessionクラス, Groupクラス, Playerクラスの4つのクラスがあります。  

  - Constants(C)クラス：アプリ全体に関する設定
  - Subsessionクラス：ゲーム全体に関する設定
  - Groupクラス：複数プレイヤーで実施する実験などにおけるグループ全体に関する設定
  - Playerクラス：各プレイヤーに関する設定

#### Constantsクラスの定義
- questionnaireフォルダ内の\_\_init__.pyを開きます。

```
class C(BaseConstants):
    NAME_IN_URL = 'questionnaire'
    PLAYERS_PER_GROUP = None #グループによる実験ではないので"None"とします。
    NUM_ROUNDS = 1 #アンケートは1度だけ行ないます。
```


#### Playerクラスの定義
- Playerクラスの中で各プレイヤーに関する変数を定義します。
- ここで定義した変数をデータとして取得することができます。

```
class Player(BasePlayer):
    q_gender = models.CharField(initial=None,
                                choices=['男性', '女性', 'その他'],
                                verbose_name='あなたの性別を教えてください。',
                                widget=widgets.RadioSelect())
                                # ラジオボタンを使うときには"widget"で設定できます。
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください。',
                                        choices=range(0, 125),
                                        initial=None)
                                        # 数字の場合は"choices"を使うことで、範囲を指定できます。
                                        # range()では0<=選択範囲<125になるので、表示される最小値は0、最大値は124になります。
    q_prefecture = models.CharField(initial=None,
                                choices=['北海道', '青森県', '岩手県', '宮城県', '秋田県', '山形県', '福島県','茨城県', '栃木県', '群馬県', '埼玉県', '千葉県', '東京都', '神奈川県','新潟県', '富山県', '石川県', '福井県', '山梨県', '長野県', '岐阜県', '静岡県', '愛知県', '三重県','滋賀県', '京都府', '大阪府', '兵庫県', '奈良県', '和歌山県','鳥取県', '島根県', '岡山県', '広島県', '山口県','徳島県', '香川県', '愛媛県', '高知県','福岡県', '佐賀県', '長崎県', '熊本県', '大分県', '宮崎県', '鹿児島県', '沖縄県'],
                                verbose_name='あなたのおすまいの地域を教えてください。')

    q_tanmatsu = models.CharField(initial=None,
                                choices=['パソコン',
                                        'タブレット',
                                        'スマートフォン',
                                        'それ以外'
                                        ],
                                verbose_name='この回答は、どの電子機器で回答していますか？',
                                widget=widgets.RadioSelect()
                                )
    q_allais_A = models.CharField(initial=None,
                                choices=['くじ１：確実に10万円', 'くじ２：確率0.01で0円、確率0.1で50万円、確率0.89で10万円を得る'
                                        ],
                                verbose_name='どちらかのくじを選択してください。',
                                widget=widgets.RadioSelect()
                                )

    q_allais_B = models.CharField(initial=None,
                                choices=['くじ3：確率0.11で10万円、確率0.89で0円', 'くじ4：確率0.1で50万円、確率0.9で0円'
                                ],
                                verbose_name='どちらかのくじを選択してください。',
                                widget=widgets.RadioSelect()
                                )


```

___
Fieldについて：
- BoolenField：0か1の値
- CurrencyField：金額やポイント
- CharField：文字列
- IntegerField：整数値
- PositiveIntegerField：正の整数値
- FloatField：実数値
- StringField：文字列
- LongStringField：長い文字列

取得したいデータや実験システムに応じて使い分けます。
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

### HTMLの定義
- HTMLでは表示するページの内容を作成します。
- questionnaireの中にPage1.htmlとPage2.htmlというhtmlファイルを作成します。

##### ページ1

```
{{ block title }}
    アンケート１
{{ endblock }}

{{ block content }}

<div>
  <p>
    以下の質問について、最もあてはまる(最も近い)ものを選んでください。
  </p>
</div>

    {{ formfields }}
    {{ next_button }}

{{ endblock }}
```

##### 各行の説明

```
{{ block title }}
    アンケート
{{ endblock }}
```

- ウェブページにおけるタイトルを設定します。

```
{{ block content }}
...
{{ endblock }}
```

- この中にウェブページに表示する内容を記述します。

```
{{ formfields }}
```

- これによってPlayerクラスで定義した質問項目を表示できます。

```
{{ next_button }}
```

- 「次へ」のボタンです。このボタンをクリックすることで次の画面へ進みます。

##### ページ2

```
{{ block title }}
    アンケート2
{{ endblock }}

{{ block content }}

<div>
  <p>
    以下のくじについて好きな方を選択してください。
  </p>
</div>

    {{ formfields }}
    {{ next_button }}

{{ endblock }}
```

#### リザルトページ

```
{{ block title }}
    アンケート回答終了
{{ endblock }}

{{ block content }}
<div>
  <p>
    ご協力ありがとうございました。
  </p>
</div>

{{ endblock }}
```

### pagesの定義
- pagesでは「ページの表示する順番」や「入力項目」、「関数の計算の順番」などを設定します。

#### Page1について
- Page1ではアンケートへの回答の入力があります。
- 次のように入力画面を作成します。

```
class Page1(Page):
    form_model = 'player'
    form_fields = [
    'q_gender',
    'q_age',
    'q_prefecture',
    'q_tanmatsu'
    ]
```

#### Page2について
- Page2ではアンケートへの回答の入力があります。
- 次のように入力画面を作成します。

```
class Page2(Page):
    form_model = 'player'
    form_fields = [
    'q_allais_A',
    'q_allais_B'
    ]
```

#### Resultsについて
- 今回は特に記述することはありません。

#### ページの表示する順番を設定する
- page_sequenceによって画面の表示する順番を設定できます。

```
page_sequence = [Page1, Page2, Results]
```

### settingにおけるsession configsの設定
- 作成したアプリを実際に動かすには、settings.pyの中のSESSION_CONFIGSにアプリを登録する必要があります。

```
SESSION_CONFIGS = [
    dict(
        name='questionnaire',
        display_name="アンケート",
        num_demo_participants=1, # ここでデモ用の参加人数を設定します
        app_sequence=['questionnaire']
    ),
]
```

### 実際に動かしてみよう
- コマンドプロンプトで```otree devserver```と打ち込みます。
- http://localhost:8000/ にアクセスしてください。


## 参考資料
- 2022oTree春合宿資料(URLの記載がOKかわからないのでここでは貼っていません)
