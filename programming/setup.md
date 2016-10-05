開発環境構築
==
開発を行うための標準的な開発環境を準備していきます

    所要時間: 60min(2,3を除く)

## 1. Apple ID
PCの初期設定を行い, Apple IDを取得して下さい

## 2. upgrade to sierra
macOS Sierraにアップグレードする

## 3. [homebrewのセットアップ]( https://blog.ymyzk.com/2015/10/os-x-el-capitan-homebrew/https://blog.ymyzk.com/2015/10/os-x-el-capitan-homebrew/)

<!--
+ `/usr/local`ディレクトリを作成する
```sh
$ sudo mkdir /usr/local && sudo chflags norestricted /usr/local && sudo chown -R $(whoami):admin /usr/local
```
-->

+ `Xcode`のインストール
+ `Xcode`のライセンスに同意する
  + `$ xcode-select --install`
+ `homebrew`のインストール
  + http://brew.sh/

## 4. 必要なパッケージのインストール
```sh
$ brew install curl direnv git imagemagick the_silver_searcher libxml2 libxslt mysql nodebrew openssl peco rbenv readline ruby-build sqlite tig wget
```

### パッケージのインストールを確認
```sh
$ type git
$ git --version
$ type ag
$ type mysql
$ mysql --version
$ type peco
$ type sqlite
$ sqlite3 --version
$ type tig
$ type wget
```

## 5. ruby

### セッティング
```
$ rbenv init
#=> eval "$(rbenv init -)"

$ echo 'eval "$(rbenv init -)"' >> .bash_profile
```

### rubyのインストール
```sh
# インストール可能なバージョンを確認する
$ rbenv install -l

# 最新のrubyをインストール(現時点)
$ MAKE_OPTS=-j4 CONFIGURE_OPTS="--disable-install-rdoc --with-iconv-dir=/usr/lib" rbenv install 2.3.1


# インストールしたrubyをデフォルトで利用するようにする
$ rbenv global 2.3.1

# ruby バージョンを確認
$ ruby -v #=> 2.3.1
```

## 6. node

### セッティング
```sh
$ mkdir ~/.nodebrew

$ nodebrew install latest
$ nodebrew use latest

$ node -v #=> v6.7.0
```

## 7. 開発用アプリケーションの準備

+ [atom](https://atom.io/)
+ [iTerm2](https://www.iterm2.com/index.html)
+ [SourceTree](https://ja.atlassian.com/software/sourcetree)

### atom

#### コマンドラインツールのインストール
+ [Atom] -> [Install Shell Commands]
+ パッケージのインストール
```sh
$ apm install $(cat <<PACKAGE
advanced-open-file
auto-update-packages
file-icons
linter
linter-coffeelint
linter-csslint
linter-erb
linter-ruby
linter-sass-lint
linter-slim
project-manager
script
PACKAGE
)
```

#### atom 環境でrbenvのrubyが使えるようにする
```coffee
# init.coffee
process.env.PATH = "#{process.env.HOME}/.rbenv/shims:#{process.env.HOME}/.rbenv/bin:#{process.env.PATH}"
```

## 8. Mission Controlを無効化する
[システム環境設定] -> [Mission Control] -> [キーボードとマウスのショートカット]

## 9. SSH
gitlab上のリポジトリを操作するためには, SSHによる認証が必要なので, SSHの初期設定をします.

### SSHキーの生成
```sh
$ mkdir ~/.ssh
$ sudo chmod 700 ~/.ssh
$ cd ~/.ssh
$ ssh-keygen -C YOUR_EMAIL_ADDRESS

$ ls
#=> id_rsa, id_rsa.pub
```
### 公開鍵のgitlabへの登録
```sh
$ cat id_rsa.pub | pbcopy
```
<https://GITLAB_HOST/profile/keys>にアクセス
