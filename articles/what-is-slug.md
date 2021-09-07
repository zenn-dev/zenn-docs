---
title: "Zennのスラッグ（slug）とは"
emoji: "🤔"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

slug（スラッグ）は、記事や本のユニークなIDのような文字列です。例えばslugが`example-article`の記事のURLは

```
https://zenn.dev/ユーザー名/articles/example-article
```

となります。

# slugの指定
ウェブ上で記事や本を作成する場合、slugはランダムで作成されます。

[コンテンツのGitHubリポジトリ管理](https://zenn.dev/zenn/articles/connect-to-github)を行っている場合は、slugを任意に指定できます。

- 記事の場合はmarkdownファイル名を`articles/[slug].md`という形式にします
- 本の場合はディレクトリ名を`books/[:slug]`という形式にします

Zenn CLIを使うとファイルの作成時にslugを指定することができます。たとえば`what-is-slug`というslugの記事を作成したい場合は以下のようなコマンドを実行します。

```bash
$ npx zenn new:article --slug what-is-slug
# => articles/what-is-slug.md`が作成される
```

詳しくは[Zenn CLIを使ったファイルの作成方法](https://zenn.dev/zenn/articles/zenn-cli-guide#%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E9%85%8D%E7%BD%AE%E3%83%AB%E3%83%BC%E3%83%AB)をご覧ください。

# slug指定時の注意点

1. slugはサイト全体で（記事や本などのコンテンツの種類ごとに）ユニークにする必要があります。
2. slugは**半角英小文字（`a-z`）、半角数字（`0-9`）、ハイフン（`-`）、アンダースコア（`_`）の12〜50字**の組み合わせにする必要があります。
3. slugは一度zenn.dev上で作成されたら変更できません（slugを変えると別の投稿として作成されます）。


