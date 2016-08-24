git/github
==

環境の確認
--
```sh
# gitコマンドが使用できることを確認する
$ type git

# gitのバージョンを確認. 古すぎる場合は最新のものに更新する
$ git --version

# gitのアップグレード
$ brew update && brew upgrade git
```

サポートツールの導入
--
```sh
# gitignoreファイルの初期設定をするためにgiboを導入する
$ brew install gibo
```

アカウントの取得
--
[github](https://github.com/)


環境構築
--

### gitリポジトリの初期設定
```sh
$ cd PROJECT_DIR
$ git init
$ gibo Ruby Rails OSX > .gitignore

# masterブランチを作成する
$ git add -A
$ git commit -m 'init'
```

### sshの設定
```sh
$ cd
$ mkdir .ssh
$ chmod 700 .ssh

$ cd .ssh
$ ssh-keygen -f github_rsa -C MAIL_ADDRESS
$ atom config
# 次の内容をcconfigファイルに追記する
:<<CONFIG_FILE
Host github
  HostName github.com
  User git
  Port 22
  IdentitiesOnly yes
  IdentityFile ~/.ssh/github_rsa
CONFIG_FILE
```

### githubに公開鍵を登録する
```sh
$ cd ~/.ssh
# 公開鍵をクリップボードにコピーする
$ cat github_rsa.pub | pbcopy
```

[setting画面を開く](https://github.com/settings/keys)
![手順1](https://cloud.githubusercontent.com/assets/1182962/17918779/dfa48088-6a02-11e6-8795-9ccbc440f148.png)
![手順2](https://cloud.githubusercontent.com/assets/1182962/17918823/338e3572-6a03-11e6-854f-8e1753210e93.png)


githubにプロジェクトのリポジトリを作成する
--
![https://github.com/](https://cloud.githubusercontent.com/assets/1182962/17918944/4e56f74e-6a04-11e6-80f8-a7e9470c03c8.png)

![](https://cloud.githubusercontent.com/assets/1182962/17919009/eb01d2d0-6a04-11e6-9d9a-c759a0a777c8.png)
