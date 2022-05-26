---
title: "UbuntuにSpigotサーバーを構築"
linktitle: "Ubuntu"
date: 2021-08-18T23:40:32+09:00
draft: false
description: UbuntuにSpigotサーバーを構築する方法
weight: 30
---

## Gitをインストール
Spigotサーバーを構築するには、ビルドという工程を踏む必要があります。
ビルドをするためにはGitが必要なので、このコマンドでインストールします。
```bash
$ sudo apt install git
```

## BuildToolsをダウンロード
まず、Spigotサーバー用のディレクトリを作成し、そのディレクトリに移動します。  
```bash
$ mkdir spigot && cd spigot
```
BuildToolsをダウンロードします。
```bash
$ wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
```
lsコマンドでBuildTools.jarが存在することを確認します。
```bash
$ ls
BuildTools.jar
```
## ビルドする
このコマンドを実行すると、最新バージョンのSpigotのビルドが始まります。  
少し時間がかかりますので、気長に待ちましょう。
```bash
$ java -jar BuildTools.jar
```
### バージョンを指定する方法
上のコマンドの末尾に、「--rev」を追加することで、バージョンを指定できます。  
例えば、1.16.5のSpigotをビルドしたい場合は、このコマンドを実行します。
```bash
$ java -jar BuildTools.jar --rev 1.16.5
```
|生成されるファイル|
|---|
|BuilData|
|BuildTools.log.txt|
|CraftBukkit|
|apache-maven-3.6.0|
|work|
|BuildTools.jar|
|Bukkit|
|Spigot|
|spigot-1.xx.x.jar|
## サーバーを実行する
まず、サーバーを実行するためのスクリプトを作成し、お好きなエディタで編集します。 ここでは、start.shを作成し、nanoで編集します。
```bash
$ nano start.sh
```
下の内容をstart.shに書き込みます。
```bash
#!/bin/bash
java -Xms1G -Xmx1G -jar spigot-1.17.1.jar nogui
```
所有者を設定して、所有者にstart.shを実行する権限を与えます。ここでは、所有者のユーザー名をubuntuとします。
```bash
$ chown ubuntu start.sh
$ chmod 700 start.sh
```
実行します。
```bash
$ ./start.sh
```
初回起動時はこのような表示が出て、強制的に終了されます。
```bash
[main/ERROR]: Failed to load properties from file: server.properties
[main/WARN]: Failed to load eula.txt
[main/INFO]: You need to agree to the EULA in order to run the server. Go to eula.txt for more info.
```
これは、「EULAに同意してください」というメッセージです。EULAに同意するために、「eula.txt」を編集します。
```bash
eula.txt

#By changing the setting below to TRUE you are indicating your agreement to our>
#Sun Aug 22 19:51:18 JST 2021
eula=false
```
「eula=false」となっている部分を、「eula=true」に書き換えて、保存してください。
もう一度start.shを実行します。
```bash
$ ./start.sh
```
設定が読み込まれ、ワールドが生成されます。
Done!と表示されたら成功です！
```bash
[Server thread/INFO]: Done (30.000s)! For help, type "help"
```
サーバーを終了する場合は、「stop」と入力してEnterキーを押してください。
```bash
>stop
```