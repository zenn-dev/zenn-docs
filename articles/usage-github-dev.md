---
title: "Zennのコンテンツをgithub.devで編集する"
emoji: "🧑‍🚀"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: 
  - zenn
  - github  
published: true
---

:::message
現在(2022/11/08)、公開されているVSCode拡張は β 版です
:::

Zenn のコンテンツ( 記事・本 )を GitHub 連携している場合、[github.dev](https://github.dev) と [Zenn VSCode拡張](https://marketplace.visualstudio.com/items?itemName=zenn.zenn-preview)を使うことで、ブラウザ上でコンテンツ( 記事・本 )を編集することができます。

# github.dev の開き方

Zenn と連携しているリポジトリページを開き、`github.com` を `github.dev` へ変更すると、開いているリポジトリが [web-based editor](https://docs.github.com/ja/codespaces/the-githubdev-web-based-editor) で開かれます。( `.` キーを押すことでも可能です )

![](/images/articles/usage-github-dev/github-dev-ss.png)
*[zenn-dev/zenn-docs](https://github.com/zenn-dev/zenn-docs)をgithub.devで開いた画面*

# VSCode 拡張のインストール

Zenn のコンテンツ( 記事・本 )を [github.dev](https://github.dev) で表示するには、[VSCode 拡張]() をインストールする必要があります。

サイドバーの拡張機能タブを開き、Marketplace で「 Zenn 」を検索して、拡張をインストールします。

![](/images/articles/usage-github-dev/searched-zenn.png)
*拡張機能のサイドパネルからZennを検索*

インストールが完了すると、アクティブバーに Zenn のロゴが追加されます。

![](/images/articles/usage-github-dev/installed-zenn.png)

Zenn のロゴをクリックすると、サイドパネルにリポジトリ内の Zenn のコンテンツが一覧として表示されます。

![](/images/articles/usage-github-dev/zenn-preview-sidebar.png)
*サイドバーにZennのコンテンツが一覧表示されている様子*


# 拡張の使い方

詳しい拡張の使い方については、GitHubリポジトリ内の README.md または、VSCode の拡張ページを参照してください。

**GitHubリポジトリ**

https://github.com/zenn-dev/zenn-vscode-extension

**VSCode 拡張ページ**

https://marketplace.visualstudio.com/items?itemName=zenn.zenn-preview


# github.dev 上での Git 操作について

以下のサイトよりご確認ください。

https://docs.github.com/ja/codespaces/the-githubdev-web-based-editor#using-source-control