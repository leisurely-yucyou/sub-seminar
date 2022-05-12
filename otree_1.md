# サブゼミ oTree勉強会　第一回

## 本日の内容
- [PythonとoTreeの導入](#pythonとotreeの導入)
- [ローカルでoTreeを動かしてみる](#ローカルでotreeを動かしてみる)
- テキストエディタの導入
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

- 下の画像の様な画面が表示されるので""





## 参考URL
- [oTree公式サイト](https://otree.readthedocs.io/en/latest/)
- [oTree公式サイト(日本語版)](https://otree.readthedocs.io/ja/latest/index.html)
-
