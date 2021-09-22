---
title: "BungeeCordの設定"
linktitle: "設定"
date: 2021-09-22T20:36:33+09:00
draft: true
description: BungeeCordのconfigファイルの解説
---

## 権限
デフォルトの設定は以下のようになっています。defaultには[server](https://docs.hyte.jp/docs/bungeecord/command/#server)と[list](https://docs.hyte.jp/docs/bungeecord/command/#list)コマンド、adminには[alert](https://docs.hyte.jp/docs/bungeecord/command/#alert)、[end](https://docs.hyte.jp/docs/bungeecord/command/#end)、[ip](https://docs.hyte.jp/docs/bungeecord/command/#ip)、[reload](https://docs.hyte.jp/docs/bungeecord/command/#reload)コマンドを実行する権限が与えられています。
```yml
permissions:
  default:
  - bungeecord.command.server
  - bungeecord.command.list
  admin:
  - bungeecord.command.alert
  - bungeecord.command.end
  - bungeecord.command.ip
  - bungeecord.command.reload
```
### Adminを追加する
configファイルのgroupsという項目で編集します。
デフォルトはmd_5（BungeeCordの開発者）がadminに割り当てられています。
このmd_5の部分を自分のIDに書き換えてください。
```yml
groups:
  md_5:
  - admin
```
```yml
groups:
  Hayate_0927:
  - admin
```

## 設定項目
### player_limit
BungeeCordの最大接続人数です。-1で無制限になります。
### max_players
見かけ上の最大接続人数です。お好きな数字を入力してください。
### servers
BungeeCordのメインの機能である、他のMinecraftサーバーを接続するための設定項目です。  
例: BungeeCordと同じマシンに建てられた25566ポートのlobbyサーバーを追加
```yml
servers:
  lobby:
    motd: Lobby Server
	address: localhost:25566
	restricted: false
```