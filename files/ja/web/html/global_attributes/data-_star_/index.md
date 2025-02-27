---
title: data-*
slug: Web/HTML/Global_attributes/data-*
tags:
  - Global attributes
  - HTML
  - Reference
translation_of: Web/HTML/Global_attributes/data-*
---
{{HTMLSidebar("Global_attributes")}}

**`data-*`** [グローバル属性](/ja/docs/Web/HTML/Global_attributes) は**カスタムデータ属性**と呼ばれる属性の組を作り、[HTML](/ja/docs/Web/HTML "HTML") と、スクリプトによる [DOM](/ja/docs/Web/API/Document_Object_Model "DOM") 表現との間で、固有の情報を交換できるようにします。

{{EmbedInteractiveExample("pages/tabbed/attribute-data.html","tabbed-standard")}}

すべてのカスタムデータは、属性を設定した要素の {{domxref("HTMLElement")}} インターフェイスを通して使用できます。 {{domxref("HTMLElement.dataset")}} プロパティがそれらへのアクセス手段を提供します。
`*` は、 [XML 名の作成規則](http://www.w3.org/TR/REC-xml/#NT-Name)に加えて以下の制約に従う名前に置き換えることができます。

- 大文字小文字にかかわらず、名前を `xml` で始めてはならない。
- 名前にセミコロン (`U+003A`) を含めてはならない。
- 名前に大文字を含めてはならない。

なお、 {{domxref("HTMLElement.dataset")}} プロパティは {{domxref("DOMStringMap")}} であり、またカスタムデータ属性名のハイフン (`U+002D`) はその次の文字を大文字化したもの (キャメルケース) に変換されるので、 _data-test-value_ は `HTMLElement.dataset.testValue` (または `HTMLElement.dataset["testValue"]`) としてアクセスできます。

### 使用方法

`data-*` 属性を追加すると通常の HTML 要素でも、より複雑で強力なプログラムオブジェクトになります。例えばゲームで宇宙船の "[スプライト](<https://ja.wikipedia.org/wiki/%E3%82%B9%E3%83%97%E3%83%A9%E3%82%A4%E3%83%88_(%E6%98%A0%E5%83%8F%E6%8A%80%E8%A1%93)>)_"_ を、単純な {{HTMLElement("img")}} 要素に [`class`](/ja/docs/Web/HTML/Global_attributes/class) 属性といくつかの `data-*` 属性を設定したもので表すことができるでしょう。

```html
<img class="spaceship cruiserX3" src="shipX3.png"
  data-ship-id="324" data-weapons="laserI laserII" data-shields="72%"
  data-x="414354" data-y="85160" data-z="31940"
  onclick="spaceships[this.dataset.shipId].blasted()">
```

もっと深い HTML のデータ属性の使用については、[データ属性の使用](/ja/docs/Learn/HTML/Howto/Use_data_attributes)を参照してください。

## 仕様書

| 仕様書                                                                                                                                               | 状態                             | 備考                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------- |
| {{SpecName('HTML WHATWG', "dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes", "data-*")}} | {{Spec2('HTML WHATWG')}} | 最新のスナップショットである {{SpecName('HTML5.1')}} から変更なし。                            |
| {{SpecName('HTML5.1', "dom.html#element-attrdef-global-data", "data-*")}}                                                     | {{Spec2('HTML5.1')}}     | {{SpecName('HTML WHATWG')}} のスナップショット、 {{SpecName('HTML5 W3C')}} から変更なし |
| {{SpecName('HTML5 W3C', "dom.html#element-attrdef-global-data", "data-*")}}                                                 | {{Spec2('HTML5 W3C')}}     | {{SpecName('HTML WHATWG')}} のスナップショット、初回定義。                                     |

## ブラウザーの互換性

{{Compat("html.global_attributes.data_attributes")}}

## 関連情報

- すべての[グローバル属性](/ja/docs/Web/HTML/Global_attributes)
- これらの値を読み書きできる {{domxref("HTMLElement.dataset")}} プロパティ
- [データ属性の使用](/ja/docs/Learn/HTML/Howto/Use_data_attributes)
