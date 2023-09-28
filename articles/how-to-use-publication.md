---
title: "Publicationの使い方"
emoji: "🪐"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

:::message
2023/1/16 現在、Publication機能はベータ版として提供しており、今後仕様を変更する可能性があります。
:::

## Publicationとは

Publicationとは、個人または組織が、一貫性のあるテーマについての記事をまとめて投稿することができる機能です。例えば以下のような使い方を想定しています。

- 会社のTech Blogとして、自社サービスの開発に関連した記事を複数人で投稿したい
- 個人やグループで1つのテーマに対して継続的に記事を投稿し、まとまりを作りたい

→ [詳しくはこちら（リリースノート）](https://info.zenn.dev/about-publication)

## Publicationの主な機能

### Publicationのトップページが生成される
Publicationを作成すると、専用のトップページ（`https://zenn.dev/p/<publication_name>`）が生成されます。このページには、Publicationの紹介文やリンクを配置したり、カバー画像を設定したりすることができ、投稿された記事の一覧が表示されます。

### Publicationにユーザーが記事を投稿できる
Publicationのメンバーは、Publicationに記事を投稿できます。投稿された記事にはPublicationの情報が表示され、記事の下部に固定文言を設定できます。投稿された記事の所有者は著者であり、他のメンバーが編集したりすることはできません。

### Publicationのメンバーを管理できる
Publicationにメンバーを招待したり、ロールを設定して権限を管理できます。

## Publicationの使い方

### Publicationを作成する

Publicationの[トップページ](https://zenn.dev/publications)より申請を行ってください。運営が確認を行い、3営業日以内に申請者のメールアドレスに結果をお知らせします。

:::message
組織の名前を利用する際の注意点

- 企業や学校法人などのPublicationとして申請する場合、その名前を使用することについて関係者からの許可を取ったうえで申請してください。大規模な組織である場合は、自ら責任を取れる範囲の名前にすることをご検討ください（例: 〇〇株式会社△△チーム、など）
- ユーザーコミュニティなどの場合も、コミュニティ内で確認を取ったうえで申請してください。
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

#### リンクの設定

Publicationのトップページに表示されるリンクを設定できます。任意のURLとラベルを指定します。

![](/images/articles/how-to-use-publication/publication_setting.png)
*Publicationのトップページの表示例*

#### 高度な設定

- **有料バッジの受付**: Publicationに投稿された記事に対して、バッジを受け付けるかどうかを設定できます。
- **本文下の固定メッセージ**: Publicationに投稿された記事の下部に、任意のメッセージを表示できます。これを使うことにより、**記事本文を編集することなくPublicationとして発信したい共通のメッセージを表示する**ことができます。例えば、自社プロダクトの紹介や採用メッセージの掲載などにご活用ください。

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
| Publicationに自分の記事を投稿/紐付け解除    |    ✅     |   ✅    |
| Publicationの他のメンバーの記事を紐付け解除 |    ✅     |        |

#### メンバーを追加する

オーナーは、Publicationのメンバー管理ページから、ZennのユーザーをPublicationのメンバーに招待できます。招待を受け取ったユーザーは、招待メールに記載されたリンクから、招待を承認できます。

#### メンバーを除外する

オーナーは、Publicationのメンバー管理ページから、メンバーをPublicationから除外できます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

除外されたメンバーがPublicationに投稿した記事の紐付けは、そのまま残ります。記事の紐付けを解除する場合は、[オーナーが記事の紐付けを解除する](#オーナーが記事の紐付けを解除する)より行います。

#### メンバーのロールを変更する

オーナーは、Publicationのメンバー管理ページから、メンバーのロールを変更できます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

#### 脱退する

全てのメンバーは、Publicationのメンバー管理ページから、Publicationを脱退できます。ただし、Publicationにオーナーが1人もいなくなるような操作はできません。

Publicationを脱退した後も、Publicationに投稿した記事の紐付けはそのまま残ります。Publicationから記事の紐付けを解除する場合は、自身の記事の管理ページより、Publicationへの紐付けを解除します。（GitHubデプロイを利用している場合は、frontmatterの`publication_name`の項目を削除します。）

### Publicationの記事を管理する

#### メンバーが記事を投稿する

Publicationのメンバーは、自身の記事をPublicationに紐付けて投稿できます。

:::message
記事をPublicationに紐付けても、記事の編集権限は著者にしかありません。
:::

- **zenn.devで記事を管理している場合**
  記事の編集ページからPublicationへの紐付けを設定できます。
- **GitHubリポジトリで記事を管理している場合**
  記事のMarkdownファイルにて、frontmatterの`publication_name`にPublicationのnameを指定することで紐付けを設定できます。

`publication_name` は、[Publicationの管理ページ](https://zenn.dev/dashboard/publications)から確認できます。

![](/images/articles/how-to-use-publication/publication_management.png)
*Publicationの管理ページ*

#### メンバーが記事をレビューする

Publicationのメンバーは、Publicationに投稿された下書き状態の記事を閲覧できます。下書きを閲覧するには、Publicationの記事の管理ページから、対象の記事を選択します。

また、記事の投稿者は、記事の編集ページや記事のプレビューページから、閲覧ページのURLを取得できます。このURLをPublicationのメンバーに共有することで、記事のレビューを依頼できます。

![](/images/articles/how-to-use-publication/preview1.png)
*記事の編集ページの投稿設定ダイアログ*

![](/images/articles/how-to-use-publication/preview2.png)
*記事のプレビューページ*

#### オーナーが記事の紐付けを解除する

オーナーは、Publicationの記事の管理ページから、記事の紐付けを解除できます。

## Publicationの削除

Publicationの削除は [お問合せフォーム](https://zenn.dev/inquiry) の「その他のお問い合わせ」より申請してください。以下の注意事項を確認いただいた上、必要事項をお問合せフォームより送信してください。運営が内容を確認し、通常は2~3営業日程度で対応します。

:::message alert
**注意事項**

- Publicationの設定はすべて削除されます。
- Publicationに投稿された記事の紐付けは解除されます。（Publicationの設定で有料バッチの受付をOFFにしている場合、記事の紐付けが解除されるとユーザーの設定に切り替わります。）
- Publicationのフォローは解除されます。
- Publicationの削除が実行された後、削除された情報を復元することはできません。
:::

必要事項

```
あなたのZenn上のユーザー名：
PublicationのトップページのURL:
削除したい理由：
```

また、メールアドレスの欄にはPublicationのオーナーがZennに登録しているメールアドレスを指定してください。本人確認のために運営からメールを送信いたします。

## よくある質問

:::details Publicationを開設するため、いままでテックブログとして利用していたユーザーアカウントの記事を、個人のユーザーアカウントに移行したい
[記事を別のユーザーに付け替えるには](https://zenn.dev/zenn/articles/transfer-article) をご覧ください。

ただし、バッジが贈られた記事については、収益の整合性が合わなくなるため移行することができません。
:::
