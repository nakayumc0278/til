### 初期設定

```
git config --global user.name "USERNAME"
git config --global user.email "MAILADDR"
```

### 初回作成

```
git clone https://github.com/nakayumc0278/*****.git
```

### ステージング

```
git add [FL名]
```

### コミット

```
git commit -m "COMMENT" [FL名]
```

### ステータス表示

```
git status
git log
git log --oneline
```

### 詳細表示　ブランチ作成

```
git branch -a
git checkout -b ブランチ名
git branch -d 削除したいブランチ名
git checkout 戻りたいブランチ名
```

### リモートにプッシュ

```
git push origin ブランチ名
```

### リモートからプル

```
git pull origin ブランチ名
```
