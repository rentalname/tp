
Mysql環境構築
==

### 前提
+ homebrewの設定が完了していること

インストール
--
### homebrewを使う場合
以下のコマンドで最新バージョンのMysqlがインストールされる
```sh
$ brew install mysql
```

初期設定
--

### DB サービスの起動
```sh
$ brew services start mysql
```

### 作成されたDBを確認する
ユーザー
--
### ユーザーの追加
```sh
$ mysql -u root
mysql> create user <USER_NAME> identified by '<PASSWORD>';
```

### 追加されたユーザーを確認する
```sh
$ mysql -u root
mysql> select User,Host from mysql.user;
```

### 追加したユーザーでDBに接続する
```sh
$ mysql -u <USER_NAME> -p
> <PASSWORD>
```

DB
--
### DBの作成
```sh
$ mysql -u root
mysql> create database <DB_NAME>;
```


### 追加されたDBを確認する
```sh
$ mysql -u root
mysql> show database;
```

権限
--
### 権限を確認する
```sh
mysql> show grants;
```

### ユーザーのデータベースへの操作・アクセス権を変更する
#### ユーザーの権限を指定する
```sh
$ mysql -u root
mysql> grants <AUTHORITY> on *.* to <USER_NAME>
```

#### ユーザーの権限をデータベース毎に指定する
```sh
$ mysql -u root
mysql> grants <AUTHORITY> on <DB_NAME>.* to <USER_NAME>
```

### [権限の種類](http://www.dbonline.jp/mysql/user/index5.html)
|権限|説明|
|----|----|
|ALL |GRANT OPTION 以外の全ての権限|
|GRANT OPTION|権限を与えることができる|
|USAGE|全ての権限を剥奪する|
|SELECT|SELECT を使用できる|
|UPDATE|UPDATE を使用できる|

TIPS
--
### mysql サーバーを再起動する
サーバーを起動したいときと再起動したいときの両方に対応できるのでこちらの方が便利
```sh
$ brew services restart mysql
```

### pg commander
mysqlをGUI操作することができるツール
```sh
$ brew cask install sequel-pro
```

### [最新以外のmysqlをインストールする](http://qiita.com/LowSE01/items/c518f61a8998ba6e4ea8)
brew versionsを利用して, 古いバージョンのmysqlをインストールできる
```sh
$ brew tap homebrew/versions

$ brew install mysql@5.6 #=> mysqlの5.6系がインストールされる
$ brew link --force mysql@5.6

# バージョンが切り替わったことを確認する
$ exec -l $SHELL
$ mysql --version
```

