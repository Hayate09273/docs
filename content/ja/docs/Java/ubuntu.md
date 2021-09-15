---
title: "Ubuntu"
date: 2021-08-16T18:21:10+09:00
draft: false
description: UbuntuにJavaをインストールする方法
weight: 1
---

このページでは、UbuntuにJavaをインストールする方法について解説していきます。

Ubuntuの場合は、aptを使用してインストールするのが良いと思います。  
このコマンドを実行すると、Java 16がインストールされます。
```bash
$ sudo apt update

$ sudo apt install openjdk-16-jre -y
```
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。
```bash
$ java -version

openjdk version "16.0.1" 2021-04-20
OpenJDK Runtime Environment (build 16.0.1+9-Ubuntu-120.04)
OpenJDK 64-Bit Server VM (build 16.0.1+9-Ubuntu-120.04, mixed mode, sharing)
```