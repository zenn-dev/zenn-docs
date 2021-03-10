---
title: "ZennのMarkdown記法"
emoji: "👩‍💻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["markdown", "zenn"]
published: true
---

このページではZennのマークダウン記法を一覧で紹介します。

# 見出し
```
# 見出し1
## 見出し2
### 見出し3
#### 見出し4
```

# リスト
```
- Hello!
- Hola!
  - Bonjour!
  * Hi!
```
- Hello!
- Hola!
  - Bonjour!
  * Hi!

リストのアイテムには`*`もしくは`-`を使います。


### 番号付きリスト
```
1. First
2. Second
```
1. First
2. Second


# テキストリンク
```
[アンカーテキスト](リンクのURL)
```
[アンカーテキスト](https://zenn.dev)
`Ctrl + K`のショートカットでも挿入できます。



# 画像
```
![altテキスト](https://画像のURL)
```
![altテキスト](https://storage.googleapis.com/zenn-user-upload/gxnwu3br83nsbqs873uibiy6fd43)

### 画像の横幅を指定する

画像の表示が大きすぎる場合は、URLの後に半角スペースを空けて`=○○x`と記述すると、画像の幅をpx単位で指定できます。

```
![altテキスト](https://画像のURL =250x)
```
![altテキスト](https://storage.googleapis.com/zenn-user-upload/gxnwu3br83nsbqs873uibiy6fd43 =250x)

### キャプションをつける
画像のすぐ下の行に`*`で挟んだテキストを配置すると、キャプションのような見た目で表示されます。
```
![](https://画像のURL)
*キャプション*
```

![](https://storage.googleapis.com/zenn-user-upload/gxnwu3br83nsbqs873uibiy6fd43 =250x)
*captions*

### 画像にリンクを貼る
以下のようにすることで画像に対してリンクを貼ることもできます。

```
[![altテキスト](画像のURL)](リンクのURL)
```



# テーブル
```
| Head | Head | Head |
| ---- | ---- | ---- |
| Text | Text | Text |
| Text | Text | Text |
```
| Head | Head | Head |
| ---- | ---- | ---- |
| Text | Text | Text |
| Text | Text | Text |



# コードブロック
コードは「```」で挟むことでブロックとして挿入できます。以下のように言語を指定するとコードへ装飾（シンタックスハイライト）が適用されます。

> \```js
> 
> \```

```js
const great = () => {
  console.log("Awesome")
}
```

シンタックスハイライトにはPrism.jsを使用しています。
[📄 対応言語の一覧 →](https://prismjs.com/#supported-languages)

### ファイル名を表示する
`言語:ファイル名`と`:`区切りで記載することで、ファイル名がコードブロックの上部に表示されるようになります。

> \```js:ファイル名
> 
> \```


```js:fooBar.js
const great = () => {
  console.log("Awesome")
}
```

### diffのシンタックスハイライト

2021/01/25〜、`diff`と言語のハイライトを同時に適用できるようになりました。以下のように`diff`と`言語名`を半角スペース区切りで指定します。


> \```diff js
> 
> \```


```diff js
@@ -4,6 +4,5 @@
+    const foo = bar.baz([1, 2, 3]) + 1;
-    let foo = bar.baz([1, 2, 3]);
```

なお、`diff`の使用時には、先頭に`+`、`-`、`半角スペース`のいずれが入っていない行はハイライトされません。

同時にファイル名を指定することも可能です。

> \```diff js:ファイル名
> 
> \```

```diff js:fooBar.js
@@ -4,6 +4,5 @@
+    const foo = bar.baz([1, 2, 3]) + 1;
-    let foo = bar.baz([1, 2, 3]);
```


# 数式

Zennでは**KaTeX**による数式表示に対応しています。

### 数式のブロックを挿入する
`$$`で記述を挟むことで、数式のブロックが挿入されます。たとえば


```
$$
e^{i\theta} = \cos\theta + i\sin\theta
$$
```
は以下のように表示されます。

$$
e^{i\theta} = \cos\theta + i\sin\theta
$$

:::message
`$$`の前後は空の行でないと正しく埋め込まれないことがあります。
:::

### インラインで数式を挿入する
`$a\ne0$`というように`$`ひとつで挟むことで、インラインで数式を含めることができます。たとえば$a\ne0$のようなイメージです。



# 引用
```
> 引用文
> 引用文
```

> 引用文
> 引用文

# 注釈
注釈を指定するとページ下部にその内容が表示されます。

```
脚注の例[^1]です。インライン^[脚注の内容その2]で書くこともできます。

[^1]: 脚注の内容その1
```

脚注の例[^1]です。インライン^[脚注の内容その2]で書くこともできます。

[^1]: 脚注の内容その1


# 区切り線
```
-----
```
-----




# インラインスタイル
```
*イタリック*
**太字**
~~打ち消し線~~
インラインで`code`を挿入する
```
*イタリック*
**太字**
~~打ち消し線~~
インラインで`code`を挿入する

## インラインのコメント
自分用のメモをしたいときはHTMLのコメント記法を使用できます。

```html
<!-- TODO: ◯◯について追記する -->
```

<!-- コメントテスト -->

この形式で書いたコメントは公開されたページ上では表示されません。ただし、複数行のコメントには対応していないのでご注意ください。


# Zenn独自の記法

### メッセージ

```
:::message
メッセージをここに
:::
```


:::message
メッセージをここに
:::

```
:::message alert
警告メッセージをここに
:::
```

:::message alert
警告メッセージをここに
:::


### アコーディオン（トグル）

```
:::details タイトル
表示したい内容
:::
```

:::details タイトル
表示したい内容
:::

分かりづらいのですが「detail」ではなく「details」です。

# コンテンツの埋め込み

### リンクカード

```bash
# URLだけの行
https://zenn.dev/zenn/articles/markdown-guide
```

URLだけが貼り付けられた行があると、その部分がカードとして表示されます。

https://zenn.dev/zenn/articles/markdown-guide

また`@[card](URL)`という書き方でカード型のリンクを貼ることもできます。

:::details アンダースコア _ を含むURLが正しく認識されない場合
[markdownパーサの仕様](https://zenn.dev/catnose99/scraps/e94c8e789f846a)により、を含むURLで、正しくURLが認識されないことがあります。

```
https://zenn.dev/__example__
```

> https://zenn.dev/__example__

#### 対処法

1. カード型のリンクとして表示したい場合は
`@[card](ここにURL)`という書き方をしてください
2. 単純にリンク化されたURLを貼り付けたい場合は`<https://zenn.dev/__example__>`のような形で`<`と`>`でURLを囲むようにしてください
:::



### ツイート

```bash
# ツイートのURLだけの行（前後に改行が必要です）
https://twitter.com/jack/status/20
```

以前は`@[tweet](ツイートのURL)`の記法を採用していましたが、2020/12/27〜URLを貼り付けるだけでツイートを埋め込むことが可能になりました。

:::details アンダースコア _ を含むURLが正しく認識されない場合
[markdownパーサの仕様](https://zenn.dev/catnose99/scraps/e94c8e789f846a)により、URLの`/`の区切りの中に2つ以上アンダースコア（`_`）を含むと、自動リンクが途中で途切れてしまいます。

```
https://twitter.com/__example__/status/12345678910
```

> https://twitter.com/__example__/status/12345678910

#### 対処法

このようなURLでは`@[tweet](ツイートのURL)`という書き方をしていただくようお願いします。

:::



#### リプライ元のツイートを非表示にする

リプライを埋め込んだ場合、デフォルトでリプライ元のツイートも含まれて表示されます。`ツイートのURL?conversation=none`のようにクエリパラメータに`conversation=none`を指定すると、リプライ元のツイートが含まれなくなります。


### YouTube

```bash
# YouTubeのURLだけの行（前後に改行が必要です）
https://www.youtube.com/watch?v=WRVsOCh907o
```

以前は`@[youtube](YouTubeの動画ID)`という記法を採用していましたが、2021/03/03〜URLを貼り付けるだけで動画を埋め込むことが可能になりました。


### GitHub Gist

```bash
@[gist](GistのページURL)
```

2020/12/28〜対応しました。特定のファイルだけ埋め込みたい場合は`@[gist](https://gist.github.com/foo/bar?file=example.json)`のようにクエリ文字列で`?file=ファイル名`という形で指定します。


### CodePen

```
@[codepen](ページのURL)
```

デフォルトの表示タブは`ページのURL?default-tab=html,css`のようにクエリを指定することで変更できます。



### SlideShare
```
@[slideshare](スライドのkey)
```
SlideShareの埋め込みiframeに含まれる`...embed_code/key/○○...`の`◯◯`の部分を入力します。


### SpeakerDeck
```
@[speakerdeck](スライドのID)
```
SpeakerDeckで取得した埋め込みコードに含まれる`data-id`の値を入力します。

### JSFiddle

```
@[jsfiddle](ページのURL)
```

### CodeSandbox

```
@[codesandbox](embed用のURL)
```

CodeSandboxでは、各ページから埋め込み用の`<iframe>`を取得できます。この`<iframe>`に含まれる`src`のURLを括弧の中に入力します。

### StackBlitz

```
@[stackblitz](embed用のURL)
```

StackBlitzでは、各ページから「Embed URL」を取得できます。取得したURLをそのまま括弧の中に入力します。

### オンラインエディターではモーダルから挿入可能

オンラインのエディターでは「+」ボタンを押すことで、外部コンテンツ埋め込み用のモーダルを表示できます。

![](https://storage.googleapis.com/zenn-user-upload/t87wf3d7xgfv7cabv4a9lfr1t79q)


