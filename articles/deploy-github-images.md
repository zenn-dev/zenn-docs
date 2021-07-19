---
title: "GitHubリポジトリ連携で画像をアップロードする方法"
emoji: "🎆"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

:::message
2021/07/19 現在、CLI での画像管理機能はベータ版として提供しており、今後仕様が変わる可能性があります。
:::

GitHub リポジトリ連携機能により、GitHub リポジトリで管理されている画像を Zenn にアップロードすることができます。

## 画像ファイルの配置ルール

画像ファイルはリポジトリ直下の `/images` ディレクトリに配置します。 `/images` ディレクトリの中の構造に制限はありませんが、拡張子だけはチェック対象となります。

```text
.
└─ images
   ├── example-image1.png
   └── example-article-1
       └─ image1.png
```

## 画像ファイルの制限事項

画像ファイルの制限は以下の通りです。違反する場合はデプロイ時にエラーとなります。

- ファイルサイズは 3MB 以内
- 対応する拡張子は `.png` `.jpg` `.jpeg` `.gif` のみ

## 画像の参照方法

画像は、記事の本文や、本のチャプターの本文から参照することができます。参照するには、画像埋め込み記法の URL 部分に `/images/` から始まる絶対パスを指定します。相対パスで指定しないようご注意ください。

```markdown
# 正しい指定方法

![](/images/example-image1.png)
![](/images/example-article-1/image1.png)

# 誤った指定方法

![](../images/example-image1.png)
![](//images/example-image1.png)
```

## Zenn CLI でプレビュー

:::message
対応バージョン: `0.1.92-alpha.2` 以降

📘 [Zenn CLI の導入がまだの方はこちら](https://zenn.dev/zenn/articles/install-zenn-cli)
:::

本文に画像が正しく表示されるかは、Zenn CLI のプレビューで確認することができます。

```shell
npx zenn preview # プレビュー開始
```

本文

```
↓正しく表示できている
![](/images/zenn-editor.png)

↓パス指定が誤っている
![](../images/zenn-editor.png)
```

プレビュー

![](/images/articles/deploy-github-images-preview.png)

## 画像のアップロード

GitHub リポジトリに画像をプッシュすることで、画像が Zenn にアップロードされ、参照した記事や本に反映されます。

GitHub リポジトリから画像を削除すると、Zenn 上からも画像は削除されます。記事や本から参照されている画像を削除しないようご注意ください。

画像を差し替える場合、デプロイ完了から最大 1 分程度、古い画像が表示されることがあります。その場合は、時間を置いて画面をリロードしてください。
