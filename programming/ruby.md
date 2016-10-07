Ruby入門
==

達成目標
--
1. Rubyによるプログラミングを行うための知識を習得する

学習内容
--
+ 基礎的な文法について
+ 標準クラス
+ デバッグ


Ruby基礎文法
--

### Rubyコードの実行方法
+ rubyスクリプトファイルを実行
  + rubyスクリプトファイルを作成する
  + `$ ruby script.rb`
+ `pry`/`irb`を使う
```sh
$ gem install pry
$ pry

> 1 + 1
#=> 2
```

+ atomのプラグインを使う
  + rubyスクリプトファイルをatomで作成
  + エディタ上で[cmd + i]

### たのしいRuby Ch. 1
+ 30分で全体に目を通す
+ 過去の経験から, 理解できる文法部分については, 飛ばす
+ 気になったところは付箋を付けるなどして, マークする
+ 動作的に気になるところがあったら実際にコードを書いて動かしてみる

#### おさらい
+ `#puts`
+ `#p`
+ if
  + then は基本省略する
  + else if ではなく`elsif`

### たのしいRuby Ch.2

#### Array
+ 15分で目を通す
+ `#each`メソッドの利用に関して, コードを書いて動作を確認する

#### Hash
+ 20分で目を通す
+ 2種類のHashリテラルについて, 書き方を確認する
+ `#each`メソッドの利用に関して, コードを書いて動作を確認する

#### 正規表現
+ 10分で目を通す
+ 時間が余ったら, [ドキュメント](http://doc.okkez.net/static/2.3.0/doc/spec=2fregexp.html)をながめてください

### Ch. 4 オブジェクトと変数・定数
+ 15分で全体に目を通す

#### おさらい
+ オブジェクト
+ クラス
+ 変数
  + ローカル変数
  + インスタンス変数
  + クラス変数
  + 変数スコープ
+ 定数
+ 多重代入

### Ch. 5 条件判断
+ 15分で全体に目を通す

#### Rubyでの真偽
<table>
  <tr>
    <td>真</td>
    <td>false以外の全て(true, 0, "false", "", [], ...)</td>
  </tr>
  <tr>
    <td>偽</td>
    <td>nil, false</td>
  </tr>
</table>

#### if/unlessの使い分けについて
+ 条件節が肯定表現になるようにif/unlessを選ぶといいです
```ruby
# bad
unless !condition
  # do something
end

# good
if condition
  # do something
end

# bad
if !condition
  # do something
end

# good
unless condition
  # do something
end
```

+ else句を含む場合は, ifを使って書きましょう.
```ruby
# bad
unless condition
  # do something 1
else
  # do something 2
end

# good
if condition
  # do something 2
else
  # do something 1
end
```

+ condition部分を工夫することで, ifを使う形に書き直せる場合があります. ifを使う方が多くのプログラマにとって読みやすいです.
```ruby
n = -100
# good
unless n.negative?
  # do something
end

# more than better
if n.positive?
  # do something
end
```

#### case
+ `#===`が呼び出される
+ <http://melborne.github.io/2013/02/25/i-wanna-say-something-about-rubys-case/>

#### 後置if, 後置unless
+ 直感的には挙動がわかりにくくなる
+ 読んだときに違和感が表れることを利用して, ガード節を記述する際に利用すると効果的

### Ch. 6 繰り返し
+ 30分で目を通す
+ 動作が予想できないコードが合った場合は, コードを書いて実行する

### Ch. 7 メソッド
+ 30分で目を通す

#### おさらい
+ インスタンスメソッド
+ クラスメソッド
+ 関数的メソッド
+ 可変長引数
```ruby
def foo(*args)
end

foo(1, 2, 3, 4)
```
+ デフォルト値
```ruby
def foo(n=3)
end

foo(5)
foo
```
+ キーワード引数
```ruby
def foo(key1:, key2: false)
end

foo(key1: "hello")
foo(key1; "bye", key2: true)
```

#### すこし特殊なメソッド定義
+ `#attr=`
```ruby
class Person
  def age=(n)
    @age = n
  end

  def adult?
    @age >= 20
  end
end

ashina = Person.new
ashina.age = 100
ashina.adult?
```

+ `#[]`
```ruby
class FizzBuzz
  def self.[](n)
    if n % 15 == 0
      "fizzbuzz"
    elsif n % 3 == 0
      "fizz"
    elsif n % 5 == 0
      "buzz"
    else
      n
    end
  end
end
```

+ `#[]=`
```ruby
class Recipe
  def initialize
    @ingredients = {}
  end

  def []=(ingredient, amount)
    @ingredients[material] = amount
  end

  def show
    @ingredients.each do |ingredient, amount|
      puts "#{material} ... #{amount}"
    end
  end
end

bread = Recipe.new

bread[:小麦粉] = "400g"
bread[:塩] = "5g"
bread[:砂糖] = "12g"
bread[:水] = "220g"

bread.show
```

クラス・モジュール
--

### Ch. 8 クラスとモジュール

#### クラス
+ クラスとインスタンス
+ クラス継承
+ class文
+ `#initialize`
+ インスタンス変数
+ インスタンスメソッド
+ アクセスメソッド
+ `self`
+ クラスメソッド
+ 定数
+ クラス変数
+ public/protected/private
  + private => レシーバを指定してメソッドを呼び出せない
  + protected => メソッドを同一クラスであれば, インスタンスメソッドとして呼び出せる
+ クラス拡張
  + オープンクラス
  + 継承

#### alias/undef
+ 3分くらいで流し読み

#### 特異クラス
+ コードを書いて動作を確認する

#### モジュール
+ Mix-in
+ 名前空間の提供

+ モジュールの作成
+ 定数
+ メソッドの定義
+ Mix-in
+ extend
+ クラスとMix-in

+ オブジェクト指向
  + 時間があったら読む

標準クラス
--
Ch. 12 から 本文を読みつつ章末の練習問題を解く

デバッグ
--
コーディング中に遭遇しやすいエラーメッセージについて確認する

+ endが足りない
```ruby
if 0.zero?
  puts 0
else
  puts "One"
endo
```

+ ハッシュリテラルの不備
```ruby
def foo
  aaa: 100
end
```

+ ハッシュリテラルとブロックの混乱
```ruby
h = {a: 100}

h.merge {b: 200}
```

+  undefined method `+' for nil:NilClass (NoMethodError)
```ruby
h = {a: 100, b: 200}

h["a"] + 100
```

+ undefined local variable or method `number' for main:Object (NameError)
```ruby
numbers = [1, 3, 5, 7, 11]

puts number
```

+ dynamic constant assignment
```ruby
def init
  STEP = 1
end

init
```
### ref.
+ http://qiita.com/scivola/items/3017068a354892b239f4
+ http://qiita.com/scivola/items/77017693de371ab49667
+ http://e-sahf.jp/class/13/error.htm
