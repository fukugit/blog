# Blog
日々の出来事や勉強したことを残しています。  
ブログはこちらからどうぞ。  
https://fukugit.github.io/blog/

## ローカルでの実行方法
このブログはHugoで作られています。ローカルで動かす方法とビルドする方法の２つについて説明していきます。  

### 前準備
以下のコマンドでHugoをインストールして下さい。
1. `brew install hugo`  

### インストール
まずこのブログをローカルへインストールする方法を説明していきます。  
`git clone`するのみでは動作しません。下記手順に従ってインストールして下さい。  

1. `git clone https://github.com/fukugit/blog.git`  

2. `cd blog/themes/`  

3. `git submodule add https://github.com/fukugit/Mainroad.git`  
上記のテンプレートは例です。テンプレートは[コチラ](https://themes.gohugo.io/)から選定することができます。  

4. `cd ./mainroad`  
こちらのディレクトリ名も例です。テンプレートの名称に合わせて変更して下さい。  

5. `git submodule update --init --recursive`  

6. `git checkout develop`  
ここは必要に応じてdevelopブランチにして下さい。テンプレートを更新しなけばmasterのままで大丈夫です。  

7. config.tomlの修正  
下記の`theme`の値を`4`で設定したディレクトリ名に変更して下さい。  
```
theme = "mainroad"
```

## ローカルで動かす方法
1. `cd blog`  

2. `hugo server --ignoreCache`  

3. `http://localhost:1313/blog/` をブラウザで開けばブログを見ることができます。  

## ビルドする方法
流れとしては、pushする前に`hugo`を実行して下さい。ブログが反映されます。  
1. `rm -Rf docs/`  

2. `hugo`  

3. `mv public/docs`  

4. `git add .`  

5. `git commit -m "Add a image file"`  

6. `git push`  


## ブログを書くうえでの注意点
ブログ(.md)ファイル内のヘッダに`draft`があります。こちらは必ず`false`にしておいて下さい。  
もしそうなっていないようであれば、いくらローカルで実行してブログが表示されたとしてもビルドをするとそのブログが表示されなくなってしまいます。  

## 謝辞
今は[Mainroad](https://github.com/Vimux/Mainroad)のテーマを使わさせてもらっています。  

