---
title: "Zenn本のチャプターファイルの作成方法が変わりました"
emoji: "🙏"
type: "idea"
topics: ["zenn"]
published: true
---

2020/10/10〜、GitHubリポジトリで本のチャプターを管理する方法が変わりました。新しい管理方法はこのページでも説明しますが、[CLIで本を管理する](https://zenn.dev/zenn/articles/zenn-cli-guide#cli%E3%81%A7%E6%9C%AC%EF%BC%88book%EF%BC%89%E3%82%92%E7%AE%A1%E7%90%86%E3%81%99%E3%82%8B)で確認することもできます。

:::message
Web上（zenn.dev上）で本を作成・編集している場合には影響はありません。
:::

# これまでの方法と問題点
GitHubリポジトリでコンテンツを管理している場合、本のチャプターファイルは以下のように作成する必要がありました。

```bash
books
└── my-awesome-book
    ├── 1.md # チャプター1
    ├── 2.md # チャプター2
    ├── 3.md # チャプター3
    └── 4.md # チャプター4
```

この方法だと、以下のような問題がありました。
- 後から「チャプター2と3の間に新しいチャプターを差し込みたくなった」ような場合、1つずつファイル名を書き直さなければならない
- チャプター番号がずれるとビューアー上でのリンクが維持されない
- ファイル名からチャプターの内容を推測できない


# 新しい方法
問題を解消するため、以下のような構成へ変更を行いました。

```bash
books
└── my-awesome-book
    ├── config.yaml # ここでチャプターの並び順を指定
    ├── about.md # チャプター
    ├── conclusion.md # チャプター
    ├── create-book.md # チャプター
    └── update-book.md # チャプター
```

👆 各チャプターのファイル名には好きな文字列（`a-z0-9`、ハイフン`-`、アンダースコア`_`の1〜50字の組み合わせ）を使い、チャプターの並び順は`config.yaml`で指定します。

### config.yamlでチャプターの並び順を指定
```yaml
title: "本のタイトル"
summary: "本の紹介文"
topics: ["markdown", "zenn"]
published: true
price: 0
# 👇 ここでチャプターの並び順を指定する
chapters:
  - about
  - create-book
  - update-book
  - conclusion
```

👆 デプロイされた本では`chapters`に配列で指定された順番にチャプターが並ぶことになります。この例の場合「`about` → `create-book` → `update-book` → `conclusion`」の順に並びます。なお、config.yamlの`chapters`に指定されなかったチャプターはzenn.devに同期されません。


:::message
現時点ではチャプターを入れ子にする（子チャプターを作る）ことはできません
:::

### チャプターのファイル名はURLの一部に
チャプターのファイル名はURLの一部となります。例えば`about.md`のチャプターのURLは`/ユーザー名/本のスラッグ/viewer/about`となります。


### 🚩 configで指定されなかったチャプターは削除されることに注意
すでに`about`、`create-book`、`update-book`、`conclusion`という4つのチャプターを持つ本がzenn.devに同期されているとします。この後、config.yamlにて、以下のように指定したうえでデプロイした場合…
```yaml
chapters:
  - about
  - conclusion
```
指定されなかった既存のチャプター（`create-book`と`update-book`）はzenn.dev上からは削除されることにご注意ください。

# すでに同期済みの本の対応について
~~すでにzenn.devに同期されている本については、以前の方法を継続して使用することができます。~~
~~ただし、以前の方法は非推奨とされ、しばらく期間が経った後に廃止される可能性があります。~~
~~（その場合、本の内容を修正するためには、新しい方法への移行を行う必要があります）~~

:::message alert
2021-08-25に、以前の方法のサポートは終了しました。
:::

## 以前の方法から移行する方法

### 手順0: CLIを最新版にする
プロジェクトのルートディレクトリで下記のコマンドを実行してください。
```
$ npm install zenn-cli@latest
```


現在のディレクトリ内のファイルが以下のようになっているとします。
```bash
books
└── my-awesome-book
    ├── 1.md
    ├── 2.md
    ├── 3.md
    └── 4.md
```

### 手順1：ファイル名の書き換え
まず、各チャプターのファイル名を「`a-z0-9`、ハイフン`-`、アンダースコア`_`の1〜50字の組み合わせ」に変更します。この文字列はURLに使われるため、チャプターの内容を表すものにすることをおすすめします。
```bash
books
└── my-awesome-book
    ├── introduction.md # チャプター1
    ├── getting-started.md # チャプター2
    ├── development.md # チャプター3
    └── deployment.md # チャプター4
```


### 手順2：config.yamlにチャプターの並び順を指定
そのうえで、`config.yaml`にチャプターの並び順を指定します。

```yaml
...省略...
# 👇 下記を追加
chapters:
  - introduction
  - getting-started
  - development
  - deployment
```

### 手順3：デプロイ
この状態でリポジトリへプッシュすれば移行完了です。（各チャプターのURLは変更されます）

---

ご迷惑をおかけして申し訳ありませんが、ご協力よろしくお願いします。
