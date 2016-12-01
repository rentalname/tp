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

#### superuser をつくる
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
$ createdb <db_name> -O <user_name>
```
`-O`オプションを指定することで, dbの所有者を変更できる.  
dbの所有者はdb操作のための全ての権限を持っているため, あらかじめdbを操作するユーザー名が分かっているのであれば所有権を指定しておいた方が楽だと思う

### 追加されたDBを確認する
```sh
$ psql -l
```

権限
--
### データベースの権限を変更する
ユーザーの権限をデータベース毎に指定する
```sh
$ psql -U <superuser> <db_name>

=> GRANT ALL ON DATABASE <db_name> TO <user_name>
```
### ロールの権限
ロールの権限を変更する
```sh
$ psql -U <superuser> <db_name>

#  ALTER ROLE name [ [ WITH ] option [ ... ] ]
=> ALTER ROLE <user_name> WITH SUPERUSER
```

#### 設定可能なロール権限
+ SUPERUSER  | NOSUPERUSER
+ CREATEDB   | NOCREATEDB
+ CREATEROLE | NOCREATEROLE
+ CREATEUSER | NOCREATEUSER

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
+ [PostgreSQLの管理系コマンドまとめ](http://qiita.com/gigamori/items/7522929e0d4b1fb4e5bf)

