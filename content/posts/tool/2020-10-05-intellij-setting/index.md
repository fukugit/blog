---
title: "IntelliJの必須設定の一覧"
date: 2020-10-05T01:21:50+09:00
draft: false
category: tool
tags: [ "tool" ]
---
IntelliJでこれだけはインストール時にやっておいたほうが良いと思っている設定です。  
<!--more-->

## スペースを表示させる
エディタ内のスペースを表示させる設定です。  
`
preference > Editor > General > Appearance > ON ‘Show whitespaces’
`
![](./img/show-whitespases.gif)  

## エディタ内の縦線を消す方法
まずエディタ内の縦線とは何かといいますと、右側にあるこいつです。  
![](./img/vertical-line.gif)  

上記の縦線を消す設定はこちらです。
`
preference > Editor > General > Appearance > OFF ‘Show hard wrap guide’
`
![](./img/vertical-line-2.gif)  


## エディタの文字サイズを変更する方法
`
preference > Editor > Font
`
![](./img/font-size-editor.gif)  


## エディタ全体の文字サイズを変更する方法
`
preference > Editor > Font
`
![](./img/font-size-all.gif)  


## タブをスペースに変換する方法
`
preference > Editor > Code Style> Java > OFF ‘Use Tab character’
`

個人的にはスペース4つではなく、以下の設定でスペース2つにすることをおすすめします。
`
preference > Editor > Code Style> Java > ‘Indent 2’
`
![](./img/change-tab-space.gif)  

