---
title: "Publicationの使い方"
emoji: "🪐"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

:::message
2022/8/22 現在、Publication機能はベータ版として提供しており、今後仕様を変更する可能性があります。
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
2022/9/1 現在、クローズドベータ期間中であるため、新規作成は受け付けておりません。なお、クローズドベータへの参加のお申し込みをされた方へは、参加可能となった場合にのみメールをお送りします。
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

#### 高度な設定

- **有料バッジの受付**: Publicationに寄稿された記事に対して、バッジを受け付けるかどうかを設定することができます。
- **本文下の固定メッセージ**: Publicationに寄稿された記事の下部に、任意のメッセージを表示することができます。これを使うことにより、記事本文を編集することなくPublicationとして発信したい共通のメッセージを表示することができます。例えば、自社プロダクトの紹介や採用メッセージの掲載などにご活用ください。

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

Publicationのメンバーは、Publicationに寄稿された下書き状態の記事を閲覧することができます。下書きを閲覧するには、Publicationの記事の管理ページから、対象の記事を選択します。

また、記事の投稿者は、記事の編集ページや記事のプレビューページから、閲覧ページのURLを取得することができます。このURLをPublicationのメンバーに共有することで、記事のレビューを依頼することができます。

![](/images/articles/how-to-use-publication/preview1.png)
*記事の編集ページの投稿設定ダイアログ*

![](/images/articles/how-to-use-publication/preview2.png)
*記事のプレビューページ*

:::message
より高度なレビュー機能を検討しています。現状のプレビュー機能では不足している点、改善してほしい点などがあれば、zenn-community の [issue](https://github.com/zenn-dev/zenn-community/issues/440) にご意見をお寄せください。
:::

#### オーナーが記事の紐付けを解除する

オーナーは、Publicationの記事の管理ページから、記事の紐付けを解除することができます。

## Publicationの削除

Publicationの削除は[お問合せフォーム](https://zenn.dev/inquiry)から受け付けています。以下の注意事項を確認いただいた上、必要事項をお問合せフォームより送信してください。運営が内容を確認し、通常は2~3営業日程度で対応します。

### 注意事項

- Publicationの設定はすべて削除されます
- Publicationに投稿された記事の紐付けは解除されます
    - Publicationの設定で有料バッチの受付をOFFにしている場合、記事の紐付けが解除されるとユーザーの設定に切り替わります
- Publicationのフォローは解除されます
- Publicationの削除が実行された後、削除された情報を復元することはできません

### 必要事項

[お問合せフォーム](https://zenn.dev/inquiry)の「その他のお問い合わせ」より、必要事項をご記入の上送信してください。

```
あなたのZenn上のユーザー名：
PublicationのトップページのURL:
削除したい理由：
```

また、メールアドレスの欄にはPublicationのオーナーがZennに登録しているメールアドレスを指定してください。
本人確認のために運営からメールを送信いたします。

## よくある質問

:::details Publicationを開設するため、いままでテックブログとして利用していたユーザーアカウントの記事を、個人のユーザーアカウントに移行したい
[記事を別のユーザーに付け替えるには](https://zenn.dev/zenn/articles/transfer-article) をご覧ください。

ただし、バッジが贈られた記事については、収益の整合性が合わなくなるため移行することができません。
:::
