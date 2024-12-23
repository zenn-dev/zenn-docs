---
title: "PublicationにGitHubリポジトリを連携してZennのコンテンツを管理する"
emoji: "😼"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

[Publication Pro](https://zenn.dev/zenn/articles/publication-pro-features)では、PublicationそのものにGitHubリポジトリを連携することができます。メンバー全員の記事を1つのGitHubリポジトリで管理することにより、組織のポリシーに沿った統制やCIの整備が柔軟に行えるようになります。

Zennアカウントに対するGitHub連携機能のドキュメントもあわせてご覧ください。

https://zenn.dev/zenn/articles/connect-to-github

:::message
本記事では、Publicationに連携したGitHubリポジトリを**Publication連携リポジトリ**と呼称します。
また、Zennアカウントに連携したGitHubリポジトリを**アカウント連携リポジトリ**と呼称します。
:::

## GitHub連携の実施

[Publicationのダッシュボード](https://zenn.dev/dashboard/publications)よりGitHub連携が可能です。

![](/images/articles/publication-pro-features/publication-github-connect.png)

連携先のPublicationが正しいことをよくご確認いただき、連携を実施してください。

:::message
Publicationに連携可能なリポジトリは1つまでです。
:::

:::message
すでにGitHubアカウント/Organization配下のリポジトリにZennアカウントを連携している場合、さらに同じGitHubアカウント/OrganizationにPublicationを連携することはできません。これはGitHub Appsの仕様になります。

Zenn運営としては、あらかじめ組織のGitHub Organizationを用意し、以下のような形で連携することを推奨しています。

- Zenn個人アカウントに対して連携はGitHub個人アカウント配下のリポジトリを連携する
- Publicationに対してはOrganization配下のリポジトリを連携する
:::

## ディレクトリ構造

Publication連携リポジトリにおけるディレクトリは以下のように構成してください。

```tree
.
└── {username}
    ├── articles
    │   └── {slug}.md
    └── images
        └── {image_file}
```

例えば、メンバー2人の記事をPublication連携リポジトリで管理する場合、以下のようになります。

```tree
.
├── example_user1
│   ├── articles
│   │   └── publication-pro-features.md
│   └── images
│       ├── example.png
│       └── example.jpg
└── example_user2
    ├── articles
    │   └── how-to-use-publication.md
    └── images
        └── example.png
```

:::message
リポジトリのトップレベルにPublicationメンバーでないユーザー名のディレクトリを作成するとデプロイ時にエラーメッセージが表示されます。

`_` 以外の記号など、ユーザー名として使用できない文字列が含まれている場合はユーザー名としてみなされません。例えば、トップレベルに `/.github` `/.scripts` などのディレクトリを作成した場合は `.` が含まれているためエラーは発生しません。
:::

### 記事内における画像の貼り付け

記事において、 `{username}/images/` に配置した画像を貼り付ける場合は、ユーザー名ディレクトリ（`{username}/`）直下からの `/images` で始まるパスを指定します。

例えば、 `example_user1/images/example.png` を `example_user1/articles/publication-pro-features.md` 内で使用する場合、

```md
![](/images/example.png)
```

と記述します。

:::message
記事の配置場所と異なるユーザー名ディレクトリ下の画像ファイルを貼り付けることはできません。

例えば、`example_user2/images/example.png` を `example_user1/articles/publication-pro-features.md` 内で使用することはできません。
:::

## Publication連携リポジトリ以外からの投稿・更新の制限

設定により、Publication連携リポジトリ以外からの投稿・更新を禁止することができます。

リポジトリ設定（`https://zenn.dev/dashboard/publications/{publication_name}/deploys?tab=repo_settings`）より、「このリポジトリ以外からの投稿・更新を禁止する」を有効化することで、Publication連携リポジトリ以外からの記事投稿や更新が行えないようになります。

![](/images/articles/publication-pro-features/publication-github-repository-enforced.png)

組織のポリシーに応じて本設定をご検討ください。

## 記事をPublication連携リポジトリに移行する

記事をPublication連携リポジトリに移行する手順について紹介します。

移行実施前に、記事をPublicationに紐づける方法については次の記事をご確認ください。

https://zenn.dev/zenn/articles/how-to-use-publication

### Web上のエディターで作成した記事の移行

[Web上のエディター](https://zenn.dev/zenn/articles/editor-guide)で作成した記事をPublication連携リポジトリに管理を移行したい場合、以下の手順を実施します。

1. （設定が有効になっている場合）「このリポジトリ以外からの投稿・更新を禁止する」を一時的に無効化する
2. 移行したい記事が対象のPublicationに紐づいていることを確認（Publicationに紐づいていない場合は、Webエディター上の操作で紐づける）
3. 移行したい記事ファイル（と画像ファイル）を[slug](https://zenn.dev/zenn/articles/what-is-slug)が同一となるようにPublication連携リポジトリに作成する
4. Publication連携リポジトリにおいて記事デプロイを実施する
5. （1の手順で設定を無効にした場合）「このリポジトリ以外からの投稿・更新を禁止する」を再度有効化する

### アカウント連携リポジトリからの記事の移行

アカウント連携リポジトリからPublication連携リポジトリに記事の管理を移行したい場合、以下の手順を実施します。

1. （設定が有効になっている場合）「このリポジトリ以外からの投稿・更新を禁止する」を一時的に無効化する
2. 移行したい記事が対象のPublicationに紐づいていることを確認（Publicationに紐づいていない場合は、アカウント連携リポジトリ内の `publication_name` frontmatterを編集して紐づける）
3. 移行したい記事ファイル（と画像ファイル）をPublication連携リポジトリに移動する
4. Publication連携リポジトリにおいて記事デプロイを実施する
5. （1の手順で設定を無効にした場合）「このリポジトリ以外からの投稿・更新を禁止する」を再度有効化する

