---
title: DOMTokenList.remove()
slug: Web/API/DOMTokenList/remove
---
{{APIRef("DOM")}}

**`remove()`** は {{domxref("DOMTokenList")}} インターフェイスのメソッドで、リストから指定されたトークンを取り除きます。

## 構文

```js
remove(token);
remove(token, token);
remove(token, token, token);
...
```

## 引数

- `token`
  - : リストから取り除きたいトークンを表す文字列です。
    文字列がリストにない場合は、エラーは発生せず、何も起こりません。

### 返値

なし。

## 例

以下の例では、 {{htmlelement("span")}} 要素に設定されたクラスのリストを、 `DOMTokenList` として受け取るのに {{domxref("Element.classList")}} を使用します。それからリストからトークンを取り除き、 `<span>` の {{domxref("Node.textContent")}} の中にリストを書き込みます。

最初に HTML です。

```html
<div id="ab" class="a b c"></div>
<div id="a" class="a b c"></div>
```

そして JavaScript です。

```js
const span = document.getElementById("ab");
const classes = span.classList;
classes.remove("c");
span.textContent = classes;
```

複数のクラスを一度に削除するために、複数のトークンを渡すことができます。渡す順序は、リスト中に出現する順序と一致している必要はありません。

```js
const span2 = document.getElementById("a")
const classes2 = span2.classList;

classes2.remove("c", "b");
span2.textContent = classes2;
```

出力結果は以下のようになります。

{{ EmbedLiveSample('Examples', '100%', 60) }}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
