HerokuへのRailsアプリケーションのデプロイ
==

Herokuアカウントの取得
--
+ <https://www.heroku.com/>にアクセスし, sign upする
+ 登録に使用したメールアドレスとパスワードを使ってサービスにログインできることを確認する

Heroku CLI
--
### 導入
+ `$ brew install heroku`

### 認証
+ `$ heroku`
  + `Unauthorized`の出力
+ `$ heroku login`
  + Herokuアカウントの取得に利用したメールアドレスとパスワードを入力する

アプリケーションの作成
--
```sh
$ mkdir APP_DIR

$ cd APP_DIR

$ bundle init

$ echo "gem 'rails'" >> Gemfile

$ bundle install --path vendor/bundle

$ bundle exec rails new .
```

git
--
### gibo
後述する`.gitignore`ファイルを作成するために`gibo`と呼ばれるパッケージをインストールする

```sh
$ brew install gibo

$ gibo -u
```

### gitリポジトリの作成

```sh
$ cd APP_DIR

$ git init

$ gibo rails macos > .gitignore

$ git status

$ git add

$ git status

$ git commit -m "init"
```

アプリケーションをherokuに作成する
--

```sh
$ cd APP_DIR

$ heroku create

$ git remote -v
```

Heroku Postgres アドオンの有効化
--
+ <https://dashboard.heroku.com/apps/YOUR_APP>にアクセスする
+ `configure Add-ons`を開く
+ `Add-ons`の検索フォームに`Heroku Postgres`を入力し表示されたアドオンをクリックする
+ `Plan name`に`Hobby Dev`を選択し, `Provision`をクリックする
+ アプリケーションダッシュボードをサイド開き`Installed add-ons`に`Heroku Postgres`が表示されたことを確認する

RailsアプリケーションのデータベースをPostgresqlに変更する
--
以下のようにファイルを編集する

```patch
diff --git a/Gemfile b/Gemfile
index b5fbf94..b86ceba 100644
--- a/Gemfile
+++ b/Gemfile
@@ -9,7 +9,7 @@ end
 # Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
 gem 'rails', '~> 5.0.2'
 # Use sqlite3 as the database for Active Record
-gem 'sqlite3'
+gem 'pg'
 # Use Puma as the app server
 gem 'puma', '~> 3.0'
 # Use SCSS for stylesheets
diff --git a/config/database.yml b/config/database.yml
index 1c1a37c..22a7757 100644
--- a/config/database.yml
+++ b/config/database.yml
@@ -5,21 +5,21 @@
 #   gem 'sqlite3'
 #
 default: &default
-  adapter: sqlite3
+  adapter: postgresql
   pool: 5
   timeout: 5000

 development:
   <<: *default
-  database: db/development.sqlite3
+  database: herokudb_dev

 # Warning: The database defined as "test" will be erased and
 # re-generated from your development database when you run "rake".
 # Do not set this db to the same as development or production.
 test:
   <<: *default
-  database: db/test.sqlite3
+  database: herokudb_test

 production:
   <<: *default
-  database: db/production.sqlite3
+  database: ENV['DATABASE_URL']
```

編集が完了したら`bundle install`を再実行する

参考資料
--
http://morizyun.github.io/blog/beginner-rails-heroku-tutorial/
