## 基本的な Git コマンドまとめ

# 初期設定

`git config --global user.name "USERNAME"`  
ユーザ ID

`git config --global user.email "MAILADDR"`  
メールアドレス

`git config --global color.ui auto`  
出力を色づけする

# clone

`git clone https://github.com/nakayumc0278/*****.git`  
リポジトリをコピーする

# add

`git add [FL名]`  
ファイルやディレクトリをインデックスに登録  
ワイルドカードで指定もできる。sample\*.py test?.js など。

# commit

`git commit -m “[コメント]”`  
コミットメッセージを同時に指定

`git commit --amend`  
直前のコミットを修正する

# status

`git status`  
ステータスの確認

# log

`git log`  
コミットログを参照

`git log --oneline`  
コミットログの先頭７桁のコミット ID を表示

`git log --graph`  
コミットログを縦グラフで表示

# branch

`git branch &[new branch]`  
現在のブランチの確認 と 新しいブランチを作成する.

`git branch -a`  
すべてのブランチを確認

`git branch -r`  
リモートブランチを確認

`git branch -d [branch]`  
ブランチを削除

`git branch -m [branch] [new branchname]`  
ブランチ名を変更

# checkuout

`git checkout [branch]`  
ブランチを変更

`git checkout -b [branch]`  
ブランチを作成して移動する

# push

`git push origin [branch]`
リモートに変更を書き込む

# pull

`git pull origin [bransh]`
リモートの変更を取り込む

# cherry-pick

`git cherry-pick [コミット ID]`  
別のブランチのコミットを現在のブランチにコピー
