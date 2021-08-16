---
title: "Ubuntuに構築する"
date: 2021-08-16T20:52:28+09:00
draft: false
description: UbuntuにBungeeCordを構築する方法についての解説
---

## BungeeCordをダウンロード
まず、BungeeCord用のディレクトリを作成し、そのディレクトリに移動します。  
名前はわかりやすいものにしておくと良いと思います。
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
## BungeeCordを実行する
まず、BungeeCordを実行するためのスクリプトを作成し、お好きなエディタで編集します。
ここでは、start.shを作成し、vimで編集します。
```bash
touch start.sh && vim start.sh
```
下の内容をstart.shに書き込みます。
vimの場合は、iキーを押して入力モードに変更し、入力が終わったらEscを押したあとに:wqと入力してEnterキーを押してください。
```bash
#!/bin/bash
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

[BungeeCord Installation | SpigotMC - High Performance Minecraft](https://www.spigotmc.org/wiki/bungeecord-installation)