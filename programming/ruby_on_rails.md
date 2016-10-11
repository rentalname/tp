Ruby on Rails
==

Railsプロジェクトを新規作成する
--
+ Railsのインストール
  + 今回はこの通りにやらない  


+ ブログアプリケーションを作成する
  + 前準備
  ```sh
  $ gem install bundler
  ```

  + 安全にRails環境を作る
  ```sh
  $ mkdir PROJECT_DIR
  $ cd PROJECT_DIR
  $ bundle init
  $ echo 'gem "rails"' >> Gemfile
  $ bundle install --path vendor/bundle
  $ bundle exec rails new .
  ```


Hello, Rails!
--
+ Webサーバーを起動する
```sh
$ bin/rails server
```

+ Railsに"Hello"と挨拶させる
  + welcome コントローラーを作成
  ```sh
  $ bin/rails generate controller welcome index
  ```
  + 作成されたファイルを確認
  + `app/views/welcome/index.html.erb`を編集


+ アプリケーションのホームページを設定する
  + `root`の設定

アプリケーションの実装と実行
--
+ ルーティングの追加
  + `resources :articles`をroutesファイルに追加

  + ルーティングを確認
  ```
  $ bin/rails routes
  ```

  + 表示されたルーティングについて確認


+ 土台を設置する
  + コントローラーの追加
  ```sh
  $ rails g controller articles
  ```

  + `new`アクションを追加

  + ビューファイルを作成


+ 最初のフォーム
  + フォームを設置
  + ポスト先のルーティングを指定する


+ 記事を作成する
  + `create`アクションを追加

+ Articleモデルを作成する
  + モデルの追加
  ```sh
  $ rails generate model Article title:string text:text
  ```


+ マイグレーションを実行する
  + マイグレーションファイルを確認
  + マイグレーションの実行
  ```sh
  $ bin/rails db:migrate
  ```


+ コントローラでデータを保存する
  + データを保存する処理を追加
  + ストロングパラメーター


+ 記事を表示する
  + `show`アクションを追加
  + ビューファイルを作成


+ すべての記事を一覧表示する
  + `index`アクションを追加
  + ビューファイルを作成


+ リンクの追加


+ 検証 (バリデーション) の追加
  + バリデーションを追加
  + エラーメッセージの表示


+ 記事を更新する
  + `edit`アクションを追加
  + ビューファイルを作成
  + `update`アクションを追加


+ 部分テンプレート(パーシャル)を使用してビューの重複コードをきれいにする
  + 部分テンプレートを作成


+ 記事を削除する
  + `destroy`アクションを追加

2番目のモデルを追加する
--
+ モデルを生成する
+ モデル同士を関連付ける
+ コメントへのルーティングを追加する
+ コントローラを生成する

リファクタリング
--
+ パーシャルコレクションを描画する
+ パーシャルのフォームを描画する

コメントを削除する
--
+ 関連付けられたオブジェクトも削除する

セキュリティ
--
+ ~~BASIC認証~~^今回はやらない
+ その他のセキュリティ対策
  + 時間があるときに読んでおく[Rails セキュリティガイド
](http://railsguides.jp/security.html)

TIPS
--
+ bundle install の高速化
  + 並列インストール
  ```sh
  $ bundle config jobs 4
  ```


+ alias be="bundle exec"


+ bundle exec / bin/rails の省略
  + [direnv](http://direnv.net/)のインストールと設定
  ```sh
    $ brew install direnv
    $ echo 'eval "$(direnv hook bash)"' >> .bash_profile
    $ echo 'PATH=$(pwd)/bin:$PATH' > .envrc
    $ direnv allow
  ```


----

本ドキュメントは[Rails Guides/Railsをはじめよう](http://railsguides.jp/getting_started.html)を改変および編集して作成されました. 本ドキュメントは[クリエイティブ・コモンズ 表示-継承 4.0 国際 (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.ja)ライセンスに基づいて公開されます.
