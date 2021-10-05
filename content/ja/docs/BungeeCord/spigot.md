---
title: "BungeeCordとSpigotサーバーを接続"
linktitle: Spigotを接続
date: 2021-09-24T21:26:21+09:00
draft: false
description: BungeeCordとSpigotを接続する方法
weight: 50
---

## Spigotの設定
BungeeCordとSpigotを接続するために、Spigotで行う設定です。
### server.properties
- online-mode  
trueからfalseに変更してください。  
この項目をfalseにするとSpigotは正規ユーザーかどうかを確認しませんが、代わりにBungeeCordで確認するので問題ありません。
- server-port  
[1024から49151までの範囲](https://ja.wikipedia.org/wiki/TCP%E3%82%84UDP%E3%81%AB%E3%81%8A%E3%81%91%E3%82%8B%E3%83%9D%E3%83%BC%E3%83%88%E7%95%AA%E5%8F%B7%E3%81%AE%E4%B8%80%E8%A6%A7#%E7%99%BB%E9%8C%B2%E6%B8%88%E3%81%BF%E3%83%9D%E3%83%BC%E3%83%88%E7%95%AA%E5%8F%B7_(1024%E2%80%9349151))で、コンピューターで使用する他のソフトウェアと被らない番号に変更してください。  
Minecraft Java Editionのマルチプレイでは25565を標準で使用するので、25565をBungeeCordに割り当てて、それ以外の数字をSpigotに割り当てると良いと思います。
### spigot.yml
- bungeecord:  
falseからtrueに変更してください。
### bukkit.yml
- connection-throttle:  
-1に変更してください。  
これは、接続する速さが設定した値より早かった場合、それを弾くものですが、BungeeCordを使用する際は無効化する方が良いです。

## BungeeCordの設定
BungeeCordとSpigotを接続するために、BungeeCordで行う設定です。  
config.ymlのserversの項目を以下のように編集してください。
```yml
servers:
  server1:
    motd: Server1
	address: localhost:25566
	restricted: false
```
2行目はサーバー名（lobby、lifeなど）にしてください。  
3行目はMOTDを設定してください。  
4行目はSpigotのアドレスです。BungeeCordとSpigotを同じコンピューターで動かす場合は、「localhost:port」のようになります。  
5行目はサーバーに接続する際、「bungeecord.server.サーバー名」の権限を必要とするかの設定です。trueにすると、この権限を持っていないプレイヤーはそのサーバーに参加出来なくなります。
### 例
- lobbyサーバー（localhost、25566）を追加
```yml
servers:
  lobby:
    motd: A Lobby Server
    address: localhost:25566
	restricted: false
```
- lifeサーバー（localhost、25567）を追加
```yml
servers:
  lobby:
    motd: A Lobby Server
	address: localhost:25566
	restricted: false
  life:
    motd: A Life Server
	address: localhost:25567
	restricted: false
```