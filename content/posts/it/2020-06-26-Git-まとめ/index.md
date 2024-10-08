---
title: "Gitまとめ"
date: 2020-06-22T13:21:50+09:00
draft: true
category: git
tags: [ "コンピューター" ]
---

Gitまとめアレコレ

<!--more-->
## ログの見方

Git logについてまずは公式サイトを読んでみよう。公式サイトの説明は[コチラ](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E5%9F%BA%E6%9C%AC-%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E5%B1%A5%E6%AD%B4%E3%81%AE%E9%96%B2%E8%A6%A7)から。

### log を1行で見る。
```sh
git log --oneline
```
### log の整形
```sh
git log --pretty=format:"%h %cd %cn '%s'"
 ## フォーマット：   コミットID    日付    名前    コメント
 ## 例：252692d Fri Apr 5 08:11:59 2019 +0900 fukugit 'バリデータを追加しました。'
```
その他のフォーマット項目については[こちら](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E5%9F%BA%E6%9C%AC-%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E5%B1%A5%E6%AD%B4%E3%81%AE%E9%96%B2%E8%A6%A7)にまとめてあります。  
「git log --pretty=format 用の便利なオプション」で検索したら一覧が出てきます。  

### log と一緒に修正箇所を全て表示する
```sh
git log -p
```

### 修正されたファイル名のみを表示する(上記の簡易版)
```sh
git log -stat
```

### 特定の文字で検索する。
```sh
git log --grep="xxxx"
```

### コミットユーザで検索する。
```sh
git log --auther="xxxx"
```

### 期間で検索する。
```sh
git log --after='2020/04/01'
git log --before='2020/04/01'
```




- - -
## Stash
### stashする。
```sh
git add .
git status
git stash save "一旦退避"
git status
```

### stash一覧を見る
```sh
git stash list
```

### stashの中身を見る
```sh
git stash list
git stash show {0}    ## {0}はgit stash listで一覧化できます。
git stash show {0} -P ## -P オプションで内容も見れます。
```

### stashを消す
```sh
git stash clear     ## 全消し
git stash drop {0}  ## 一部消し
```

### stashを適用する。
```sh
git stash apply {0}
git stash list  ## 適用してもstashは消えていません。
git stash drop {0}
```

### stash を適用して同時に消します。
```sh
git stash pop {0}
```





- - -
## pull
### マージコミットを作らずにPullする方法（rebaseのようなイメージ）
```sh
git pull -–rebase origin branchname
```
[このサイト](https://kray.jp/blog/git-pull-rebase/)にgit pull と git pull --rebase の違いが書かれています。  


- - -
## merge
### コミット有りマージ
```sh
git merge develop  ## マージしたらマージ分のコミットIDが付きます。これは他のコミットIDが変更されないことを意味します。一方でrebaseはコミットIDが変わってしまいます。
```


- - - 
## Rebase
### 2つのブランチをマージします。
```sh
git rebase develop
git status             ## viで競合しているファイルを開いて、競合を解消します。
git add .              ## このタイミングだとまだどのブランチも選択した状態になっていないけど問題無しです。
git rebase --continue  ## このタイミングでブランチが選択された状態になります。
## 注意！！！ rebaseをすることでコミットIDが変わってしまいます。すでにpush済みの場合はpush -f をしないといけなくなる可能性があるので気をつけて！
```

### rebase の取り消し
```sh
git rebase --abort
```

### 複数commitの集約
```sh
git rebase -i HEAD~2  ## 過去2つのコミットが対象です。
## viが開きます。
pick 4eb0c37 コミットその１
pick 8c5ca88 コミットその２
## viで消してしまいたいコミット（集約したいコミット）にs を付けて保存します。
pick 4eb0c37 コミットその１
s 8c5ca88 コミットその２
## さらに別のvi が開くのでコミットコメントを整備します。ファイルを保存します。
コミットその１
コミットその２ ## このコメントが不要なら消します。
## これで終わりです。この方法もコミットIDが変わってしまうので気をつけて下さい。
```




- - -
## ■差分チェック

### ステージングに乗せる前にカレントブランチとの差分を確認する
```sh
git diff --name-only
```

### ステージングに乗せた後にカレントブランチとの差分を確認する
```sh
git diff --cached --name-only
```

### ブランチ間の差分を確認する(両方コミットする必要あり)
```sh
git diff master develop
```

### リモートブランチとの差分を確認する(両方コミットする必要あり)
```sh
git diff origin/dvelop develop
```






- - -
## 取り消し系

### git add する前のファイル・ディレクトリを元に戻す。（追加したファイルは消せない）  
```sh
1： ## 適当なファイルを修正(addしない。)
2: git diff --name-only
3: git checkout .
```

### 追加したファイルを消すのはこちら。  
```sh
1： ## 適当なファイルを追加(addしない。)
2: git clean -df 
```

### 特定ファイルを１つ前に戻す
```sh
1: ## 適当なファイルを修正（コミットされているやつ）
2: git checkout HEAD Test.txt
```

### git add . もしくは commit したあとに取り消す方法  
resetは取り消しがコミットログに残らない。よってpushした後にやるとヤバい。
```sh
1: git add .
2: git diff --cached --name-only
3: git reset --hard HEAD            ## addしたものが全て削除される。 git checkout . と同じ
4: git reset --hard HEAD^           ## 1つ前のコミットに戻る。今のコミットは削除される。)
5: git reset --hard vsd122414dsfsfe ## コミットIDを指定して、コミットIDのところまで戻る。コミットIDを削除するのではないので気を付けること
```

### resetを取り消したい（resetしたけど元の状態に戻したい時用)
```sh
1: git add .
2: git commit -m "test"
3: git reset --hard HEAD      ## test commit を無かったことに。
4: git reset --hard ORIG_HEAD ## test commit を復活
```

### pushをした後に取り消す方法
revertはresetと違ってコミットログに残る。
```sh
1: git add .
2: git commit -m"xxxxxxxxxx"
3: git log                     ## 取り消し対象のコミットIDを取得
4: git revert vsd122414dsfsfe  ## 取り消し対象のコミットIDを指定
5: git push
```



- - -
## コミット

### 直前のコミットメッセージを修正
```sh
git commit --amend -m"ファイルを追加しました。"
```

### ２つ以上前のコミットメッセージを修正
```sh
## 残念ながら git rebase -i を使うしかないです。
```

### 直前のコミットに軽微なコミットを混ぜ込む方法。  
```sh
1: ## 適当なファイルを修正
2: git add .
3: git commit --amend　## 直前のコミットに１を混ぜ込む
```

### コメント付きコミット(一番標準的なもの)  
```sh
1: ## 適当なファイルを修正
2: git add .
3: git commit -m"xxxxxxxxxx"
```

- - -
## CherryPick
```sh
git cherry-pick 7c44840faab76c69c0b0a
```


- - -
## 外部Gitブランチを自分のブランチ内に取り込む(git submodule)
サブモジュールについては[公式サイト](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%81%95%E3%81%BE%E3%81%96%E3%81%BE%E3%81%AA%E3%83%84%E3%83%BC%E3%83%AB-%E3%82%B5%E3%83%96%E3%83%A2%E3%82%B8%E3%83%A5%E3%83%BC%E3%83%AB)の説明を一読したほうがよいかもね。 

### submodule 取り込み
```sh
git submodule add サブモジュール化したいリポジトリ パス/名前指定
cd サブモジュール化したディレクトリ
git submodule update --init --recursive
```

### submodule を削除
```sh
cd サブモジュール化したいリポジトリのディレクトリ（トップレベル）
git submodule deinit -f 追加したサブモジュール
git rm -f 追加したサブモジュール
cd 自分のブランチのディレクトリ（トップレベル）
$ rm -rf .git/modules/追加したサブモジュール 
```

- - -
## 削除
### ローカルブランチの削除  
```sh
git push -D branchname ##-Dはpush残しがあっても削除する強力なやつ
```

### リモートブランチの削除  
```sh
git push --delete origin feature/test
```
