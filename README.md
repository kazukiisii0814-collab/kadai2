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

### 3: クローンの作成　
Bがフォークによって作られたリポジトリのURLを自身のローカルリポジトリにクローンする。
```
git clone [リモートリポジトリのURL].git
cd [リポジトリ名]
```

### 4: 作業ブランチでの開発
手順を基にBは作業ブランチを作り開発を進める。
```
git branch develop # 適当なブランチ名
git switch develop
vi index.html # ファイルの編集
git add index.html
git commit -m "add index.html"
git push origin develop
```

修正をしたらプッシュし、GitHub上で「Compare & pull request」を押し、「Create pull request」を押して、「Merge pull request」をしてAにリクエストを送る。

<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170106" src="https://github.com/user-attachments/assets/1e1121a0-e067-4efa-810a-197beea2d6b8" />
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170114" src="https://github.com/user-attachments/assets/68e406bc-c8a8-40c8-876f-567e41b0253d" />
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170130" src="https://github.com/user-attachments/assets/33e6c94e-2771-474f-94aa-9746ea7fa963" />

AがGitHub上でBから送られたリクエストをレビューしマージする。
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170151" src="https://github.com/user-attachments/assets/af1b4929-ad78-457b-8ca6-a741c70cd1e1" />

矢印から内容をレビューし問題がなければ、「Merge pull request」を押して、「Confirm merge」を押してマージする。
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170233" src="https://github.com/user-attachments/assets/8794447b-9a68-44fd-92be-2d740342829c" />

Aはローカルのmainブランチを最新化(pull)し、作業ブランチを作り開発を進める。
```
git branch develop2 # 適当なブランチ名
git switch develop2
vi index.html # ファイルの編集
git add index.html
git commit -m "add index.html"
git push origin develop2
```

修正をしたらプッシュし、GitHub上で「Compare & pull request」を押し、「Create pull request」を押して、「Merge pull request」を作成しマージする。
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170900" src="https://github.com/user-attachments/assets/b8d7b9e8-89ae-4b23-98a4-0ece9f7e6624" />
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170926" src="https://github.com/user-attachments/assets/a3b5c5d0-8586-4ceb-8404-41a9185feb3e" />
<img width="1920" height="1032" alt="スクリーンショット 2026-08-24 170941" src="https://github.com/user-attachments/assets/d8537acb-9c3c-45d6-8e19-08f1267d034c" />

Bがローカルのmainブランチを最新化し、作業ブランチを作成。stylesheet.cssを追加しプルリクエストを出す。
```
git remote add upstream [AのリモートリポジトリのURL].git
git switch main
git fetch upstream
git merge upstream/main
git switch develop
echo "hello" >> stylesheet.css
git add stylesheet.css
git commit -m "add stylesheet.css commit"
git push -u origin develop
```
プッシュしたら、先ほどと同じ過程を通しマージを行い、AがBのプルリクエストをレビューし、mainブランチにマージする。。

## 参考
* (2025/11/28)「つくって、壊して、直して学ぶ Git＆GitHub 入門」　高橋あおい　9784798191584
