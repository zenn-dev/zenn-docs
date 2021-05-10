---
title: "Zennで途中からGitHubリポジトリ連携をはじめるときの手順"
emoji: "🐙"
type: "idea"
topics: ["zenn"]
published: true
---

Zennでは投稿データをGitHubリポジトリで管理し、自動的に同期が行われるように設定できます。

:::message
リポジトリ同期には記事（article）と本（book）が対応しており、スクラップ（scrap）は対応していません。
:::


すでにブラウザからZennに記事や本を投稿しており、途中からGitHub連携をはじめる場合には、エクスポート機能を使うとスムーズに執筆環境を移行できます。コメントやLikeなどのメタデータもそのまま引き継がれます。

# 途中からGitHubリポジトリでの投稿データ管理をはじめるまでの手順


## 手順1: GitHubリポジトリ連携を行う

まだリポジトリの連携が完了していない場合は、こちらの記事の手順に従って連携を行ってください。

https://zenn.dev/zenn/articles/connect-to-github

## 手順2： 投稿データをエクスポートする
すでにZennに投稿済みのデータはエクスポート機能を用いてテキストファイルとしてダウンロードできます。

**[投稿データをエクスポート（要ログイン）](https://zenn.dev/settings/export)**

ダウンロードしたzipファイルを開くと、`articles`、`books`、`scraps`といったディレクトリが表示されます（投稿データが存在しないディレクトリは含まれません）。

## 手順3： 連携リポジトリのルートに`articles`、`books`ディレクトリを配置

このうち、`articles`と`books`を連携リポジトリのルートディレクトリにそのまま配置します。

![](https://storage.googleapis.com/zenn-user-upload/yu84oke4inu5l5prmrowrqtgvv9y)

`articles`と`books`内にはマークダウンファイルや本の設定ファイルなどが含まれており、これらのファイルはそのままzenn.devに同期（デプロイ）できる形式となっています。

## 手順4: 変更をコミットしGitHubへプッシュする
変更をコミットし、GitHubリポジトリのデプロイ対象ブランチ[^1]へとプッシュすると自動でデプロイが開始されます。既にZennで作成済みの投稿であっても、GitHubリポジトリ上で変更を行うことで内容が上書きされます。

:::message
上書きの対象かどうかは[スラッグ](https://zenn.dev/zenn/articles/what-is-slug)が同一かどうかにより決まります。
:::

[^1]: [ダッシュボードのデプロイ設定](https://zenn.dev/dashboard/deploys)から変更できます。