---
title: "GitHubリポジトリ連携時に投稿ページにGitHubへのリンクを表示する"
emoji: "🔗"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---


投稿データをGitHubリポジトリからデプロイした場合、表示ページに「GitHubで編集を提案」というリンクを表示できます。これにより読者に修正提案のプルリクエストを作成してもらいやすくなります。

次の画像は実際に表示されるリンクのイメージです。

**記事の本文下**
![](https://storage.googleapis.com/zenn-user-upload/uj9ddsewac5p8fb6w3fv60a49tjo =420x)

**本のチャプターの本文下**
![](https://storage.googleapis.com/zenn-user-upload/hxi4og4tdn0eeqm40jhvarwt6boa =560x)

## 表示のON/OFFを切り替える

表示の有無はダッシュボードの[リポジトリ設定](https://zenn.dev/dashboard/deploys?tab=repo_settings)からリポジトリごとに設定できます。なお、プライベートリポジトリではこのオプションを有効にすることはできません。

![](https://storage.googleapis.com/zenn-user-upload/ttpldbh2ftabxj4adfnmhaa1ek8m =420x)

## その他の表示リンクについて


このオプションが有効になっている場合、公開後に本文が更新された投稿にはコミット一覧ページへのリンクも表示されます。

**記事の更新日横**
![](https://storage.googleapis.com/zenn-user-upload/hjtn9osxhihkaqcpi056oulgo4qu =400x)

**本の更新日横**
![](https://storage.googleapis.com/zenn-user-upload/4mmttmg5tob5uqxslrv7a4nl5qna =300x)

