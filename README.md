# Ruby on Rails チュートリアルのサンプルアプリケーション

これは、次の教材で作られたサンプルアプリケーションです。   
[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
[Michael Hartl](http://www.michaelhartl.com/) 著

## ライセンス

[Ruby on Rails チュートリアル](https://railstutorial.jp/)内にある
ソースコードはMITライセンスとBeerwareライセンスのもとで公開されています。
詳細は [LICENSE.md](LICENSE.md) をご覧ください。

## 使い方

このアプリケーションを動かす場合は、まずはリポジトリを手元にクローンしてください。
その後、次のコマンドで必要になる RubyGems をインストールします。

```
$ bundle install --without production
```

その後、データベースへのマイグレーションを実行します。

```
$ rails db:migrate
```

最後に、テストを実行してうまく動いているかどうか確認してください。

```
$ rails test
```

テストが無事に通ったら、Railsサーバーを立ち上げる準備が整っているはずです。

```
$ rails server
```

詳しくは、[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
を参考にしてください。

## 個人メモ
rails destroy db:rollback ミスった時のコマンド
マイグレーションはその度にヴァージョンが保存される。

<% ... %>と書くと、中に書かれたコードを単に実行するだけで何も出力しません。
<%= ... %>のように等号を追加すると、中のコードの実行結果がテンプレートのその部分に挿入されます。

Railsサーバーのpidを知るには、ps aux | grep server)

## 詰まったところ・知らなかった部分
### 第3章
テストを書いた時にエラーが起きた
原因→rails5.1.4以下かつminitestが5.11.0以上の時に
minitestの仕様変更にrailsが対応していないため。
gem install railsで最新のものにすると直せる。

### 第4章
後続if
   
    puts "x is not empty" if !x.empty? 

モジュールは、関連したメソッドをまとめる方法の１つで、includeメソッドを使ってモジュールを読み込むことができます (ミックスイン (mixed in) とも呼びます)
Railsでは自動的にヘルパーモジュールを読み込んでくれるので、include行をわざわざ書く必要がありません。

！を使って破壊的メソッド（変数の値を変える）
配列に-1で最後の要素を指定できる。
mapメソッドは配列に
 %w[A B C].map { |char| char.downcase }で文字列の配列
省略記法が一般的で、次のように書くこともできます (この記法を“symbol-to-proc”と呼びます)。
%w[A B C].map(&:downcase)

ハッシュのハッシュ
params[:user] = { name: "Michael Hartl", email: "mhartl@example.com" }

オブジェクトの表示　.inspect

メソッドの丸括弧は省略可能,rubyは改行と空白を区別していない

メソッドがクラス自身 (この場合はnew) に対して呼び出されるとき、このメソッドをクラスメソッドと呼びます。クラスのnewメソッドを呼び出した結果は、そのクラスのオブジェクトであり、これはクラスのインスタンスとも呼ばれます。lengthのように、インスタンスに対して呼び出すメソッドはインスタンスメソッドと呼ばれます。
、selfはオブジェクト自身

アクセサー (accessor) をそれぞれ作成します。アクセサーを作成すると、そのデータを取り出すメソッド (getter) と、データに代入するメソッド (setter) をそれぞれ定義
インスタンス変数@nameとインスタンス変数@emailにアクセスするためのメソッドが用意されます。
Railsでは、インスタンス変数をコントローラ内で宣言するだけでビューで使えるようになる、といった点に主な利用価値があります

マスアサインメント (mass assignment) と呼ばれる技法
ハッシュ引数を使ってオブジェクトを初期化する
