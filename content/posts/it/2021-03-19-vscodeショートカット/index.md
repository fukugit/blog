---
title: "VSCodeショートカット集"
date: 2021-03-19T03:21:50+09:00
draft: false
category: tool
tags: [ "コンピューター" ]
---

VSCodeでよく使うショートカットをまとめました。

<!--more-->
## US配列キーボード
US配列キーボードだとショートカットキーが正常に動かないこともあります。  
そんな時は[コチラ](https://webrandum.net/visual-studio-code-keydown-code/)を参考に。  

## 注意
ここで定義したショートカットは、初期設定とは異なるショートカットキーもあるので、動かない場合はcommand idで確認して下さい。  

## ショートカットキー 一覧の開き方
| description         | Key Map           | command id            |
| ------------------- | ----------------- | --------------------- |
| Open shourtcut view | `⌘` `k` , `⌘` `S` | openGlobalKeybindings |

## 画面分割系

| description                       | Key Map     | command id               |
| --------------------------------- | ----------- | ------------------------ |
| Split Editor                      | `⌘` `\`     | splitEditor              |
| Split Editor to bottom            | `⌥` `⌘` `\` | splitEditorOrthogonal    |
| Split Terminal                    | `⌘` `\`     | terminal.split           |

## エディタ系

| description      | Key Map           | command id      |
| ---------------- | ----------------- | --------------- |
| Close all editor | `⌘` `k` , `⌘` `w` | closeAllEditors |

## サイドバー移動系
| description                       | Key Map | command id               |
| --------------------------------- | ------- | ------------------------ |
| Go to Active file name in SideBar | `⌘` `;` | showActiveFileInExplorer |
| Focus into SideBar                | `⌘` `0` | focusSideBar             |
| Toggle SideBar                    | `⌘` `B` | toggleSidebarVisibility  |
| Open File in SideBar              | `Space` | openFilePreserveFocus    |

## ターミナル系
| description    | Key Map | command id    |
| -------------- | ------- | ------------- |
| Close Terminal | `⌃` `w` | terminal.kill |

## サーバ起動系
| description           | Key Map           | command id |
| --------------------- | ----------------- | ---------- |
| Open with Live Server | `⌘` `n` , `⌘` `o` | goOnline   |
| Stop with Live Server | `⌘` `n` , `⌘` `c` | goOffline  |