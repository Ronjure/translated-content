---
title: 'あなたのスキルをテストしよう: 数学'
slug: Learn/JavaScript/First_steps/Test_your_skills:_Math
---
{{learnsidebar}}

このスキルテストの目的は、[JavaScript での基本演算 — 数値と演算子](/ja/docs/Learn/JavaScript/First_steps/Math) の記事を理解しているかどうかを評価することです。

> **Note:** 下記のインタラクティブエディターのソリューションで試してみることができますが、コードをダウンロードし、[CodePen](https://codepen.io/)、[jsFiddle](https://jsfiddle.net/)、[Glitch](https://glitch.com/) などのオンラインツールを利用すると、タスクに取り組むのに役立つかもしれません。
>
> 行き詰まったなら、私たちに助けを求めてください。 — このページの下部の [Assessment or further help](#assessment_or_further_help) セクションを参照

> **Note:** 下記の作成では、あなたのコードにエラーがあれば、このページの結果パネル（または、ダウンロード可能なバージョンでは、ブラウザーの JavaScript コンソール）に出力され、答えにたどり着くための助けとなります。

## 数学 1

基本演算子の知識をテストすることから始めましょう。4 つの数値を作成し、最初の 2 つを加算してください。そして 3 番目から 4 番目を減算してください。そうして出来た 2 つの 2 次結果を乗算して、48 になるようにしてください。最後に、この値が偶数であることを証明するテストを記述することも必要ですね。

では、完成イメージを再構築するために、下記のライブコードを更新してみましょう。次の手順に従ってください:

1.  数値の変数を 4 つ作成してください。変数にわかりやすい名前を付けてください。
2.  最初の 2 つの変数を加算し、その結果を別の変数に格納してください。
3.  3 番目の変数から 4 番目の変数を減算し、その結果を別の変数に格納してください。
4.  上記 2 つの工程の結果を乗算し、`finalResult` という変数に格納してください。その結果は 48 になるはずです。もしならなければ、初期の設定数値を調整する必要があります。
5.  最後に、`finalResult` が偶数であるかどうかをチェックする計算式を記述してください。結果を `evenOddResult` という変数に格納してください。

{{EmbedGHLiveSample("learning-area/javascript/introduction-to-js-1/tasks/math/math1.html", '100%', 400)}}

> **Note:** [このタスクのための準備済みファイルをダウンロード](https://github.com/mdn/learning-area/blob/master/javascript/introduction-to-js-1/tasks/math/math1-download.html) して、自身のエディターまたはオンラインエディターで動かせるようにしてください。

## 数学 2

2 番目のタスクでは、すでに結果が変数 `result` と `result2` に格納されている 2 つの計算式が提供されています。しかし、これらの結果は私たちが求めているものではありません。望む結果にするために、2 つの計算式を変更する必要がでてきます。

私たちは何を求めている？ 2 つの結果を乗算し、その結果を小数第 2 位までにフォーマットすると、最終結果は 10.42 になるようにしたいのです。

この完成イメージを再構築するために、下記のライブコードを更新してみましょう。次の手順に従ってください:

1.  `result` と `result2` を乗算し、結果を `result` に代入し戻す計算式を記述してください。これは、代入演算子の略記形を使いましょう。
2.  その結果を小数第 2 位までにフォーマットし、そして `finalResult` という変数に格納する 1 行コードを記述してください。
3.  `typeof` を使用して `finalResult` のデータ型をチェックしてください。実際には `string` 型であることがわかるでしょう！それを `number` 型に変換し、結果を `finalNumber` という変数に格納する 1 行コードを記述してください。
4.  `finalNumber` の値は `10.42` にならなければいけません。戻って、この最終結果が得られるように最初に与えられていた計算式を更新してください。数値や演算子は更新しないでくださいね。

{{EmbedGHLiveSample("learning-area/javascript/introduction-to-js-1/tasks/math/math2.html", '100%', 400)}}

> **Note:** [このタスクのための準備済みファイルをダウンロード](https://github.com/mdn/learning-area/blob/master/javascript/introduction-to-js-1/tasks/math/math2-download.html) して、自身のエディターまたはオンラインエディターで動かせるようにしてください。

## 数学 3

この記事の最後のタスクでは、いくつかのテストを記述していきましょう。各々がステートメントと 2 つの変数で構成されてる、3 つのグループが与えられています。各グループについて、与えられているステートメントを証明または反証するテストを記述してください。これらのテスト結果を、各々 `weightComparison`、`heightComparison`、そして `pwdMatch` という変数に格納してください。

{{EmbedGHLiveSample("learning-area/javascript/introduction-to-js-1/tasks/math/math3.html", '100%', 400)}}

> **Note:** [このタスクのための準備済みファイルをダウンロード](https://github.com/mdn/learning-area/blob/master/javascript/introduction-to-js-1/tasks/math/math3-download.html) して、自身のエディターまたはオンラインエディターで動かせるようにしてください。

## 評価またはさらなる助け

上記のインタラクティブエディターでこれらの作成を練習することができます。

あなたの制作物を評価してもらいたい、または行き詰まって助けを求めたい場合:

1.  あなたの制作物を、[CodePen](https://codepen.io/)、[jsFiddle](https://jsfiddle.net/)、または [Glitch](https://glitch.com/) のような共有可能なオンラインエディターに置いてください。いちから自身でコードを記述することもできますし、上記のセクションでリンク付けされている準備済みファイルを利用するのもよいでしょう。
2.  [MDN Discourse forum Learning category](https://discourse.mozilla.org/c/mdn/learn) で、評価を希望したり、助けを求めるポストを投稿してください。ポストには以下を含みましょう:

    - "Assessment wanted for Math 1 skill test" のような説明的なタイトル
    - あなたがこれまで試したことの詳細、そしてあなたが私たちに何をしてほしいか。例えば、行き詰まって助けが必要だとか、評価をしてほしいなど。
    - 評価してほしかったり、助けが必要な作成物へのリンク。共有可能なオンラインエディター（上記ステップ 1 で述べたもの）を使って。これは分かりやすくするためのよい実践方法でしょう — コードが見れない状態で、コーディング問題を抱えている人を助けることはとても難しいですよね。
    - 実際のタスクまたは評価ページのリンク。そうすれば、あなたがどの質問に助けが必要かがわかります。
