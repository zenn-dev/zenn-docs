---
title: "Zenn CLIをインストールする"
emoji: "💻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

# Zenn CLIとは

ZennとGitHubリポジトリを連携すると、ローカルの好きなエディターで投稿コンテンツの作成・編集ができるようになります。

📘 **[ZennとGitHubリポジトリを連携する →](https://zenn.dev/zenn/articles/connect-to-github)**

ローカルでの執筆時には、スムーズに**markdownファイルの作成**したり、コンテンツを**プレビュー**したりするために「Zenn CLI」を導入しましょう。

:::message
Zenn CLIのソースコードは[GitHubに公開](https://github.com/zenn-dev/zenn-editor)されています
:::

# Zenn CLIの導入手順

## 1. 事前準備
- あらかじめ[ZennとGitHubリポジトリとの連携](https://zenn.dev/zenn/articles/connect-to-github)を行っておくことをおすすめします。
- Zenn CLIを使うにはNode.js 14以上が必要です。Node.jsをはじめて使う場合は[インストール](https://nodejs.org/ja/)する必要があります。


## 2. CLIをインストールする
Zennのコンテンツを管理したいディレクトリで、以下のコマンドを実行します。

```shell
$ npm init --yes # プロジェクトをデフォルト設定で初期化
$ npm install zenn-cli # zenn-cliを導入
```

これでディレクトリにCLIがインストールされます。

## 3. Zenn用のセットアップを行う

続いて以下の`npx`コマンドを実行します。

```shell
$ npx zenn init
```

`README.md`や`.gitignore`のほか、`articles`と`books`という名前のディレクトリが作成されます。この中にmarkdownファイル（`◯◯.md`）を入れていくことになります。

これでZenn CLIの導入は完了です🎉

# CLIをアップデートする

Zenn CLIの表示がzenn.devと異なるときやCLI利用時に更新通知が表示されたときは下記のコマンドでアップデートを行ってください。

```shell
$ npm install zenn-cli@latest
```

# コンテンツを作成・編集する
具体的な執筆方法は下記のページをご覧ください。

📘 **[Zenn CLIの使い方 →](https://zenn.dev/zenn/articles/zenn-cli-guide)**
