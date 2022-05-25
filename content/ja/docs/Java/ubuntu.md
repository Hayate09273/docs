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
このコマンドを実行すると、Java 17がインストールされます。
```bash
$ sudo apt update

$ sudo apt install openjdk-17-jre -y
```

古いバージョンのJavaを使用したい場合は、「17」の部分を他の数字に置き換えてください。
```bash
$ sudo apt install openjdk-11-jre -y
```
```bash
$ sudo apt install openjdk-8-jre -y
```
## バージョンを確認
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。  
ダブルクオーテーションで囲まれた部分がバージョンです。
```bash
$ java -version

openjdk version "17.0.3" 2022-04-19
OpenJDK Runtime Environment (build 17.0.3+7-Ubuntu-0ubuntu0.22.04.1)
OpenJDK 64-Bit Server VM (build 17.0.3+7-Ubuntu-0ubuntu0.22.04.1, mixed mode, sharing)
```