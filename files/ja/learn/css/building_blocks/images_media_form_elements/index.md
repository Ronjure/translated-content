---
title: 画像・メディア・フォーム要素
slug: Learn/CSS/Building_blocks/Images_media_form_elements
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/CSS/Building_blocks/Sizing_items_in_CSS", "Learn/CSS/Building_blocks/Styling_tables", "Learn/CSS/Building_blocks")}}

このレッスンでは、特定の要素が CSS でどのように扱われるかを見ていきます。画像・メディア・フォーム要素では、CSS でスタイルを設定するにあたって通常のボックスとは少し異なる動作をします。何が可能で何が不可能かを理解することで、フラストレーションを軽減することができます。このレッスンでは、知っておくべきことのをいくつかを取り上げます。

| 前提条件: | 基本的なコンピューターリテラシー、[基本的なソフトウェアがインストールされている](/ja/Learn/Getting_started_with_the_web/Installing_basic_software)こと、[ファイルの扱い](/ja/Learn/Getting_started_with_the_web/Dealing_with_files)、HTML の基本（[HTML 入門](/ja/docs/Learn/HTML/Introduction_to_HTML)）および CSS に関するアイデア（[CSS の第一歩](/ja/docs/Learn/CSS/First_steps)）に関する基本的な知識を得ている。 |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 目的:     | CSS でスタイルを設定したときに一部の要素が異常に動作することを理解する。                                                                                                                                                                                                                                                                                                                                               |

## 置換要素

画像とビデオは、**[置き換えられた要素](/ja/docs/Web/CSS/Replaced_element)**として説明されています。これは、CSS がこれらの要素の内部レイアウトに影響を与えることはできず、他の要素の中でのページ上の位置のみに影響を与えることを意味します。ただし、後で説明するように、CSS が画像に対して様々なことができます。

画像や動画などの特定の置換された要素は、アスペクト比を持つものとしても記述されています。これは、水平方向 (x) と垂直方向 (y) の両方の寸法を持ち、デフォルトではファイルの本質的な寸法を使って表示されることを意味します。

## 画像サイズ

これらのレッスンを受けてすでにお分かりのように、CSS ではすべてのものがボックスを生成します。画像ファイルの固有の寸法よりも小さいか大きいサイズの画像をボックス内に配置すると、ボックスよりも小さく表示されるか、ボックスをオーバーフローさせてしまいます。オーバーフローで何が起こるかについて決定を下す必要があります。

以下の例では、2 つのボックスがあり、どちらもサイズは 200 ピクセルです。

- 1 つは 200 ピクセル未満の画像を含んでいます。これはボックスよりも小さく、それを埋めるために引き伸ばしません。
- もう 1 つは 200 ピクセルより大きく、ボックスをオーバーフローします。

{{EmbedGHLiveSample("css-examples/learn/images/size.html", '100%', 1000)}}

では、オーバーフローの問題について何ができるでしょうか？

[前のレッスン](/ja/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS)で学んだように、一般的な手法は、画像の {{cssxref("max-width")}} を 100％にすることです。これにより、画像のサイズはボックスよりも小さくなりますが、大きくはなりません。この手法は、[`<video>`](/ja/docs/Web/HTML/Element/video)や [`<iframe>`](/ja/docs/Web/HTML/Element/iframe) などの他の置換された要素でも機能します。

**上記の例 `max-width: 100%` の `<img>` 要素に追加してみてください。小さい画像は変更されないままですが、大きい画像はボックスに収まるように小さくなります。**

コンテナー内のイメージについて他の選択を行うことができます。例えば、ボックスを完全に覆うように画像のサイズを変更したい場合があります。

ここでは、{{cssxref("object-fit")}} プロパティが役立ちます。`object-fit` 置き換えられた要素を使用する場合、さまざまな方法でボックスに合うようにサイズを変更できます。

以下では、値 `cover` を使用して画像を縮小し、アスペクト比を維持してボックスをきれいに埋めます。アスペクト比が維持されているため、画像の一部がボックスでトリミングされます。

{{EmbedGHLiveSample("css-examples/learn/images/object-fit.html", '100%', 1000)}}

`contain` を値として使用する場合、ボックス内に収まるほど小さくなるまで画像が縮小されます。これは、ボックスと同じアスペクト比ではない場合、「レターボックス」になります。

`fill` を試すこともできます 。これは、ボックスを塗りつぶしますが、アスペクト比を維持しません。

## レイアウト内の置換要素

置換された要素にさまざまな CSS レイアウト手法を使用すると、他の要素とは動作が少し異なる場合があります。 たとえば、フレックスまたはグリッドレイアウトでは、要素はデフォルトで領域全体に拡大されます。 画像は伸縮せず、代わりにグリッド領域またはフレックスコンテナーの始点に揃えられます。

次の例では、2 列 2 行のグリッドコンテナーがあり、4 つのアイテムが含まれています。すべての `<div>` 要素には背景色があり、行と列に合わせて伸縮します。ただし、画像は引き伸ばされません。

{{EmbedGHLiveSample("css-examples/learn/images/layout.html", '100%', 1000)}}

これらのレッスンを順番に実行している場合は、まだレイアウトを確認していない可能性があります。置き換えられた要素は、グリッドまたはフレックスレイアウトの一部になると、基本的にレイアウトによって不自然に引き伸ばされないようにするために、異なるデフォルトの動作になることに注意してください。

画像を強制的に引き伸ばして、グリッドセルを塗りつぶすには、次のような操作を行う必要があります。

```css
img {
  width: 100%;
  height: 100%;
}
```

ただし、これは画像を引き伸ばすため、おそらく望んでいることではありません。

## フォーム要素

CSS でのスタイル設定に関しては、フォーム要素はトリッキーな問題であり、[HTML フォームモジュール](/ja/docs/Learn/HTML/Forms)には、フォーム要素のスタイル設定に関する詳細なガイドが含まれていますが、ここでは完全には再現しません。記事のこのセクションでは、強調すべきいくつかの重要な点があります。

多くのフォームコントロールは [`<input>`](/ja/docs/Web/HTML/Element/input) 要素によってページに追加されます。これは、テキスト入力などの単純なフォームフィールドから、色や日付の選択などの HTML5 で追加されたより複雑なフィールドまでを定義します。の `<textarea>` などの追加要素や、`<fieldset>` や `<legend>` などのフォームの一部を格納したりラベルを貼ったりするために使われる要素もあります。

HTML5 には、Web 開発者が必須フィールド、さらには入力する必要があるコンテンツのタイプを指定できるようにする属性も含まれています。ユーザーが予期しない何かを入力したり、必須フィールドを空白のままにしたりすると、ブラウザーにエラーメッセージが表示されることがあります。 ブラウザーによって、このようなアイテムのスタイリングやカスタマイズがどの程度可能なのかについては一貫性がありません。

### テキスト入力欄のスタイル

`<input type="text">`、`<input type="email">`、`<textarea>` 要素などのテキスト入力を可能にする要素は、スタイルを整えるのが非常に簡単で、ページ上の他のボックスと同じように振る舞う傾向があります。しかし、これらの要素のデフォルトのスタイルは、ユーザーがサイトを訪問する際に使用するオペレーティングシステムやブラウザーによって異なります。

以下の例では、CSS を使用していくつかのテキスト入力にスタイルを設定しています。境界線、マージン、パディングなどがすべて期待どおりに適用されていることがわかります。属性セレクターを使用して、さまざまな入力タイプをターゲットにしています。ボーダーを調整し、フィールドに背景色を追加し、フォントとパディングを変更して、このフォームの外観を変更してみてください。

{{EmbedGHLiveSample("css-examples/learn/images/form.html", '100%', 1000)}}

> **Warning:** **重要**：フォーム要素のスタイルを変更するときは、ユーザーがフォーム要素であることをユーザーに明確に伝えるように注意する必要があります。周囲のコンテンツとほとんど見分けがつかない境界線や背景のないフォーム入力を作成することもできますが、これにより認識や入力が非常に難しくなります。

このコースの HTML パートの[フォームスタイリング](/ja/docs/Learn/HTML/Forms/Styling_HTML_forms)に関するレッスンで説明したように、より複雑な入力タイプの多くはオペレーティングシステムによってレンダリングされ、スタイリングにアクセスできません。そのため、フォームは訪問者によってかなり違って見えることを常に想定し、複雑なフォームをいくつかのブラウザーでテストする必要があります。

### 継承とフォーム要素

一部のブラウザーでは、フォーム要素はデフォルトではフォントのスタイルを継承しません。そのため、フォームのフィールドがボディや親要素で定義されたフォントを使用するようにしたい場合は、CSS にこのルールを追加する必要があります。

```css
button,
input,
select,
textarea {
  font-family : inherit;
  font-size : 100%;
}
```

### フォーム要素と box-sizing

ブラウザー間で、フォーム要素は、さまざまなウィジェットに対してさまざまなボックスサイズ設定ルールを使用します。[ボックスモデルのレッスンで](/ja/docs/Learn/CSS/Building_blocks/The_box_model)`box-sizing` プロパティについて学習しました。フォームのスタイル設定時にこの知識を使用して、フォーム要素に幅と高さを設定するときに一貫したエクスペリエンスを確保できます。

一貫性を保つために、すべての要素でマージンとパディングに `0` を設定し、特定のコントロールをスタイリングするときにこれらを追加することをお勧めします

```css
button,
input,
select,
textarea {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
```

### その他の便利な設定

上記のルールに加えて、スクロールバーが不要な場合に IE がスクロールバーを表示しないよう `overflow: auto` に `<textarea>`s を設定する必要があります。

```css
textarea {
  overflow: auto;
}
```

### リセット処理としてまとめる

最後のステップとして、上記で説明したさまざまなプロパティを次の「フォームリセット」にラップして、作業の一貫性のあるベースを提供できます。これには、最後の 3 つのセクションで言及したすべてのアイテムが含まれます。

```css
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
  box-sizing: border-box;
  padding: 0; margin: 0;
}

textarea {
  overflow: auto;
}
```

> **Note:** 正規化スタイルシートは、すべてのプロジェクトで使用する一連のベースラインスタイルを作成するために、多くの開発者によって使用されています。通常、これらは上記で説明したものと同様のことを行います。CSS で独自の作業を行う前に、ブラウザー間で異なるものがすべて一貫したデフォルトに設定されていることを確認してください。ブラウザーは通常、以前より一貫性があるため、以前ほど重要ではありません。ただし、1 つの例を見てみたい場合は、[Normalize.css を](http://necolas.github.io/normalize.css/)チェックしてください[。Normalize.css](http://necolas.github.io/normalize.css/)は、多くのプロジェクトでベースとして使用されている非常に人気のあるスタイルシートです。

フォームのスタイル設定の詳細については、これらのガイドの HTML セクションにある 2 つの記事をご覧ください。

- [HTML フォームのスタイル](/ja/docs/Learn/HTML/Forms/Styling_HTML_forms)
- [HTML フォームの高度なスタイル](/ja/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms)

## まとめ

このレッスンでは、CSS で画像、メディア、およびその他の異常な要素を操作するときに発生するいくつかの違いを強調しました。次の記事では、HTML テーブルをスタイルする必要がある場合に役立ついくつかのヒントについて説明します。

{{PreviousMenuNext("Learn/CSS/Building_blocks/Sizing_items_in_CSS", "Learn/CSS/Building_blocks/Styling_tables", "Learn/CSS/Building_blocks")}}

## このモジュール

1.  [カスケードと継承](/ja/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
2.  [CSS セレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors)

    - [要素・クラス・ID によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)
    - [属性によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)
    - [擬似クラスおよび疑似要素によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)
    - [結合子](/ja/docs/Learn/CSS/Building_blocks/Selectors/Combinators)

3.  [ボックスモデル](/ja/docs/Learn/CSS/Building_blocks/The_box_model)
4.  [背景と枠線](/ja/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders)
5.  [テキスト方向の操作](/ja/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)
6.  [要素のはみ出し（オーバーフロー）](/ja/docs/Learn/CSS/Building_blocks/Overflowing_content)
7.  [CSS の値と単位](/ja/docs/Learn/CSS/Building_blocks/Values_and_units)
8.  [CSS によるサイズ設定](/ja/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS)
9.  [画像・メディア・フォーム要素](/ja/docs/Learn/CSS/Building_blocks/Images_media_form_elements)
10. [表のスタイリング](/ja/docs/Learn/CSS/Building_blocks/Styling_tables)
11. [CSS のデバッグ](/ja/docs/Learn/CSS/Building_blocks/Debugging_CSS)
12. [CSS の整理](/ja/docs/Learn/CSS/Building_blocks/Organizing)
