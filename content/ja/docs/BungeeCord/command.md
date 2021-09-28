---
title: "BungeeCordのコマンド"
linktitle: コマンド
date: 2021-09-22T21:12:02+09:00
draft: false
description: BungeeCordのコマンドの解説
---

## コマンド
### server
#### 引数なし  
現在接続しているサーバーと、接続できるサーバーの一覧が表示されます。  
#### 引数あり
指定したサーバーに移動できます。
```bash
/server lobby
```
### glist
現在どのサーバーに誰がいるのか表示するコマンドです。  
### alert
BungeeCordに接続されているサーバー全体にメッセージを流すコマンドです。メッセージはチャットに表示されます。  
```bash
/alert メッセージ
```
### end
BungeeCordを終了するコマンドです。
### ip
現在接続しているプレイヤーのIPアドレスを表示するコマンドです。  
```bash
/ip steve
```
### greload
BungeeCordのconfigファイルを再読込するコマンドです。  
### send
指定したプレイヤーを指定したサーバーへ移動するコマンドです。  
```bash
/send プレイヤー サーバー
```
#### プレイヤーの引数
- all  
BungeeCordのネットワーク上にいるが、指定したサーバーにいない全てのプレイヤー
- current  
BungeeCordのネットワーク上にいる全てのプレイヤー
- MCID  
指定したプレイヤーのみ
```bash
/send steve life

/send all lobby
```