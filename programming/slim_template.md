Slimテンプレート
==
+ <http://slim-lang.com/>


### Install
+ gem "slim-rails"

### サンプル
```slim
doctype html
html
  head
    title Slim Examples
    meta name="keywords" content="template language"
    meta name="author" content=author
    javascript:
      alert('Slim supports embedded javascript!')

  body
    h1 Markup examples

    #content
      p This example shows you how a basic Slim file looks like.

      == yield

      - unless items.empty?
        table
          - items.each do |item|
            tr
              td.name = item.name
              td.price = item.price
    div id="footer"
      = render 'footer'
      | Copyright © #{year} #{author}
```

### 構文
+ doctype宣言
```slim
doctype html
```

+ id属性
```slim
h1#site_title
```

+ class属性
```slim
p.message
```

+ text要素
```slim
p
  | はろーわーるど
```

+ attr属性
```slim
a href="#"
```

+ rubyコード
```slim
= Time.now
```

```slim
- [:foo, :bar, :baz].each do |sym|
  p
    = sym
```
