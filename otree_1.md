# サブゼミ oTree勉強会　第一回

## 本日の内容
- [PythonとoTreeの導入](#pythonとotreeの導入)
- [ローカルでoTreeを動かしてみる](#ローカルでotreeを動かしてみる)
- [テキストエディタの導入](#テキストエディタの導入)
- HTMLを触ってみる

#### 注意事項
- MacOSはカバーできないかも
- 今日の内容はoTree春合宿の内容と重複します
- oTree Lite(バージョン5)を取り扱います

## PythonとoTreeの導入

- https://otree.readthedocs.io/ja/latest/install-windows.html  
を参考にPythonとoTreeを導入します。

- 注意事項
  - ```pip3 install -U otree```でエラーが出る場合は```pip install -U otree```にするといいかも
  - Pythonを入れたらコマンドプロンプトで```python```と打ち込んでバージョンが表示されたらOK!

#### oTree用の作業ディレクトリの作成
- 下の画像のようにoTree用の作業ディレクトリ(フォルダ)を作成します。  
私はCドライブを圧迫したくないのでDドライブにフォルダを作成しています。

![image](https://user-images.githubusercontent.com/48300561/167908122-a4b63b3d-df9c-4127-acd9-67b7c0b98c1f.png)

#### プロジェクトフォルダの作成
- コマンドプロンプトを起動して現在のディレクトリを先ほど作った作業ディレクトリにします。  
```cd/d D:\otreeLite```

- 私の場合はディレクトリのPATHが"D:\otreeLite"ですが、PATHは人によって異なるので各自PATHを打ち込んでください

- 現在のディレクトリの指定が出来たら"subsemi_1"という名前のプロジェクトフォルダを作成します。  

```otree startproject subsemi_1```

ここではプロジェクトがサブゼミで使うものだと分かりやすくするため"subsemi_1"と名付けました。自分で実験プログラムを開発する時は好きな名前(何の実験プログラムかわかりやすい名前)を付けましょう。

- Include sample games?(y or n) → y
  - このあとサンプルゲームを触るので"y"と打ち込みます。

## ローカルでoTreeを動かしてみる
- コマンドプロンプトを起動します。  
  - コマンドプロンプトの起動方法が分からない人へ  
  Windowsキー+Rを押して"cmd"と打ち込むことで起動できます。  

![image](https://user-images.githubusercontent.com/48300561/167978248-1a4923e9-ff07-4ec7-9792-eaf4eac20ffd.png)

- コマンドプロンプト上で```cd subsemi_1```と打ち込みます。

- コマンドプロンプト上で```otree devserver```と打ち込みます。
- "Open your browser to http://localhost:8000/ "と表示されるので、http://localhost:8000/ にアクセスします。
  - "Open your browser ~"が表示されない人は言ってください。

- 下の画像の様な画面が表示されるので"Guess 2/3 of the Average"をクリックします。  

![image](https://user-images.githubusercontent.com/48300561/167981055-7e1d6155-373b-4147-a9d2-5d977b8138ec.png)

- すると、次の画像の様な画面が表示されるので"Play in split screen mode."をクリックして実際にゲームをプレイしてみましょう。

![image](https://user-images.githubusercontent.com/48300561/167981337-2c226af0-5327-4e38-a827-d9af00677edb.png)

## テキストエディタの導入

- テキストエディタはプログラムを書いていくうえで欠かせないツールです。
- 様々なソフトがあるので自分に合ったエディタを使うことをおすすめします。

- Visual Studio CodeとAtomのインストール方法を紹介します。(インストールするのはどちらか一方で大丈夫です。)

#### Visual Studio Codeのインストール
- https://code.visualstudio.com/ からインストーラーをダウンロードしてインストールしましょう。
- わかりやすい説明は[ここ](https://qiita.com/MtBigYashi/items/a840865a6908de044724)

- VScodeをより快適にするためには
  - [公式マニュアル](https://code.visualstudio.com/docs)
  - [日本語化](https://www.python.jp/python_vscode/windows/setup/install_vscode.html#%E3%83%A1%E3%83%8B%E3%83%A5%E3%83%BC%E3%81%AA%E3%81%A9%E3%81%AE%E6%97%A5%E6%9C%AC%E8%AA%9E%E5%8C%96)
  - [Python用の環境](https://www.python.jp/python_vscode/windows/setup/install_vscode.html#Python%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)

#### Atomのインストール
- https://atom.io/ からインストーラーをダウンロードしてインストールしましょう。
- 分かりやすい説明は[ここ](https://qiita.com/yasushi-jp/items/bb92b4fa846f3b3e2733)

- Atomをより快適にするには
  - [公式マニュアル](https://flight-manual.atom.io/)
  - [日本語化](https://qiita.com/biz-nakashima001/items/1419cc86e3b62fa2eb53#:~:text=%E3%80%8COpen%20Installer%E3%80%8D%E3%82%92%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF%E3%80%82,%E3%81%A6%E3%81%84%E3%82%8B%E3%81%93%E3%81%A8%E3%82%92%E7%A2%BA%E8%AA%8D%E3%80%82)
  - [Python用の環境](https://qiita.com/suecharo/items/dbc525dd5f39bdb8403c)

## HTMLを触ってみる





## 参考URL
- [oTree公式サイト](https://otree.readthedocs.io/en/latest/)
- [oTree公式サイト(日本語版)](https://otree.readthedocs.io/ja/latest/index.html)
-
