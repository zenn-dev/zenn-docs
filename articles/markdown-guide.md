---
title: "ZennのMarkdown記法"
emoji: "👩‍💻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Markdown", "zenn"]
published: false
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


# テキストリンク
```
[アンカーテキスト](リンクのURL)
```
[アンカーテキスト](https://zenn.dev)
`Ctrl + K`のショートカットでも挿入できます。


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
`$a\ne0$`というよう`$`ひとつで挟むことで、インラインで数式を含めることができます。たとえば$a\ne0$のようなイメージです。

# 引用
```
> 引用文
> 引用文
```
> 引用文
> 引用文

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

# 外部コンテンツの埋め込み


### Twitter

```
@[tweet](ツイートページのURL)
```

「twitter」ではなく「tweet」であることにご注意ください。


### YouTube

```
@[youtube](動画のID)
```
URLに含まれる英数字の組み合わせを入力します。

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

### オンラインエディターではモーダルから挿入可能

オンラインのエディターでは「+」ボタンを押すことで、外部コンテンツ埋め込み用のモーダルを表示できます。

![](https://storage.googleapis.com/zenn-user-upload/t87wf3d7xgfv7cabv4a9lfr1t79q)



---

今後[CodeSandbox](https://codesandbox.io)などの埋め込みにも対応する予定です。