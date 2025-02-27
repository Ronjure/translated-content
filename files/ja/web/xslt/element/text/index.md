---
title: <xsl:text>
slug: Web/XSLT/Element/text
tags:
  - Text
  - XSLT
  - リファレンス
  - 要素
translation_of: Web/XSLT/Element/text
---
{{ XsltRef() }}

`<xsl:text>` 要素はリテラルテキストを出力ツリーに書き込みます。 `#PCDATA`、リテラルテキスト、およびエンティティ参照を含むことがあります。

### 構文

```
<xsl:text disable-output-escaping="yes" | "no">
	TEXT
</xsl:text>
```

### 必須属性

なし

### 任意属性

- `disable-output-escaping` (Netscape は変換の結果 - 下の「出力」 - を直列化しませんので、この属性は本質的に文脈上は無関係です。html エンティティを出力するには、代わりに数値を使用します (例: `&nbsp`の `&#160`) )
  - : 出力に書き込まれたときに特殊文字をエスケープするかどうかを指定します。使用可能な値は "`yes`" または "`no`" です。たとえば "`yes`" が設定されている場合、文字>は `>` ではなく"`&gt`" として出力されます。

### タイプ

命令は、テンプレート内に表示されます。

### 定義

XSLT, section 7.2

### Gecko のサポート

注意してサポートされています。
