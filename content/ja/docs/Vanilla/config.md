---
title: "バニラサーバーの設定"
linktitle: "設定"
date: 2021-10-16T20:27:15+09:00
draft: true
description: バニラサーバーの設定方法の解説
---

### 設定ファイルを編集
バニラサーバーの設定を変更するには、「server.properties」というファイルを編集します。

|項目|初期値|解説|
|:--|:--|:--|
|broadcast-rcon-to-ops|true||
|view-distance|10|描画する最大チャンク数|
|enable-jmx-monitoring|false||
|server-ip|空欄||
|resource-pack-prompt|空欄||
|rcon.port|25575||
|gamemode|survival|ゲームモードの設定。survival, creative, adventure, spectator|
|server-port|25565|サーバーが使用するポート|
|allow-nether|true|ネザーを有効にするか|
|enable-command-block|false|コマンドブロックを有効にするか|
|enable-rcon|false||
|sync-chunk-writes|true||
|enable-query|false||
|op-permission-level|4|OPユーザーが使用できるコマンドのレベル。1-4の整数|
|prevent-proxy-connections|false||
|resource-pack|空欄||
|entity-broadcast-range-percentage|100||
|level-name|world|使用するワールドのディレクトリ名|
|rcon.password|空欄||
|player-idle-timeout|0||
|motd|A Minecraft Server|ゲーム内でのサーバーリストに表示されるメッセージ。|
|query.port|25565||
|force-gamemode|false||
|rate-limit|0||
|hardcore|false|ハードコアを有効にするか|
|white-list|false|ホワイトリストを有効にするか|
|broadcast-console-to-ops|true||
|pvp|true|PvPを有効にするか|
|spawn-npcs|true|NPCのスポーンを有効にするか|
|spawn-animals|true|動物のスポーンを有効にするか|
|snooper-enabled|true|スポナーを有効にするか|
|difficulty|easy|難易度の設定。peaceful, easy, normal, hard|
|function-permission-level|2||
|network-compression-threshold|256||
|text-filtering-config|空欄||
|require-resource-pack|false||
|spawn-monsters|true|モンスターのスポーンを有効にするか|
|max-tick-time|60000||
|enforce-whitelist|false||
|use-native-transport|true||
|max-players|20|接続できるプレイヤー数|
|resource-pack-sha1|空欄||
|spawn-protection|16|スポーン地点の保護の範囲。|
|online-mode|true|オンラインモードを有効にするか|
|enable-status|true||
|allow-flight|false||
|max-world-size|29999984||