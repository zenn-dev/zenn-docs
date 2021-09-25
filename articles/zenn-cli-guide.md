---
title: "Zenn CLIで記事・本を管理する方法"
emoji: "🔨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

このページでは Zenn CLI の使い方とコマンドの一覧を紹介します。まだインストールしていない方は下記のリンク先をご覧ください。

📘 **[Zenn CLI を導入する →](https://zenn.dev/zenn/articles/install-zenn-cli)**

# CLI で記事（article）を管理する

## ファイルの配置ルール

1 つの記事の内容は、1 つのmarkdownファイル（`◯◯.md`）で管理します。ファイルは`articles`という名前のディレクトリ内に含める必要があります。

```
.
└─ articles
   ├── example-article1.md
   └── example-article2.md
```

具体的な例として[Zenn のドキュメント用リポジトリ](https://github.com/zenn-dev/zenn-docs)を見ると分かりやすいかもしれません。

## 記事の作成

:::message
まだ`articles`ディレクトリが存在しない場合は、事前に`npx zenn init`を実行してください（参考：[zenn-cli のセットアップ](https://zenn.dev/zenn/articles/install-zenn-cli#2.-zenn%E7%94%A8%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97%E3%82%92%E8%A1%8C%E3%81%86)）
:::

以下のコマンドによりmarkdownファイルを簡単に作成できます。

```shell
$ npx zenn new:article
```

`articles/ランダムなslug.md`というファイルが作成されます。slug（スラッグ）はその記事のユニークな ID のようなものです。詳しくは「[Zenn の slug とは](https://zenn.dev/zenn/articles/what-is-slug)」をご覧ください。

作成されたファイルの中身は次のようになっています。

```yaml
---
title: "" # 記事のタイトル
emoji: "😸" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: [] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---
ここから本文を書く
```

👆 ファイルの上部には`---`に挟まれる形で記事の設定（Front Matter）が含まれています。ここに記事のタイトル（title）やトピックス（topics）などを**yaml 形式**で指定することになります。

コマンド実行時に記事の Front Matter をオプションで指定することもできます。

```shell
$ npx zenn new:article --slug 記事のスラッグ --title タイトル --type idea --emoji ✨
```

:::message
slug は`a-z0-9`、ハイフン`-`、アンダースコア`_`の 12〜50 字の組み合わせにする必要があります
:::

:::details 本文に画像を挿入するには
GitHub連携時に本文に画像を挿入したい場合、下記リンク先の方法でリポジトリ内に画像を配置するか、[画像のアップロードページ](https://zenn.dev/dashboard/uploader)をご利用ください。

https://zenn.dev/zenn/articles/deploy-github-images
:::

## プレビューする

本文の執筆は、ブラウザでプレビューしながら確認できます。ブラウザでプレビューするためには次のコマンドを実行します。

```shell
$ npx zenn preview # プレビュー開始
```

![](https://storage.googleapis.com/zenn-user-upload/jix99kz8oao4czphw2ogxm5sup9s)

👆 このように各記事をプレビューをしながら執筆できます。

:::message
デフォルトでは`localhost:8000`で立ち上がりますが`npx zenn preview --port 3000`というようにポート番号の指定もできます。
:::

## 記事を公開する

記事を zenn.dev 上で公開するには`published`オプションが`true`になっていることを確認したうえで、ファイルをコミットし、Zenn と連携されている GitHub リポジトリにプッシュします。
Zenn と連携したリポジトリの登録ブランチにプッシュされると、同期（デプロイ）が開始されます。

:::message
デプロイ履歴は[ダッシュボード](https://zenn.dev/dashboard/deploys)から見ることができます。デプロイ時にエラーが発生している場合もここから見る必要があります。
:::

なおコミットメッセージに`[ci skip]`もしくは`[skip ci]`が含まれていると Zenn でのデプロイがスキップされます。

## 記事の更新

記事の更新を行う場合も、markdownファイルを編集し、GitHub リポジトリへプッシュするだけで OK です。このとき slug が同一のものでないと別の記事として作成されてしまうので注意しましょう。

:::message alert
リポジトリの変更が zenn.dev に反映されるまでにしばらく時間がかかります。[ダッシュボード](https://zenn.dev/dashboard/deploys)からデプロイのステータスをご確認ください。

また、未ログイン状態ではしばらくキャッシュされた古い内容が表示される可能性があります。時間を置いた後にリロードしてご確認ください。
:::

## 記事の削除

削除は[ダッシュボード](https://zenn.dev/dashboard)から行います。安全のため、`articles`ディレクトリからmarkdownファイルを削除しても zenn.dev 上では削除はされません。

---

# CLI で本（book）を管理する

Zenn の本は複数のチャプターで構成されます。

## 本のディレクトリ構成

:::message
まだ`books`ディレクトリが存在しない場合は、事前に`npx zenn init`を実行してください（参考：[zenn-cli のセットアップ](https://zenn.dev/zenn/articles/install-zenn-cli#2.-zenn%E7%94%A8%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97%E3%82%92%E8%A1%8C%E3%81%86)）
:::

GitHub リポジトリで本のデータを管理する場合は、次のようなディレクトリ構成にします。

```shell
.
├─ articles
└─ books
   └── 本のスラッグ
       ├── config.yaml # 本の設定
       ├── cover.png　# カバー画像（JPEGかPNG）
       └── チャプターのスラッグ.md # 各チャプター
```

具体的には、以下のようになります。

```shell
# 具体的な例
books
└── my-awesome-book
    ├── config.yaml
    ├── cover.png
    ├── example1.md
    ├── example2.md
    └── example3.md
```

👆`example1.md`や`example2.md`は各チャプターファイルの例です（のちほど詳しく説明します）。

これが 1 冊の本のファイル構成です。複数の本を作成するためには、同様の構成のディレクトリを複数`books`内に作ることになります。

:::message
実際の例として[Zenn のドキュメント用リポジトリ](https://github.com/zenn-dev/zenn-docs)が参考になるかもしれません。
:::

## 本の各ファイルの役割

### 📄 config.yaml

本の設定ファイルです。以下のように記入してください。

```yaml
title: "本のタイトル"
summary: "本の紹介文"
topics: ["markdown", "zenn", "react"] # トピック（5つまで）
published: true # falseだと下書き
price: 0 # 有料の場合200〜5000
chapters:
  - example1 # チャプター1
  - example2 # チャプター2
  - example3 # チャプター3
```

- **`title`** : 本のタイトルを入力します
- **`summary`** : 本の紹介文を入力します。これは有料の本であっても公開されます
- **`topics`** : トピック（タグ）を 5 つまで指定します
- **`published`** : 公開する場合は`true`にします
- **`price`** : たとえば本を 1000 円で販売するときは`price: 1000`と記載します（200〜5000 の間で 100 円単位で設定する必要があります）
- **`chapters`** : チャプターの並び順を配列で指定します（入れ子には未対応）。ここに指定されなかったチャプターは zenn.dev に同期されません
- **`toc_depth`** : 以下の説明をご覧ください

#### 🚀 目次の表示設定

2020/10/26 から、チャプターごとの目次を表示できるようになりました。デフォルトでは「h1」と「h2」見出しまで目次に表示されます。

`config.yaml`で`toc_depth: 0`と記載すると各チャプターの目次を非表示にできます。`toc_depth: 1`とすると「h1」見出しだけが目次に表示されます。この値は`0`〜`3`の範囲で指定する必要があります。

※ この値は本全体での設定になります。チャプターごとに別の設定をすることはできません。

### 🖼️ カバー画像

本のカバー画像（表紙）は`cover.png`もしくは`cover.jpeg`というファイル名で配置します。
推奨の画像サイズは**幅 500px・高さ 700px**です。他のサイズにした場合も最終的にこのサイズにリサイズされます。

### 📄 各チャプターのファイル（`◯◯.md`）

各チャプターのファイル名は「`a-z0-9`、ハイフン`-`、アンダースコア`_`の 1〜50 字の組み合わせ」+ `.md`とします。この文字列は URL の一部となります。例えば`about.md`のチャプターの URL は`/ユーザー名/本のスラッグ/viewer/about`となります。

各チャプターのmarkdownファイルには Front Matter でタイトルを指定し、その下に本文を書いていきます。

```yaml
---
title: "チャプターのタイトル"
---
ここからチャプター本文
```

:::details 本文に画像を挿入するには
GitHub連携時に本文に画像を挿入したい場合、下記リンク先の方法でリポジトリ内に画像を配置するか、[画像のアップロードページ](https://zenn.dev/dashboard/uploader)をご利用ください。

https://zenn.dev/zenn/articles/deploy-github-images
:::


有料の本で一部のチャプターを無料公開する場合は`free: true`を指定してください。本の価格が ¥0（無料）のときはこの設定は無視されます。

```yaml
---
title: "タイトル"
free: true
---

```

### 具体的な例

たとえば、次の 4 つのチャプターファイルを作ったとします。

- `abstract.md`
- `results.md`
- `introduction.md`
- `conclusion.md`

表示順は`config.yaml`で指定します。

```yaml
# config.yaml
...省略...
chapters:
  - introduction
  - results
  - conclusion
```

👆 zenn.dev 上では`chapters`に配列で指定された順番にチャプターが並ぶことになります。この例の場合「introduction → results → conclusion」の順に並びます。`abstract.md`は指定されていないため同期されません。

#### ファイル名（チャプター番号.slug.md）で並び順を管理することも

`config.yaml`でチャプターの並び順を指定すると、ディレクトリ内が煩雑になってしまうという場合には、ファイル名で並び順を制御することもできます。

::::details 詳しく読む

ファイル名を`チャプター番号.slug.md`という形にすると、その順番通りにチャプターが表示されます。

```shell
# 具体的な例
books
└── my-awesome-book
    ├── config.yaml
    ├── 1.intro.md
    ├── 2.foo.md
    └── 3.bar.md
```

この方法でデプロイを行う場合、`config.yaml`の`chapters`は空にしておく必要があります。

デプロイ時に以下のようなファイルの読み方をするためです。

- `config.yaml`で`chapters`が指定されている場合 => 指定通りに`slug.md`を読みにいく
- `config.yaml`で`chapters`が空の場合 => `番号.slug.md`を読みにいく

::: message alert
複数のチャプターで同じ slug を使うことはできません。例えば`2.summary.md`と`3.summary.md`という同一 slug のファイルがあった場合、どちらか片方しか反映されません。
:::

[関連する GitHub Issue →](https://github.com/zenn-dev/zenn-editor/issues/45)

::::

## 本の雛形をコマンドで作成する

本の構成は少し複雑ですが、下記のコマンドを使えば雛形を作成できます。

```shell
$ npx zenn new:book
# 本のslugを指定する場合は以下のようにします。
# npx zenn new:book --slug ここにスラッグ
```

あとは 1 つずつファイルを作成していけば OK です。

:::message
本の slug は`a-z0-9`、ハイフン`-`、アンダースコア`_`の 12〜50 字の組み合わせにする必要があります
:::

## 本と各チャプターをプレビューする

以下のコマンドにより、ブラウザ上でプレビューしながら執筆できます。

```shell
$ npx zenn preview
```

## 最大チャプター数

本のチャプターは1冊あたり最大100個まで作成できます。

## 本の更新

本の更新を行う場合も、ファイルを変更し、GitHub リポジトリへプッシュするだけで OK です。このとき slug（ディレクトリ名）が同一のものでないと別の本として作成されてしまうので注意しましょう。

:::message alert
リポジトリの変更が zenn.dev に反映されるまでにしばらく時間がかかります。[ダッシュボード](https://zenn.dev/dashboard/deploys)からデプロイのステータスをご確認ください。

また、未ログイン状態ではしばらくキャッシュされた古い内容が表示される可能性があります。時間を置いた後にリロードしてご確認ください。
:::

## 本の削除

削除は[ダッシュボード](https://zenn.dev/dashboard)から行います。`books`ディレクトリからファイルを削除しても zenn.dev 上では削除はされません。
