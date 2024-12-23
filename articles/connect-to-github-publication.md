---
title: "PublicationにGitHubリポジトリを連携してZennのコンテンツを管理する"
emoji: "😼"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

PublicationそのものにGitHubリポジトリを連携することができます。メンバー全員の記事を1つのGitHubリポジトリで管理することにより、組織の統制や統一されたCIの整備が柔軟に行えるようになります。

:::message
Zennアカウントに対するGitHub連携機能のドキュメントもあわせてご覧ください。

https://zenn.dev/zenn/articles/connect-to-github
:::

:::message
本記事では、Publicationに連携したGitHubリポジトリを**Publicationリポジトリ**と呼称します。
また、Zennアカウントに連携したGitHubリポジトリを**アカウントリポジトリ**と呼称します。
:::

## GitHub連携の実施

PublicationのダッシュボードよりGitHub連携が可能です（`https://zenn.dev/dashboard/publications/{publication_name}/deploys`）。

![](/images/articles/publication-pro-features/publication-github-connect.png)

連携先のPublicationが正しいことをよくご確認いただき、連携を実施してください。

:::message
Publicationに連携可能なリポジトリは1つまでです。
:::

:::message
連携するGitHubアカウント Organizationは分ける
:::

## ディレクトリ構造

Publicationリポジトリにおけるディレクトリは以下のように構成してください。

```tree
.
└── {username}
    ├── articles
    │   ├── {slug}.md
    └── images
        └── {image_file}
```

例えば、メンバー2人の記事をPublicationリポジトリで管理する場合、以下のようになります。

```tree
.
├── zenn
│   ├── articles
│   │   ├── publication-pro-features.md
│   └── images
│       ├── example.png
│       └── example.jpg
└── dyoshikawa
    ├── articles
    │   └── zenn-check-spam-by-llm.md
    └── images
        └── example.png
```

:::message
リポジトリのトップレベルにPublicationメンバーでないユーザー名のディレクトリを作成するとデプロイ時にエラーメッセージが表示されます。

`_` 以外の記号など、ユーザー名として使用できない文字列が含まれている場合はユーザー名としてみなされません。例えば、トップレベルに `/.github` `/.scripts` などのディレクトリを作成した場合は `.` が含まれているためエラーは発生しません。
:::

## Publicationリポジトリ以外からの投稿・更新の制限

設定により、Publicationリポジトリ以外からの投稿・更新を禁止することができます。

リポジトリ設定（`https://zenn.dev/dashboard/publications/{publication_name}/deploys?tab=repo_settings`）より、「このリポジトリ以外からの投稿・更新を禁止する」を有効化することで、Publicationリポジトリ以外からの記事投稿や更新が行えないようになります。

![](/images/articles/publication-pro-features/publication-github-repository-enforced.png)

組織のポリシーに応じて本設定をご検討ください。

## 記事をPublicationリポジトリに移行する

### Web上のエディターで作成した記事の移行

### アカウントリポジトリからの記事の移行
