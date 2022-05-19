# サブゼミ oTree勉強会　第二回

## 本日の内容

- [テキストエディタの導入](#テキストエディタの導入)
- [HTMLを触ってみる](#HTMLを触ってみる)

### 前回の内容
- [PythonとoTreeの導入](#pythonとotreeの導入)
- [ローカルでoTreeを動かしてみる](#ローカルでotreeを動かしてみる)


## テキストエディタの導入

- テキストエディタはプログラムを書いていくうえで欠かせないツールです。
- 様々なソフトがあるので自分に合ったエディタを使うことをおすすめします。

- Visual Studio Codeのインストール方法を紹介します。

#### Visual Studio Codeのインストール
- https://code.visualstudio.com/ からインストーラーをダウンロードしてインストールしましょう。
- サイトにアクセスすると次のような画面になります。"Download for Windows"と書いてある青いボタンをクリックしてインストーラーをダウンロードします。

![image](https://user-images.githubusercontent.com/48300561/169306755-388bc303-4e95-4da6-9453-6c19f455d08e.png)

- ダウンロード出来たらインストーラーを起動して、表示される指示に従ってインストールを進めましょう。


- わかりやすい説明は[ここ](https://qiita.com/MtBigYashi/items/a840865a6908de044724)

- VScodeをより快適にするためには
  - [公式マニュアル](https://code.visualstudio.com/docs)
  - [日本語化](https://www.python.jp/python_vscode/windows/setup/install_vscode.html#%E3%83%A1%E3%83%8B%E3%83%A5%E3%83%BC%E3%81%AA%E3%81%A9%E3%81%AE%E6%97%A5%E6%9C%AC%E8%AA%9E%E5%8C%96)
  - [Python用の環境](https://www.python.jp/python_vscode/windows/setup/install_vscode.html#Python%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)

## HTMLを触ってみる

- VScodeを起動して画面左上にある"ファイル"から"フォルダを開く"を選択し、前回の勉強会で作成したoTreeのフォルダを開きます。
- 画面上部にある"Terminal"から"New Terminal"をクリックすると画面下部にターミナルが開かれます。

![image](https://user-images.githubusercontent.com/48300561/169308164-474d7369-3c8d-46b5-86c9-d954911ffbe0.png)


- ターミナルに"otree devserver"と打ち込み、ローカルでoTreeを起動します。  
※エラーが出る場合コマンドプロンプトなどでoTreeを起動しても大丈夫です。

- http://localhost:8000/ にアクセスします。

- Guess 2/3 of the Averageを開きます

#### Introducion.html

- 下の画の画面左部分はブラウザでイントロダクションのページを開いたもので、右部分はVScodeでHTMLファイルを開いたものです。

![image](https://user-images.githubusercontent.com/48300561/169311145-bdb59769-4670-47a0-8131-ba9004ec7d6d.png)

- ブラウザ上で表示されている内容がHTMLファイルには書いていないことが分かります。

- VScode上に"{{ }}"で囲まれている部分はotree用のコマンドです。

- VScodeの4行目に"{{ include C.INSTRUCTIONS_TEMPLATE }}"と書いているので、"__init__.py"を開いてclass Cの"INSTRUCTIONS_TEMPLATE"を確認します。

![image](https://user-images.githubusercontent.com/48300561/169313437-06011a8b-13c9-4930-a463-dc5a5767d338.png)

- ```INSTRUCTIONS_TEMPLATE = 'guess_two_thirds/instructions.html'```と書いてあるのでinstructions.htmlを呼び出していることが分かりました。
- それではinstructions.htmlをVScodeで開いてみましょう。

#### instructions.html

![image](https://user-images.githubusercontent.com/48300561/169313792-29d6507f-c223-4f80-8a93-c1d551e18943.png)
- ブラウザ上で表示される文章と同じものがあることが分かります。それではHTMLファイルに変更を加えていきます。

- 先ほど"{{}}"で囲まれた部分はoTreeのコマンドと説明しましたが"<>"や"</>"で囲まれているのはHTMLのコマンドです。
- 6行目の"Instructions"を"インストラクション"と日本語に修正します。修正出来たら"ctrl+S"を押して変更を保存します。
- ブラウザを更新すると下の画面のように変更が反映されます。

![image](https://user-images.githubusercontent.com/48300561/169314658-d914dd1f-72dd-4b39-9ae9-af3c89b744ed.png)

- 上と同様に他の部分も日本語に書き換えてみましょう。(下に日本語訳を書いているのでコピペでOKです。)

  - 10~15行目  
  あなたは{{ C.PLAYERS_PER_GROUP }}人一組のグループに分けられました。  
  各人は0から{{ C.GUESS_MAX }}の間の数字を一つ選択します。  
  全員が選んだ数字の平均に2/3をかけた数字に最も近い数字を選択した人が勝ちです。

  - 19~21行目  
  勝った人は{{ C.JACKPOT }}を得る事が出来ます。  
  もし勝った人が複数人いた場合は{{ C.JACKPOT }}を勝った人で等分します。

  - 24行目  
  このゲームは{{ C.NUM_ROUNDS }}回繰り返し行ないます。

- このページの変更は以上です。

#### Guess.html

- まずHTMLファイルの内容について説明します。

-

## 参考URL
- [oTree公式サイト](https://otree.readthedocs.io/en/latest/)
- [oTree公式サイト(日本語版)](https://otree.readthedocs.io/ja/latest/index.html)


### VScode以外のテキストエディタの紹介
- テキストエディタは先述したように様々なソフトがあります。
- 僕がよく使っているAtomというエディタのインストール方法を記載しておきます。

#### Atomのインストール
- https://atom.io/ からインストーラーをダウンロードしてインストールしましょう。
- 分かりやすい説明は[ここ](https://qiita.com/yasushi-jp/items/bb92b4fa846f3b3e2733)

- Atomをより快適にするには
  - [公式マニュアル](https://flight-manual.atom.io/)
  - [日本語化](https://qiita.com/biz-nakashima001/items/1419cc86e3b62fa2eb53#:~:text=%E3%80%8COpen%20Installer%E3%80%8D%E3%82%92%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%80%82,%E3%81%A6%E3%81%84%E3%82%8B%E3%81%93%E3%81%A8%E3%82%92%E7%A2%BA%E8%AA%8D%E3%80%82)
  - [Python用の環境](https://qiita.com/suecharo/items/dbc525dd5f39bdb8403c)
