---
title: "UbuntuにJavaをインストール"
linktitle: "Ubuntu"
date: 2021-08-16T18:21:10+09:00
draft: false
description: UbuntuにJavaをインストールする方法
weight: 1
---

## インストール

Ubuntuの場合は、aptを使用してインストールするのが良いと思います。  
このコマンドを実行すると、Java 16がインストールされます。
```bash
$ sudo apt update

$ sudo apt install openjdk-16-jre -y
```

古いバージョンのJavaを使用したい場合は、「16」の部分を他の数字に置き換えてください。
```bash
$ sudo apt install openjdk-11-jre -y
```
```bash
$ sudo apt install openjdk-8-jre -y
```
## バージョンを確認
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。  
ダブルクオーテーションで囲まれた部分がバージョンになります。これはインストール時期によって違うかもしれません。
```bash
$ java -version

openjdk version "16.0.1" 2021-04-20
OpenJDK Runtime Environment (build 16.0.1+9-Ubuntu-120.04)
OpenJDK 64-Bit Server VM (build 16.0.1+9-Ubuntu-120.04, mixed mode, sharing)
```