# サブゼミ oTree勉強会　第四回

## 本日の内容

- [Herokuの登録](Heroku)
- oTree Hubの使い方

### 前回の内容
- 囚人のジレンマゲームの作成

## Heroku

#### アカウントの登録

- [Heroku](https://jp.heroku.com/)にアクセスします。

- 次のような画面が表示されるので新規登録からアカウントの登録を行ないます。

ここに新規登録画面

- 新規登録をクリックすると次の画面が表示されるので必要な情報を入力しましょう。

ここに情報登録画面

- 「登録したメールアドレス宛にメールを送信した」と表示されるのでメールボックスを確認しましょう。

- 届いたメールのリンクをクリックしてパスワードを決定しましょう。

- Herokuのサイトに戻りログイン出来たらOKです。

####  クレジットカードの登録

- クレジットカードの登録も必要なので行ないます。(TA等で何度も実験を行ないましたが請求が来たことはないのでご心配なく)

herokuの適当な画面

-右上のアイコンをクリックし Account settingsにアクセスします。

billingの画面

- Billingの設定を開きクレジットカードの登録を行ないます。

次のように登録したクレジットカードの情報が表示されたらOKです。

#### アプリ登録

- Herokuの[Dashboard](https://dashboard.heroku.com/apps)にアクセスします。

heroku dashboardの画面

- newというボタンをクリックしcreate new appをクリックします。

- app nameは何のアプリかわかる名前を付け、regionはUSのままで大丈夫です。入力できたらcreate appをクリックします。

- Dashboard画面に先ほど入力したアプリ名が表示されていればアプリ登録終了です。

## oTree zipの準備

``` cd D:\otree_sub_semi\subsemi_1 ```

- コマンドプロンプトの現在のディレクトリをotreeの作業ディレクトリにします。  

```otree zip```

- 上のコマンドを実行して「Saved your code info file "ディレクトリ名.otreezip"」と表示されたらOKです。


## oTree Hub

#### アカウントの登録

- [oTree Hub](https://www.otreehub.com/)にアクセスします。次のような画面が表示されるのでRegisterから登録を行ないます。(登録手順は簡単なので割愛します)

- 登録出来たらログインします。

#### Herokuとの連携

- Heroku server deploymentをクリックするとHerokuとの連携を要求されるので連携させます。

- 連携させると次のような画面が表示されます。

otree hub のheroku projectsの画面

- Other Sitesに先ほどHerokuで登録したアプリが表示されているはずなのでRegisterをクリックしてActive Sitesに追加します。

- 先ほどのアプリがActive Sitesに追加出来たらDeployをクリックします。

- Upload code to Herokuから先ほど作ったotreezipファイルをアップロードします。

- Build resultに"Your build succeeded."が表示されていればアップロード完了です。

- 次にReset DBをクリックし、"Resetdb succeeded."と表示されたらOKです。

- "https://アプリ名.herokuapp.com/"が背景が水色部分の4番にあるのでクリックします。

- するとよく見る画面が表示されます。

#### オンライン実験をするためには
- 修論等でオンライン実験を行なうには他にも設定することがあります。

- 被験者のログインIDやデバッグのオフなどについてはQ.3以降のサブゼミでやろうと思います。
