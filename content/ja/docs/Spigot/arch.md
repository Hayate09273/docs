---
title: "Arch LinuxにSpigotサーバーを構築"
linktitle: "Arch Linux"
date: 2021-10-01T21:39:48+09:00
draft: false
description: Arch LinuxにSpigotサーバーを構築する方法
---

## Gitをインストール
Spigotサーバーを構築するには、ビルドという工程を踏む必要があります。
ビルドをするためにはGitが必要なので、このコマンドでインストールします。
```bash
# pacman -S git
```

## BuildToolsをダウンロード
まず、Spigotサーバー用のディレクトリを作成し、そのディレクトリに移動します。  
```bash
$ mkdir spigot && cd spigot
```
BuildToolsをダウンロードします。
```bash
$ curl -O https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
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
まず、サーバーを実行するためのスクリプトを作成し、お好きなエディタで編集します。  
下の内容を先ほど作成したスクリプトに書き込みます。  
```bash
#!/bin/bash
java -Xms1G -Xmx1G -jar spigot-1.xx.x.jar nogui
```
所有者にスクリプトを実行する権限を与えます。
```bash
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
「stop」と入力するとサーバーが終了します。
```bash
>stop
```