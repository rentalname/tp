Git ベストプラクティス
==

良いコミットメッセージ
--
ref. <http://postd.cc/how-to-write-a-git-commit-message/>

### 基本スタイル
```
1行目: 変更概要(50字くらい)
2行目: 空行
3行目: 変更の詳細(必要であれば)
```

### 変更概要
+ コミットの種別
  + Fix: バグ修正
  + Feature: 新規の(ファイル)機能追加
  + Improve: バグではない機能の修正
+ 対応するチケット番号
+ 文末にピリオドをつけない

### 変更の詳細
+ このコミットが解決している問題を説明する
+ どのように(how)**ではなく**, **なぜ** この変更をしたのかに重きを置く(どのように変更したかはコードを見れば分かる)
+ この変更で生じる副作用や直感的には分からない他の結果は生じないか？何かあればここで説明する
+ 一行を72文字以内で折り返す

### コミットの粒度
+ 複数のことを一つのコミットで解決しない
  + 機能の追加
  + バグの修正
  + Typoの修正
  + リファクタリング
  + コードの整形

### 参考リンク
+ [Git コミットメッセージのプラクティスまとめ](http://morizyun.github.io/blog/git-commit-log-format/)
+ [gitにおけるコミットログ/メッセージ例文集100](http://anond.hatelabo.jp/20160725092419)
+ [Gitのコミットメッセージの書き方](http://blog.toshimaru.net/git-29764/)
+ [Gitのコミットメッセージの書き方](http://postd.cc/how-to-write-a-git-commit-message/)
+ [Gitのコミットメッセージの書き方](http://qiita.com/itosho/items/9565c6ad2ffc24c09364)
+ [Gitのコミット作法(コミット単位とコミットメッセージ)を調べてまとめてみた](http://d.hatena.ne.jp/shouh/20151202/1449059707)


gitコマンドの補完/gitプロンプトの利用
--
+ ref.
  + <http://qiita.com/koyopro/items/3fce94537df2be6247a3>
  + <http://qiita.com/varmil/items/9b0aeafa85975474e9b6>

```bash
# ~/.bash_profile

# スクリプト読み込み
source $(brew --prefix git)/etc/bash_completion.d/git-completion.bash
source $(brew --prefix git)/etc/bash_completion.d/git-prompt.sh


source $HOME/.git-completion.bash
source $HOME/.git-prompt.sh

# プロンプトに各種情報を表示
GIT_PS1_SHOWDIRTYSTATE=1
GIT_PS1_SHOWUPSTREAM=1
GIT_PS1_SHOWUNTRACKEDFILES=
GIT_PS1_SHOWSTASHSTATE=1

############### ターミナルのコマンド受付状態の表示変更
# \u ユーザ名
# \h ホスト名
# \W カレントディレクトリ
# \w カレントディレクトリのパス
# \n 改行
# \d 日付
# \[ 表示させない文字列の開始
# \] 表示させない文字列の終了
# \$ $
export PS1='\[\033[1;32m\]\u\[\033[00m\]:\[\033[1;34m\]\w\[\033[1;31m\]$(__git_ps1)\[\033[00m\] \$ '
##############
```
