ざっくりjQuery
==

ref. <http://alphasis.info/jquery-api/>

セレクター
--
+ $(SELECTOR)
+ $('#id')
+ $('.class')
+ $('tag')


イベント
--
+ `#on`
  + 指定する要素に特定のイベントが発生した場合に実行する処理を登録する
+ `#ready`
  + DOMの準備ができた時に実行する処理を登録する

### sample
```html
<button class="add">ADD</button>
<input type="number" class="count">
```
```javascript
$(function(){
  $(".add").on("click", function(){
    alert("click");
  });

  $(".count").on("change", function(e){
    var count = $(e.target).val()
    console.log(count)
  })
})
```

### イベントの種類
+ click
  + 要素がクリックされた
+ change
  + 要素に変更があった


属性
--
+ `#attr`
  + 要素のhtml属性値の取得および設定
+ `#addClass`
  + 要素にクラスを追加する
+ `#val`
  + 要素のvalue属性値の取得および設定
+ `#text`
  + 要素のテキスト要素を取得および設定
+ `#html`
  + 要素が内包する要素のhtmlを取得および設定


トラバース
--
+ `#find`
  + 要素の中から指定した要素を探索する
+ `#closest`
  + 要素の親要素をたどって指定した要素を探索する


スタイル
--
+ `#css`
  + 要素のstyle属性を書き換える


エフェクト
--
+ `#hide`
  + 要素を隠す


DOM操作
--
+ `#insertBefore`
  + 要素を指定した要素の前に追加する
+ `#append`
  + 要素内のコンテンツの最後に, 指定した要素を追加する
