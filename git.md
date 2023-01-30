# 基本的な Git コマンドまとめ

## 初期設定

`git config --global user.name "username"`  
ユーザ ID

`git config --global user.email "e-mail"`  
メールアドレス

`git config --global color.ui auto`  
出力を色づけする

## 初期化 & リモートリポジトリの追加
`git init`  
`git remote add origin [URL]`  
`git pull origin [baranch]`  

## 直前のコミットを取り消したいとき
`git commit --amend`

## push を取り消したくなったとき
` git reset --mixed HEAD^`  
` git push -f origin [branch]`

# コマンドの説明

## Git の管理
### status

`git status`  
現在のステータスの確認

### log

`git log`  
コミットしたログを出力

`git log --oneline`  
コミットしたログの先頭７桁のコミットIDとコミットメッセージを出力

`git log --graph`  
コミットしたログを縦グラフで出力

## ファイル操作系
### clone

`git clone https://github.com/username/repo-name.git`  
リポジトリをコピーする

### add

`git add [File]`  
ファイルやディレクトリをステージングに追加する  
ワイルドカードで指定もできる。`sample/*.py` など

### commit

`git commit -m "Commit Message"`  
コミットメッセージを同時に指定

### push

`git push origin [branch]`  
リモートに変更を書き込む

### pull

`git pull origin [bransh]`  
リモートの変更を取り込む

## ブランチ操作
### branch

`git branch [new branch]`  
新しいブランチを作成する

`git branch -a`  
すべてのブランチを確認

`git branch -d [branch]`  
ブランチを削除

`git branch -m [branch] [new branch]`  
ブランチ名を変更

### checkout

`git checkout [branch]`  
ブランチを切替える

`git checkout -b [branch]`  
ブランチを作成しつつ、作成したブランチに切替える

### cherry-pick

`git cherry-pick [commit-id]`  
別のブランチのコミットを現在のブランチにコピー

## タグ操作
### tag

`git tag [tag name]`  
現在のコミットにタグを付ける

`git tag -a [tag name] -m "tag message"`  
タグにメッセージを付ける

`git tag -a [tag name] [commit id]`  
コミットした後にタグをつける場合

`git tag -d [tag name]`  
タグを削除する

`git push origin [tag name]`  
リモートにタグをプッシュする