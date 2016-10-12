rails環境でのデバッグ
==

better_errors
--

### 導入
+ Gemfileに`gem "better_errors"`を追加
+ Gemfileに`gem "binding_of_caller"`を追加

### 機能
`rails s`でサーバーが起動している際に, アプリケーション側で例外が発生した時, 例外を発生したコードのコンテキストでデバッガーを利用できるようになる.
デバッグ操作はブラウザ上で実行できる.

### Tips
`better_errors`が提供するデバッグ画面は, `pry`に比べて操作性に劣る.
better_errorsのデバッグ画面で, `binding.pry`を実行することで, `pry`を使ってターミナル上でデバッグを続けることができる.

pry-rails
--

### [State navigation](https://github.com/pry/pry/wiki/State-navigation)

log
--

### lessを使ったログファイルの監視
+ `-R`
  + 色つきのログを色つきのまま表示できるようにする
+ `+F`
  + ファイルに追記があった時に逐次読み込む

rails.logger
--

javascript
--
+ デベロッパーツール
+ log
+ debugger

html
--
+ デベロッパーツール

css
--
+ デベロッパーツール
