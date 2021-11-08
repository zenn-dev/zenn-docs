---
title: "ZennをRSSフィードで購読する"
emoji: "🎞"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn", "rss"]
published: true
---

現在Zennでは以下の3種類のRSSフィードを用意しています。

# 1. トレンドのフィード

**https://zenn.dev/feed**

# 2. ユーザーごとのフィード

```
https://zenn.dev/ユーザー名/feed
```

たとえば Zenn 公式アカウント（[@zenn](https://zenn.dev/zenn)）のフィードは[https://zenn.dev/zenn/feed](https://zenn.dev/zenn/feed)となります。
ユーザーページのURLの末尾に`/feed`を足す形です。

:::details スクラップをフィードに含める

デフォルトではスクラップはフィードに含まれてません。スクラップも含めたい場合は`https://zenn.dev/ユーザー名/feed?include_scraps=1`のように`include_scraps=1`というクエリ文字列を指定します。

:::

:::details 全ての公開アイテムをフィードに含める
デフォルトではフィードに出力される投稿（記事・本）の数は20ほどに制限されています。すべての公開された投稿を出力したい場合は`https://zenn.dev/ユーザー名/feed?all=1`のように`all=1`というクエリ文字列を指定します。
:::

# 3. トピックごとのフィード

```
https://zenn.dev/topics/トピック名/feed
```

たとえばトピック「[zenn](https://zenn.dev/topics/zenn)」のフィードは[https://zenn.dev/topics/zenn/feed](https://zenn.dev/topics/zenn/feed)となります。
トピックページのURLの末尾に`/feed`を足す形です。

