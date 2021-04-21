---
title: "GitHubリポジトリ連携時に投稿ページにGitHubへのリンクを表示する"
emoji: "🔗"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---


投稿データをGitHubリポジトリからデプロイした場合、表示ページに「GitHubで編集を提案」というリンクを表示できます。これにより読者に修正提案のプルリクエストを作成してもらいやすくなります。

次の画像は記事本文下に表示されるリンクのイメージです。

![](https://storage.googleapis.com/zenn-user-upload/uj9ddsewac5p8fb6w3fv60a49tjo =420x)

### 表示のON/OFFを切り替える

表示の有無はダッシュボードの[デプロイ](https://zenn.dev/dashboard/deploys)にてリポジトリごとに設定できます。なお、プライベートリポジトリではこのオプションを有効にすることはできません。

![](https://storage.googleapis.com/zenn-user-upload/ttpldbh2ftabxj4adfnmhaa1ek8m =420x)

### その他の表示リンクについて


このオプションが有効になっている場合、公開後に本文が更新された記事にはコミット一覧ページへのリンクも表示されます。


![](https://storage.googleapis.com/zenn-user-upload/hjtn9osxhihkaqcpi056oulgo4qu =400x)


2021/04/21時点では記事（article）のみ対応していますが、近日中に本（book）でもリンクが表示されるようにアップデートを行う予定です。