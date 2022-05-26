---
title: "CentOS Stream 8にBungeeCordを構築"
linktitle: "CentOS Stream 8"
date: 2021-10-06T22:31:40+09:00
draft: false
description: CentOS Stream 8にBungeeCordを構築する方法
weight: 25
---

## BungeeCordをダウンロード
まず、BungeeCord用のディレクトリを作成し、そのディレクトリに移動します。  
名前はわかりやすいものにしておくと良いと思います。
```bash
$ mkdir BungeeCord && cd BungeeCord
```
BungeeCord.jarをダウンロードします。
```bash
$ wget https://ci.md-5.net/job/BungeeCord/lastSuccessfulBuild/artifact/bootstrap/target/BungeeCord.jar
```
lsコマンドでBungeeCord.jarが存在することを確認しておきます。
```bash
$ ls
BungeeCord.jar
```
## BungeeCordを実行する
まず、BungeeCordを実行するためのスクリプトを作成し、お好きなエディタで編集します。
```bash
$ nano start.sh
```
下の内容をstart.shに書き込みます。
```bash
#!/bin/bash
java -Xms512M -Xmx512M -jar BungeeCord.jar
```
所有者にstart.shを実行する権限を与えます。
```bash
$ chmod 700 start.sh
```
実行します。
```bash
$ ./start.sh
```
画面にログが流れ、最後がこのような文で終わっていたら成功です！
```bash
[INFO] Listening on /0.0.0.0:25577
```
BungeeCordを終了する場合は、「end」と入力してください。
```bash
>end
```
## 参考にしたサイト

[BungeeCord Installation | SpigotMC - High Performance Minecraft](https://www.spigotmc.org/wiki/bungeecord-installation)