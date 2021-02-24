---
title: "Zennのスラッグ（slug）とは"
emoji: "🤔"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

slug（スラッグ）は、記事や本のユニークなIDのような文字列です。例えばスラッグが`example-article`の記事のURLは

```
https://zenn.dev/ユーザー名/articles/example-article
```

となります。

# slugの指定
ウェブ上で記事や本を作成する場合、slugはランダムで作成されます。[コンテンツのGitHubリポジトリ管理](https://zenn.dev/zenn/articles/connect-to-github)を行っている場合のみ、slugを任意に指定できます。

# slug指定時の注意点

1. slugはサイト全体で（記事や本などのコンテンツの種類ごとに）ユニークにする必要があります。
2. slugは**半角英小文字（`a-z`）、半角数字（`0-9`）、ハイフン（`-`）の12〜50字**の組み合わせにする必要があります。
3. slugは一度zenn.dev上で作成されたら変更できません（slugを変えると別の投稿として作成されます）。


