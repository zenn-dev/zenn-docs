---
title: "Zennのコンテンツ作成ガイド"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn"]
published: true
---

このページではZennで記事や本を作成するときの執筆環境について紹介します。

# Zenn の執筆方法は 2 種類

Zennのコンテンツは次のいずれかの方法で作成します。

## 1. Web エディター

![Zennのエディター](https://storage.googleapis.com/zenn-user-upload/tb04ri7f5v9mdccsehi5jppvfpm3)

ブラウザ上で動くエディターです。Zennにログインした状態で使用します。

:::details ショートカットを使用しよう

オンラインのマークダウンエディターでは、以下のショートカットを使用できます。

- **Ctrl + P（プレビュー）**：マークダウンがどのように表示されるかをチェックできます。もう一度ショートカットを実行すると、エディターに戻ります。
- **Ctrl + S（内容の保存）**：変更内容を保存します。
- **Ctrl + I（埋め込み）**：ツイートや YouTube、CodePen、SpeakerDeck などの埋め込みコンテンツを挿入するためのモーダルが表示されます。

※ Mac の場合は`Ctrl`の代わりに`⌘`キーを使用します。

:::

## 2. ローカルのテキストエディター + CLI

![VS code](https://storage.googleapis.com/zenn-user-upload/n0tufad6ruthuy0j2hxhffg87hpz =660x)

![](https://storage.googleapis.com/zenn-user-upload/ve1rve2rb3yvvcat974fxt2rftc1)

自分の好きな環境で執筆したい方は**GitHub リポジトリとの連携機能**を利用することをおすすめします。リポジトリ連携をすると、特定のブランチに変更があったときに自動でコンテンツがzenn.devに反映されるようになります。

📘 **[Zenn と GitHub リポジトリを連携する →](https://zenn.dev/zenn/articles/connect-to-github)**

リポジトリ連携時には、ローカルでマークダウンファイルを作成し、好きなテキストエディターで編集を行います。Zenn CLIを使うことでブラウザでプレビューしながら執筆することが可能になります。

📘 **[Zenn CLI を導入する →](https://zenn.dev/zenn/articles/install-zenn-cli)**

---

オンラインエディターを使う場合も、CLIを使う場合もマークダウンの書き方は変わりません。具体的な記法は下記のリンク先をご覧ください。

📘 **[Zenn のマークダウン記法 →](https://zenn.dev/zenn/articles/markdown-guide)**
