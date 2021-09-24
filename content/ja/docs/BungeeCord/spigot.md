---
title: "Spigotサーバーを接続"
linktitle: Spigot
date: 2021-09-24T21:26:21+09:00
draft: false
description: BungeeCordとSpigotを接続する方法
---

## Spigotの設定
BungeeCordとSpigotを接続するために、Spigotで行う設定です。
### server.properties
- online-mode  
trueからfalseに変更してください。  
この項目をfalseにするとSpigotは正規ユーザーかどうかを確認しませんが、代わりにBungeeCordで確認するので問題ありません。
- server-port  
1024から49151までの範囲で、他のソフトウェアと被らない番号に変更してください。  
Minecraft Java Editionのマルチプレイでは25565を標準で使用するので、25565をBungeeCordに割り当てて、それ以外の数字をSpigotに割り当てると良いと思います。
### spigot.yml
- bungeecord:  
falseからtrueに変更してください。
### bukkit.yml
- connection-throttle:  
-1に変更してください。  
これは、接続する速さが設定した値より早かった場合、それを弾くものですが、BungeeCordを使用する際は無効化する方が良いです。