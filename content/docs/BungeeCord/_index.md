---
title: "BungeeCord"
date: 2021-07-13T19:50:31+09:00
draft: false
github_url: "https://github.com/Hayate09273/docs_content/edit/main/docs/BungeeCord/index.md"
description: BungeeCordの構築方法
---

このページでは、BungeeCordを構築する方法について説明していきます。  
Javaがインストール済みであることが前提です。
Javaのインストール方法は[こちら](/docs/java/)

## Linux

### BungeeCordをダウンロード
まず、BungeeCord用のディレクトリを作成し、そのディレクトリに移動します。
```bash
mkdir BungeeCord && cd BungeeCord
```
BungeeCord.jarをダウンロードします。
```bash
wget https://ci.md-5.net/job/BungeeCord/lastSuccessfulBuild/artifact/bootstrap/target/BungeeCord.jar
```
lsコマンドでBungeeCord.jarが存在することを確認しておきます。
```bash
ls
BungeeCord.jar
```
### BungeeCordを実行する
まず、BungeeCordを実行するためのスクリプトを作成し、お好きなエディタで編集します。
ここでは、start.shを作成し、vimで編集します。
```bash
touch start.sh && vim start.sh
```

```bash
#!/bin/sh
java -Xms512M -Xmx512M -jar BungeeCord.jar
```
所有者を設定して、所有者にstart.shを実行する権限を与えます。
ここでは、所有者のユーザー名をubuntuとします。
```bash
chown ubuntu start.sh
chmod 700 start.sh
```
実行します。
```bash
./start.sh
```
画面にログが流れ、最後がこのような文で終わっていたら成功です！
```bash
[INFO] Listening on /0.0.0.0:25577
```
## 参考にしたサイト
https://ja.wikipedia.org/wiki/Java%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E5%B1%A5%E6%AD%B4
https://www.spigotmc.org/wiki/bungeecord-installation/