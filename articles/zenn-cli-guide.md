---
title: "Zenn CLIで記事・本を管理する方法"
emoji: "🔨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---


このページではZenn CLIの使い方とコマンドの一覧を紹介します。まだインストールしていない方は下記のリンク先をご覧ください。

📘 **[Zenn CLIを導入する →](https://zenn.dev/zenn/articles/install-zenn-cli)**


# CLIで記事（article）を管理する

## ファイルの配置ルール
1つの記事の内容は、1つのマークダウンファイル（`◯◯.md`）で管理します。ファイルは`articles`という名前のディレクトリ内に含める必要があります。

```
.
└─ articles
   ├── example-article1.md
   └── example-article2.md
```

具体的な例として[Zennのドキュメント用リポジトリ](https://github.com/zenn-dev/zenn-docs
)を見ると分かりやすいかもしれません。

## 記事の作成
以下のコマンドによりマークダウンファイルを簡単に作成できます。

```shell
$ npx zenn new:article
```

`articles/ランダムなslug.md`というファイルが作成されます。slug（スラッグ）はその記事のユニークなIDのようなものです。詳しくは「[Zennのslugとは](https://zenn.dev/zenn/articles/what-is-slug)」をご覧ください。


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

👆 ファイルの上部には`---`に挟まれる形で記事の設定（Front Matter）が含まれています。ここに記事のタイトル（title）やトピックス（topics）などを**yaml形式**で指定することになります。

コマンド実行時に記事のFront Matterをオプションで指定することもできます。

```shell
$ npx zenn new:article --slug 記事のスラッグ --title タイトル --type idea --emoji ✨ 
```

:::message
slugは`a-z0-9`とハイフン`-`の12〜50字の組み合わせにする必要があります
:::

:::details 本文に画像を挿入するには
GitHub連携時に本文で画像を使う際は[画像のアップロードページ](/dashboard/uploader)をご利用ください。
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
記事をzenn.dev上で公開するには`published`オプションが`true`になっていることを確認したうえで、ファイルをコミットし、Zennと連携されているGitHubリポジトリにプッシュします。
Zennと連携したリポジトリの登録ブランチにプッシュされると、同期（デプロイ）が開始されます。

:::message
デプロイ履歴は[ダッシュボード](/dashboard/deploys)から見ることができます。デプロイ時にエラーが発生している場合もここから見る必要があります。
:::

## 記事の更新
記事の更新を行う場合も、マークダウンファイルを編集し、GitHubリポジトリへプッシュするだけでOKです。このときslugが同一のものでないと別の記事として作成されてしまうので注意しましょう。

:::message alert
リポジトリの変更がzenn.devに反映されるまでにしばらく時間がかかります。[ダッシュボード](/dashboard/deploys)からデプロイのステータスをご確認ください。

また、未ログイン状態ではしばらくキャッシュされた古い内容が表示される可能性があります。時間を置いた後にリロードしてご確認ください。
:::

## 記事の削除
削除は[ダッシュボード](/dashboard)から行います。安全のため、`articles`ディレクトリからマークダウンファイルを削除してもzenn.dev上では削除はされません。

----

# CLIで本（book）を管理する

:::message alert
2020/10/10〜チャプターファイルの管理方法が変わりました。`npm install zenn-cli@latest`を実行してCLIが最新版になっていることをご確認ください。

[🐱 以前の方法](https://github.com/zenn-dev/zenn-docs/blob/9c433b5a4ec6cb7ec60bb36a54cf92eee7078ca6/articles/zenn-cli-guide.md#%E6%9C%AC%E3%81%AE%E5%90%84%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E5%BD%B9%E5%89%B2) / [🦁 以前の方法から新しい方法へ移行する](https://zenn.dev/zenn/articles/deprecated-book-deployment)
:::


Zennの本は複数のチャプターで構成されます。

## 本のディレクトリ構成

GitHubリポジトリで本のデータを管理する場合は、次のようなディレクトリ構成にします。

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

これが1冊の本のファイル構成です。複数の本を作成するためには、同様の構成のディレクトリを複数`books`内に作ることになります。

:::message
実際の例として[Zennのドキュメント用リポジトリ](https://github.com/zenn-dev/zenn-docs)が参考になるかもしれません。
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
- **`topics`** : トピック（タグ）を5つまで指定します
- **`published`** : 公開する場合は`true`にします
- **`price`** : たとえば本を1000円で販売するときは`price: 1000`と記載します（200〜5000の間で100円単位で設定する必要があります）
- **`chapters`** : チャプターの並び順を配列で指定します（入れ子には未対応）。ここに指定されなかったチャプターはzenn.devに同期されません
- **`toc_depth`** : 以下の説明をご覧ください


#### 🚀 目次の表示設定
2020/10/26から、チャプターごとの目次を表示できるようになりました。デフォルトでは「h1」と「h2」見出しまで目次に表示されます。

`config.yaml`で`toc_depth: 0`と記載すると各チャプターの目次を非表示にできます。`toc_depth: 1`とすると「h1」見出しだけが目次に表示されます。この値は`0`〜`3`の範囲で指定する必要があります。

※ この値は本全体での設定になります。チャプターごとに別の設定をすることはできません。


### 🖼️ カバー画像
本のカバー画像（表紙）は`cover.png`もしくは`cover.jpeg`というファイル名で配置します。
推奨の画像サイズは**幅500px・高さ700px**です。他のサイズにした場合も最終的にこのサイズにリサイズされます。

### 📄 各チャプターのファイル（`◯◯.md`）
各チャプターのファイル名は「`a-z0-9`と`-`の1〜50字の組み合わせ」+ `.md`とします。この文字列はURLの一部となります。例えば`about.md`のチャプターのURLは`/ユーザー名/本のスラッグ/viewer/about`となります。

各チャプターのマークダウンファイルにはFront Matterでタイトルを指定し、その下に本文を書いていきます。

```yaml
---
title: "チャプターのタイトル"
---

ここからチャプター本文
```

:::details 本文に画像を挿入するには
GitHub連携時に本文で画像を使う際は[画像のアップロードページ](/dashboard/uploader)をご利用ください。
:::

有料の本でチャプターを無料公開する場合は`free: true`を指定してください。 



```yaml
---
title: "タイトル"
free: true
---
```

### 具体的な例
たとえば、次の4つのチャプターファイルを作ったとします。

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
👆 zenn.dev上では`chapters`に配列で指定された順番にチャプターが並ぶことになります。この例の場合「introduction → results → conclusion」の順に並びます。`abstract.md`は指定されていないため同期されません。

## 本の雛形をコマンドで作成する

本の構成は少し複雑ですが、下記のコマンドを使えば雛形を作成できます。

```shell
$ npx zenn new:book
# 本のslugを指定する場合は以下のようにします。
# npx zenn new:book --slug ここにスラッグ
```

あとは1つずつファイルを作成していけばOKです。

:::message
本のslugは`a-z0-9`とハイフン`-`の12〜50字の組み合わせにする必要があります
:::

## 本と各チャプターをプレビューする

以下のコマンドにより、ブラウザ上でプレビューしながら執筆できます。

```shell
$ npx zenn preview
```

## 本の更新
本の更新を行う場合も、ファイルを変更し、GitHubリポジトリへプッシュするだけでOKです。このときslug（ディレクトリ名）が同一のものでないと別の本として作成されてしまうので注意しましょう。

:::message alert
リポジトリの変更がzenn.devに反映されるまでにしばらく時間がかかります。[ダッシュボード](/dashboard/deploys)からデプロイのステータスをご確認ください。

また、未ログイン状態ではしばらくキャッシュされた古い内容が表示される可能性があります。時間を置いた後にリロードしてご確認ください。
:::


## 本の削除
削除は[ダッシュボード](/dashboard)から行います。`books`ディレクトリからファイルを削除してもzenn.dev上では削除はされません。


