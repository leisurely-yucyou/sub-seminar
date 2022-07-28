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

![image](https://user-images.githubusercontent.com/48300561/181419713-01409007-db32-41b1-a852-990806f687d1.png)


- 新規登録をクリックすると次の画面が表示されるので必要な情報を入力しましょう。

![image](https://user-images.githubusercontent.com/48300561/181419840-7a0dccdb-248d-4b19-a2d4-7d2e42152ab4.png)

- 「登録したメールアドレス宛にメールを送信した」と表示されるのでメールボックスを確認しましょう。

- 届いたメールのリンクをクリックしてパスワードを決定しましょう。

- Herokuのサイトに戻りログイン出来たらOKです。

####  クレジットカードの登録

- クレジットカードの登録も必要なので行ないます。(TA等で何度も実験を行ないましたが請求が来たことはないのでご心配なく)

![image](https://user-images.githubusercontent.com/48300561/181420695-7f2f5c0f-44ae-40ee-b39e-06dca5629e32.png)

-右上のアイコンをクリックし Account settingsにアクセスします。

![スクリーンショット 2022-07-28 133050](https://user-images.githubusercontent.com/48300561/181420868-49256fbf-4bb2-47c3-ab87-0f7655e5a75a.png)


- Billingの設定を開きクレジットカードの登録を行ないます。

- 先ほどの画面のように登録したクレジットカードの情報が表示されたらOKです。

#### アプリ登録

- Herokuの[Dashboard](https://dashboard.heroku.com/apps)にアクセスします。

![image](https://user-images.githubusercontent.com/48300561/181420984-63b2edcc-f9d0-4a7a-8543-9f5288f9d352.png)

- newというボタンをクリックしcreate new appをクリックします。

![image](https://user-images.githubusercontent.com/48300561/181421029-b5f87cd8-26ce-4c43-a662-715d6bdf8d47.png)


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

![image](https://user-images.githubusercontent.com/48300561/181421096-f80424fa-d8c0-4981-96de-a9dd2d645e99.png)

- 登録出来たらログインします。

#### Herokuとの連携

- Heroku server deploymentをクリックするとHerokuとの連携を要求されるので連携させます。

- 連携させると次のような画面が表示されます。

![image](https://user-images.githubusercontent.com/48300561/181421162-66fa1549-23c9-457b-9c8d-e730c2eac094.png)

- Other Sitesに先ほどHerokuで登録したアプリが表示されているはずなのでRegisterをクリックしてActive Sitesに追加します。

- 先ほどのアプリがActive Sitesに追加出来たらDeployをクリックします。

![image](https://user-images.githubusercontent.com/48300561/181421219-0fae70a9-96a2-4a1c-af5b-51963ed441b3.png)

- Upload code to Herokuから先ほど作ったotreezipファイルをアップロードします。

- Build resultに"Your build succeeded."が表示されていればアップロード完了です。

- 次にReset DBをクリックし、"Resetdb succeeded."と表示されたらOKです。

- "https://アプリ名.herokuapp.com/"が背景が水色部分の4番にあるのでクリックします。

- するとよく見る画面が表示されます。

![image](https://user-images.githubusercontent.com/48300561/181421278-b4af77dd-65f3-4909-a213-cade5604ab6a.png)

#### オンライン実験をするためには
- 修論等でオンライン実験を行なうには他にも設定することがあります。

- 被験者のログインIDやデバッグのオフなどについてはQ.3以降のサブゼミでやろうと思います。
