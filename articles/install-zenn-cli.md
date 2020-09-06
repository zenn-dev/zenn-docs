---
title: "Zenn CLIをインストールする"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---



# Zenn CLIとは

ZennとGitHubリポジトリを連携すると、ローカルの好きなエディターで投稿コンテンツの作成・編集ができるようになります。

📘 **[ZennとGitHubリポジトリを連携する →](/zenn/articles/connect-to-github)**

ローカルでの執筆時には、スムーズに**マークダウンファイルの作成**したり、コンテンツを**プレビュー**したりするために「Zenn CLI」を導入しましょう。

:::message
Zenn CLIのソースコードは[GitHubに公開](https://github.com/zenn-dev/zenn-editor)されています
:::

# Zenn CLIの導入手順

## 0. 事前準備
- あらかじめ[ZennとGitHubリポジトリとの連携](/zenn/articles/connect-to-github)を行っておくことをおすすめします。
- Zenn CLIはNode.js製です。Node.jsをはじめて使う場合は[インストール](https://nodejs.org/ja/)する必要があります。

## 1. CLIをインストールする
Zennのコンテンツを管理したいディレクトリで、以下のコマンドを実行します。

```shell
$ npm init --yes # プロジェクトをデフォルト設定で初期化
$ npm install zenn-cli # zenn-cliを導入
```

これでディレクトリにCLIがインストールされます。


## 2. Zenn用のセットアップを行う

続いて以下の`npx`コマンドを実行します。

```shell
$ npx zenn init
```


`README.md`や`.gitignore`のほか、`articles`と`books`というディレクトリが作成されているはずです。この中にマークダウンファイル（`◯◯.md`）を入れていくことになります。

## 3. 導入完了🎉
これでZenn CLIの導入は完了です。以下のコマンドを実行することでブラウザでプレビューが開きます。

```shell
$ npx zenn preview
# 👀 Preview on http://localhost:8000
```

![](https://storage.googleapis.com/zenn-user-upload/51h36ls52d5gvl5wja9pk15kq3cv)

:::details 別のポート番号を指定する
`npx zenn preview --port 3333`のようにポート番号を指定することもできます。
:::


# CLIをアップデートする

Zenn CLIの表示がzenn.devと異なるときやCLI利用時に更新通知が表示されたときは下記のコマンドでアップデートを行ってください。

```shell
$ npm install zenn-cli@latest
```


# コンテンツを作成・編集する
具体的な執筆方法は下記のページをご覧ください。

📝 **[Zenn CLIの使い方 →](/zenn/articles/zenn-cli-guide)**

