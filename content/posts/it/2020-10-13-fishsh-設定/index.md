---
title: "Fish shellをインストールする方法"
date: 2020-10-13T01:21:50+09:00
draft: true
category: shell
tags: [ "コンピューター" ]
---
補完機能が非常に便利なFishシェルをインストールしてログインシェルに設定する方法をメモしていきます。  

<!--more-->

## インストール
```sh
brew install fish
```

## ログインシェルへ設定
まずはFishシェルのパスを確認します。  
```sh
which fish
> /usr/local/bin/fish
```

vim で上記のパスをshellsに追記します。  
```sh
vi /etc/shells
> /usr/local/bin/fish
```

ログインシェルを変更します。  
```sh
chsh -s /usr/local/bin/fish
```

上記の方法だとターミナルを落とすとログインシェルが元に戻ってしまうので`.bash_profile` へ `/usr/local/bin/fish` を追加します。
これでターミナルを再度開いてもログインシェルはFishシェルのままです。  
```sh
vi .bash_profile
> /usr/local/bin/fish
```


## oh-my-fishのインストール
oh-my-fishとは、FishシェルのテーマをインストルールしたりするFishシェルの拡張ツールです。  
```sh
curl -L https://github.com/oh-my-fish/oh-my-fish/raw/master/bin/install | fish
```

インストールできたかバージョン確認を見てみよう。  
```sh
omf -v
> Oh My Fish version 6
```

Fishシェルのテーマをインストールします。  
```sh
omf install beloglazov
```

Fishシェルのテーマは[コチラ](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md)にたくさん用意されています。  