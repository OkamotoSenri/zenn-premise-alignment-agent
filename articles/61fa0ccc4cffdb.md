---
title: "ZennとGitHubを連携してCLIで記事を書く環境を作った"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn", "github", "cli"]
published: false
---

## はじめに

ZennはGitHubリポジトリと連携することで、ローカルで記事を書いてGitにpushするだけで公開できる。この記事では、その環境を作るまでの手順をまとめる。

## 手順

### 1. GitHubリポジトリを作成する

GitHub上で新しいリポジトリを作成する。名前は何でもよいが、Zenn用とわかりやすいものにしておくと管理しやすい。

### 2. ZennとGitHubを連携する

[Zennのダッシュボード](https://zenn.dev/dashboard/deploys)から「GitHubからのデプロイ」を設定し、作成したリポジトリを選択して連携する。

### 3. リポジトリをクローンする

```bash
git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

### 4. Zenn CLIをセットアップする

```bash
npm init --yes
npm install zenn-cli
npx zenn init
```

`npx zenn init` を実行すると `articles/` と `books/` ディレクトリが作成される。

## 記事を書いてみる

新しい記事ファイルを作成するには以下のコマンドを使う。

```bash
npx zenn new:article
```

ローカルでプレビューしながら書くには：

```bash
npx zenn preview
```

ブラウザで `http://localhost:8000` を開くと、記事のプレビューが確認できる。

## 公開する

記事のフロントマターの `published` を `true` にしてGitHubにpushすれば、Zennに自動でデプロイされる。

```bash
git add .
git commit -m "add article"
git push
```

## まとめ

一度設定してしまえば、あとはローカルで書いてpushするだけで記事が公開できる。バージョン管理もできるのでGit慣れしている人には快適な執筆環境になる。
