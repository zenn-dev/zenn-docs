---
title: "投稿ページにGitHubリポジトリへのリンクを表示するには"
emoji: "🔗"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

## 概要

記事や本などの投稿データをGitHubリポジトリからデプロイした場合、表示ページに **「GitHubで編集を提案」** というリンクを表示できます。これにより読者に修正提案のプルリクエストを作成してもらいやすくなります。

次の画像は、実際に表示されるリンクのイメージです。

**記事の本文下**
![](https://storage.googleapis.com/zenn-user-upload/uj9ddsewac5p8fb6w3fv60a49tjo)

**本のチャプターの本文下**
![](https://storage.googleapis.com/zenn-user-upload/hxi4og4tdn0eeqm40jhvarwt6boa)

## 表示のON/OFFを切り替える

表示の有無はダッシュボードの[リポジトリ設定](https://zenn.dev/dashboard/deploys?tab=repo_settings)からリポジトリごとに設定できます。なお、プライベートリポジトリではこのオプションを有効にすることはできません。

![](/images/articles/show-github-link/show-link-setting.png)

:::message
連携したGitHubリポジトリの公開設定を `public` から `private` に変更した場合、この設定は**自動的に変更されません**。リンクを非表示にするには、手動で「表示しない」に変更してください。（issue: [#467](https://github.com/zenn-dev/zenn-community/issues/467)）
:::

## その他の表示リンクについて


このオプションが有効になっている場合、公開後に本文が更新された投稿にはコミット一覧ページへのリンクも表示されます。

**記事の更新日横**
![](/images/articles/show-github-link/article-commit-link.png)

**本の更新日横**
![](/images/articles/show-github-link/book-commit-link.png)

