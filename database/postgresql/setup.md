Postgresql環境構築
==

インストール
--
### homebrewを使う場合
```sh
$ brew install postgresql
```

初期設定
--
### PGDATA
環境変数にPGDATAを追加する
```sh
$ echo "PGDATA=/usr/local/var/postgres" >> ~/.bash_profile
# or
$ echo "PGDATA=/usr/local/var/postgres" >> ~/.zshenv
```

### initdb
`initdb`コマンドでdatabase環境を初期化する
```sh
$ rm -rf $PGDATA
$ initdb
```
superuserが自分のユーザー名で作成される

### DB サービスの起動
```sh
$ brew services start postgresql
```

### 作成されたDBを確認する
```sh
$ psql -l
```
ユーザー
--
### ユーザーの追加
```sh
$ createuser <user_name>
```

### 追加されたユーザーを確認する
```sh
$ psql postgres

=> select * from pg_user
```
DB
--
### DBの作成
```sh
$ createdb <db_name>
```

### 追加されたDBを確認する
```sh
$ psql -l
```

TIPS
--
### postgresql サーバーを再起動する
サーバーを起動したいときと再起動したいときの両方に対応できるのでこちらの方が便利
```sh
$ brew services restart postgresql
```

### pg commander
postgresqlを操作することができるGUIのツール
```sh
$ brew cask install pg-commander
```

参考
--
+ [MacのRailsアプリでPostgreSQLを使う方法](http://qiita.com/yh2020/items/8be3087004d100fe752b)
