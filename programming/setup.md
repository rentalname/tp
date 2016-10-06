開発環境構築
==
開発を行うための標準的な開発環境を準備します

    所要時間: 60min(2,3を除く)

準備
--
+ Apple IDの取得
+ OSを最新にする
+ Xcodeのインストール

[homebrew](http://brew.sh/)
--
+ `Xcode`のライセンスに同意する
  + `$ xcode-select --install`
+ `homebrew`のインストール
  + http://brew.sh/
  + homebrewのインストール方法は変更になることがあるので, 公式サイトの案内を参考にする

開発によく使うパッケージのインストール
--
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
$ type sqlite3
$ sqlite3 --version
$ type tig
$ type wget
```

### ライブラリのリンク
```sh
$ brew link --force libxml2 libxslt
```

ruby
--

### rbenv
`rbenv`を利用することで, rubyのバージョンを指定して, rubyを実行することができる.
プロジェクトによって, 利用するrubyバージョンに差異があるので, `rbenv`が利用できることは重要.

```sh
$ rbenv init
#=> eval "$(rbenv init -)"

$ echo 'eval "$(rbenv init -)"' >> .bash_profile

# 一旦shellを再起動する
exec -l $SHELL
```

### rubyのインストール
```sh
# インストール可能なバージョンを確認する
$ rbenv install -l

# 最新のrubyをインストール(現時点)

$ MAKE_OPTS=-j4 CONFIGURE_OPTS="--disable-install-rdoc --with-readline-dir=$(brew --prefix readline) --with-iconv-dir=/usr/lib" rbenv install 2.3.1


# インストールしたrubyをデフォルトで利用するようにする
$ rbenv global 2.3.1

# ruby バージョンを確認
$ ruby -v #=> 2.3.1
```

### gemのインストール時にドキュメントをインストールしないようにする
```sh
echo "gem: --no-document" > ~/.gemrc
```

node
--
railsが依存するライブラリの中に, javascriptの実行環境を要求するものがあるので, nodeをjavascriptの実行環境として利用できるようにする

### nodebrew
`nodebrew`を利用することで, 最新のnodeを簡単に導入することができる
```sh
$ mkdir -p ~/.nodebrew/src

$ nodebrew install latest
$ nodebrew use latest

$ node -v #=> v6.7.0
```

開発用アプリケーション
--
個人の嗜好によって, 好きなアプリケーションを使用することができる.
説明のしやすさの都合で以下のアプリケーションをオススメします.

+ [atom](https://atom.io/)
+ [iTerm2](https://www.iterm2.com/index.html)
+ [SourceTree](https://ja.atlassian.com/software/sourcetree)

### [atom](https://atom.io/)
コードエディタです

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
+ [Atom] -> [Init Script]
```coffee
# init.coffee
process.env.PATH = "#{process.env.HOME}/.rbenv/shims:#{process.env.HOME}/.rbenv/bin:#{process.env.PATH}"
```

### [iTerm2](https://www.iterm2.com/index.html)
ターミナルソフト. macに標準で備わっている[端末]と同等の機能を持っている.

### [SourceTree](https://ja.atlassian.com/software/sourcetree)
GUIで操作可能なgitクライアント

## 8. Mission Controlを無効化する
+ 貴重なキーボードショートカットを占有しているので, 無効にします.
+ [システム環境設定] -> [Mission Control] -> [キーボードとマウスのショートカット]

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
