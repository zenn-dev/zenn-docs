---
title: "GitHubリポジトリでZennのコンテンツを管理する"
emoji: "😸"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---


Zennには[Web上のエディター](https://zenn.dev/zenn/articles/editor-guide)が用意されていますが、GitHubリポジトリと連携すればローカルのテキストエディターで執筆することもできます。

# GitHub連携時のイメージ

GitHubリポジトリと連携した場合、投稿コンテンツの作成や更新はすべてリポジトリ内で行います。**登録したブランチに変更があると、zenn.devへ自動で同期（デプロイ）が行われます**。

:::details 同期するブランチの指定
GitHub連携が完了している場合、下記のページからブランチを変更できます。
[デプロイ設定 →](https://zenn.dev/dashboard/deploys?tab=repo_settings)
:::

### コンテンツの作成
ローカルのテキストエディターなどでmarkdownファイルを作成し、編集します。ファイルの作成やプレビューには[Zenn CLI](https://zenn.dev/zenn/articles/install-zenn-cli)を使用できます。

markdownファイルの編集後、リモートリポジトリ（GitHub）へプッシュします。登録したブランチへのプッシュやプルリクエストのマージによりデプロイが開始されます。



:::message
Zenn上にまだ存在しない名前のファイルが見つかると新しい投稿として作成されます。
:::

デプロイの進捗状況はヘッダーにアイコンで表示されます。

![ダッシュボードのデプロイ履歴](/images/articles/connect-to-github/header-deploy-status.gif =150x)






デプロイ履歴は[ダッシュボード](https://zenn.dev/dashboard/deploys)から確認できます。デプロイ時に発生したエラーもここでチェックします。



![ダッシュボードのデプロイ履歴](/images/articles/connect-to-github/deploy-history.png)*デプロイ履歴*



### 内容の更新
内容を変更するときは`.md`ファイルを編集し、再度プッシュします。変更が加えられた`.md`ファイルのみがzenn.devに同期されます。

### コンテンツの削除
安全のため、コンテンツの削除は[ダッシュボードの投稿管理](https://zenn.dev/dashboard)からのみ行うことができます。


![投稿管理ダッシュボード](/images/articles/connect-to-github/delete-deployed-article.png)



# GitHubとの連携手順
## 1. リポジトリを作成する
まずGitHubで好きな名前のリポジトリを作成します。公開設定はPublicでもPrivateでもOKです。この時点ではリポジトリの中身は空にしておきます。README.mdを作成する必要もありません。

![GitHubでリポジトリを作成](https://storage.googleapis.com/zenn-user-upload/t1og2ri6shz2qy501p2mmhre2a0x =600x)


## 2. Zennのダッシュボードから連携する

Zennにログインしたうえで、ダッシュボードの[GitHubからのデプロイ](https://zenn.dev/dashboard/deploys)を開きます。

![GitHub連携ページ](/images/articles/connect-to-github/connect-to-github.png)



［リポジトリを連携］を選ぶと、リポジトリを選択する画面が表示されます。

![GitHubでのリポジトリの選択](https://storage.googleapis.com/zenn-user-upload/vim7vyhvmubm2wchnovclp6b5hgg)


このとき必ず「Only select repositories」にチェックを入れて、**連携するリポジトリだけを選ぶ**ようにしてください。

:::message
連携できるリポジトリは最大2つです。3つ以上選択されていると連携が失敗します。これは安全のための意図的な仕様です。
:::

これで連携は完了です。

## 3. 同期するブランチ名を確認
[リポジトリ設定タブ](https://zenn.dev/dashboard/deploys?tab=repo_settings)で同期したいブランチ名を確認・変更します。

![リポジトリの設定](/images/articles/connect-to-github/repo-settings.png =480x)


ここで登録されている名前のブランチに変更があったときに自動でデプロイが行われます。


## ファイルの作成やプレビューはCLIで
ローカルでのファイルの作成や、markdownのプレビューにはZenn CLIを使います。具体的な使い方は下記のページをご覧ください。

📘 **[Zenn CLIの導入手順 →](https://zenn.dev/zenn/articles/install-zenn-cli)**



# GitHubリポジトリ連携についてのFAQ

## 連携するリポジトリを変更したい

[ダッシュボード](https://zenn.dev/dashboard/deploys)で連携を解除した後に、再度連携を行なってください。連携を解除しても同期されているデータはそのまま残ります。

連携するリポジトリを追加したい場合も一度連携を解除してから再連携を行っていただくようお願いします。


## リポジトリにプッシュしてもデプロイされない

[ダッシュボード](https://zenn.dev/dashboard/deploys)からデプロイ履歴を確認してください。

プッシュされた内容に問題がある場合は、エラーメッセージが表示されます。

もしデプロイ履歴にログが出ていない場合は、GitHubの[インストール済みのApplications](https://github.com/settings/installations)の一覧からZenn ConnectのConfigureを開き、ダッシュボードに表示されている連携リポジトリとApplicationがアクセスを許可しているリポジトリが一致することを確認してください。

**▼ [リポジトリ設定](https://zenn.dev/dashboard/deploys?tab=repo_settings)に表示されているリポジトリ**

![リポジトリの設定](/images/articles/connect-to-github/repo-settings.png =480x)

**▼ Applicationがアクセスを許可しているリポジトリ**

![Applicationがアクセスを許可しているリポジトリ](https://storage.googleapis.com/zenn-user-upload/g08tioqppyzdhkazpic50df5iai6 =500x)

一致していない場合はデプロイされませんので、Application側のリポジトリを変更してください。また、連携するリポジトリを変更したい場合は、zennのダッシュボードから一度連携を解除してから再度連携を行ってください。


## 複数リポジトリ連携時に同じ記事を別リポジトリに移行することはできる？

[slug](https://zenn.dev/zenn/articles/what-is-slug)が一致していればどちらのリポジトリから同期されても同じように上書きされます。そのため、記事や本のファイルを別のリポジトリに移動するだけで移行は完了します。
