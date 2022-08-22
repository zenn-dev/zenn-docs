---
title: "Publicationの使い方"
emoji: "🪐"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

:::message
2022/08/22 現在、Publication機能はベータ版として提供しており、今後仕様が変わる可能性があります。
:::

## Publicationとは

Publicationとは、個人または組織が、一貫性のあるテーマについての記事をまとめて投稿することができる機能です。例えば以下のような使い方を想定しています。

- 会社のTech Blogとして、自社サービスの開発に関連した記事を複数人で投稿したい
- 個人やグループで1つのテーマに対して継続的に記事を投稿し、まとまりを作りたい

→ [詳しくはこちら（リリースノート）](https://info.zenn.dev/about-publication)

## Publicationの主な機能

- **Publicationのトップページが生成される**
  Publicationを作成すると、専用のトップページ（`https://zenn.dev/p/<publication_name>`）が生成されます。このページには、Publicationの紹介文やLinkを配置したり、カバー画像を設定したりすることができ、寄稿された記事の一覧が表示されます。
- **Publicationにユーザーが記事を寄稿できる**
  Publicationのメンバーは、Publicationに記事を寄稿することができます。これにより、Publicationを訪れたユーザーに一貫したテーマの記事を見せることができます。また、記事ページからもPublicationを認識してもらうことができます。寄稿された記事の所有者は著者であり、他のメンバーが編集したりすることはできません。
- **Publicationのメンバーを管理できる**
  Publicationにメンバーを招待したり、ロールを設定して権限を管理することができます。

## Publicationの使い方

### Publicationを作成する

:::message
2022/08/22 現在、Publication機能は利用者を限定して提供しています。利用を希望する方は、こちらの[フォーム](https://docs.google.com/forms/d/e/1FAIpQLSdZvZk18V3Eftc-szrVz8csB93-YwQkSCLBylJQnwGUou-8Lg/viewform)よりご応募ください（2022年8月末まで）なお、応募いただいた全員が利用できるわけではないことはご了承ください。
:::

### Publicationの設定を管理する

オーナーは、Publicationの設定ページから、Publicationに関する設定を行うことができます。

#### 基本設定

Publicationの基本設定として、以下の項目が設定できます。

- 表示名
- 説明文
- Twitter/GitHubのアカウント
- アイコン画像
- カバー画像

#### ナビゲーションメニューの設定

ナビゲーションメニューは、Publicationのトップページに表示されるリンクです。任意のページに対するリンクをラベル付きで設定することができます。

![](/images/articles/how-to-use-publication/publication_setting.png)
*Publicationのトップページの表示例*

### Publicationのメンバーを管理する

#### ロール

Publicationのメンバーにはロールが割り当てられます。ロールの用途と権限は以下の通りです。

| 操作                                        | オーナー | 編集者 |
| ------------------------------------------- | :------: | :----: |
| Publicationの設定を編集                     |    ✅     |        |
| Publicationにメンバーを招待                 |    ✅     |        |
| Publicationのメンバーを除外                 |    ✅     |        |
| Publicationのメンバーのロールを変更         |    ✅     |        |
| Publicationから離脱                         |    ✅     |   ✅    |
| Publicationに自分の記事を寄稿/紐付け解除    |    ✅     |   ✅    |
| Publicationの他のメンバーの記事を紐付け解除 |    ✅     |        |

#### メンバーを追加する

オーナーは、Publicationのメンバー管理ページから、ZennのユーザーをPublicationのメンバーに追加することができます。

#### メンバーを除外する

オーナーは、Publicationのメンバー管理ページから、メンバーをPublicationから除外することができます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

除外されたメンバーがPublicationに寄稿した記事の紐付けは、そのまま残ります。記事の紐付けを解除する場合は、[オーナーが記事の紐付けを解除する](#オーナーが記事の紐付けを解除する)より行います。

#### メンバーのロールを変更する

オーナーは、Publicationのメンバー管理ページから、メンバーのロールを変更することができます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

#### 脱退する

全てのメンバーは、Publicationのメンバー管理ページから、Publicationを脱退ことができます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

Publicationを脱退した後も、Publicationに寄稿した記事の紐付けはそのまま残ります。Publicationから記事の紐付けを解除する場合は、自身の記事の管理ページより、Publicationへの紐付けを解除します。（GitHubデプロイを利用している場合は、frontmatterの`publication_name`の項目を削除します。）

### Publicationの記事を管理する

#### メンバーが記事を寄稿する

Publicationのメンバーは、自身の記事をPublicationに紐付けて寄稿することができます。

- **zenn.devで記事を管理している場合**
  記事の編集ページからPublicationへの紐付けを設定することができます。
- **GitHubリポジトリで記事を管理している場合**
  記事のMarkdownファイルにて、frontmatterの`publication_name`にPublicationのnameを指定することで紐付けを設定することができます。

`publication_name` は、[Publicationの管理ページ](https://zenn.dev/p)から確認することができます。

![](/images/articles/how-to-use-publication/publication_management.png)
*Publicationの管理ページ*

記事を寄稿しても、記事は著者のコンテンツであり、編集権は著者にしかありません。

#### メンバーが記事をレビューする

Comming soon...

#### オーナーが記事の紐付けを解除する

オーナーは、Publicationの記事の管理ページから、記事の紐付けを解除することができます。

## よくある質問

:::details Publicationを開設するため、いままでテックブログとして利用していたユーザーアカウントの記事を、個人のユーザーアカウントに移行したい
移行の対応をいたします。（準備が整い次第、アナウンスいたします。）

ただし、バッジが贈られた記事については、収益の整合性が合わなくなるため移行することができません。
:::
