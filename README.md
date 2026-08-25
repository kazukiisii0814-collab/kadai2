# フォークとプルモデル
## モデルの概要
フォークとプルモデルとはGit及びGithubを用いてチーム開発を行うための手段である。
大きく分けると「複製する（Fork）」「変更する（Commit/Push）」「提案する（Pull Request）」「統合する(Review & Merge)」の4つのフェーズで構成されている。

* 複製する(Fork)
 他人のGitHubリポジトリを、自分のGitHubアカウント配下へ丸ごとコピー（複製）します。これにより自分の領域で自由に変更が可能です。

* 変更する(Clone / Development)
 自分のGitHubにあるフォーク済みリポジトリをローカルPCにダウンロード（Clone）し、機能追加やバグ修正を行います

* 提案する（Pull Request）
 元リポジトリの管理者に対して「自分のフォークでこういう変更をしたので、本番コードに読み込んで（Pullして）ください」と取り込みを提案（リクエスト）します。

* 統合する
 本家の管理者が変更内容を確認（レビュー）します。問題がなければボタン一つで本家のコードに統合（マージ）され、開発が完了します。
  
## 役割及び手順
### 役割分担
* **A　(リード役)** 

* **B　(開発者)** 

### 手順
1. AがGitHub上にリモートリポジトリを用意し、index.html（"Hello"と記述）をmainブランチにPushする。
2. Bがリポジトリをcloneし、作業ブランチを作成。index.htmlを編集してPushし、Aへプルリクエストを出す。
3. AがBのプルリクエストをレビューし、mainブランチにマージする。
4. Aがローカルのmainブランチを最新化（pull）し、作業ブランチを作成。index.htmlを編集してPRを作成・マージする。
5. Bがローカルのmainブランチを最新化（pull）し、作業ブランチを作成。stylesheet.cssを追加してAへプルリクエストを出す。
6. AがBのプルリクエストをレビューし、mainブランチにマージする。

## 演習

### 1: リポジトリの作成
AがGitHub上にリモートリポジトリを作成する。今回はGitで作成した。
```
 mkdir kadai2
 cd kadai2
 git init
 echo "hello" >> README.md
 git add README.md
 git commit -m "first commit"
 gh repo create kadai2 --public --source=. --remote=origin --push
```
### 2: フォークで複製
BがAの作ったリポジトリのあるURLを調べ、右上の方にある「Fork」を押し、「Copy the main branch only」にチェックを入れた状態で、「Create fork」を押す。BのアカウントからAのリポジトリが開けていることがわかる。
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 165635" src="https://github.com/user-attachments/assets/297234f5-50c2-4fbc-a2c5-235e8946c41f" />
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 165648" src="https://github.com/user-attachments/assets/da397936-9c5f-4925-831c-99c2f12bfd96" />


