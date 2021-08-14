---
title: "バニラサーバー"
date: 2021-08-14T20:26:19+09:00
draft: false
description: バニラサーバーの構築方法
weight: 3
---

このページでは、バニラサーバーを構築する方法について説明していきます。  
Javaがインストール済みであることが前提です。
Javaのインストール方法は[こちら](/docs/java/)

## Linux

### サーバーのファイルをダウンロード
まず、サーバー用のディレクトリを作成し、そのディレクトリに移動します。
名前はわかりやすいものにしておくと良いと思います。
```bash
mkdir server && cd server
```
サーバーのファイルをダウンロードします。このURLは1.17.1のものです。
```bash
wget https://launcher.mojang.com/v1/objects/a16d67e5807f57fc4e550299cf20226194497dc2/server.jar
```
lsコマンドでserver.jarが存在することを確認しておきます。
```bash
ls
server.jar
```
### サーバーを実行する
まず、サーバーを実行するためのスクリプトを作成し、お好きなエディタで編集します。
ここでは、start.shを作成し、vimで編集します。
```bash
touch start.sh && vim start.sh
```
下の内容をstart.shに書き込みます。
vimの場合は、iキーを押して入力モードに変更し、入力が終わったらEscを押したあとに:wqと入力してEnterキーを押してください。
```bash
#!/bin/bash
java -Xmx1G -Xms1G -jar server.jar nogui
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
初回起動時はこのような表示が出て、強制的に終了されます。
```bash
[main/ERROR]: Failed to load properties from file: server.properties
[main/WARN]: Failed to load eula.txt
[main/INFO]: You need to agree to the EULA in order to run the server. Go to eula.txt for more info.
```
これは、「EULAに同意してください」というメッセージです。EULAに同意するために、server.jarやstart.shと同じ階層に生成された「eula.txt」を編集します。
```bash
vim eula.txt

#By changing the setting below to TRUE you are indicating your agreement to our EULA (https://account.mojang.com/documents/minecraft_eula).
#Sat Aug 14 21:23:03 JST 2021
eula=false
```
「eula=false」となっている部分を、「eula=true」に書き換えて、保存してください。

もう一度start.shを実行します。
```bash
./start.sh
```
設定が読み込まれ、ワールドが生成されます。  
Done!と表示されたら成功です！
```bash
[Server thread/INFO]: Done (62.449s)! For help, type "help"
```
サーバーを終了する場合は、「stop」と入力してEnterキーを押してください。