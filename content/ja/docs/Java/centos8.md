---
title: "CentOS Stream 8にJavaをインストール"
linktitle: "CentOS Stream 8"
date: 2021-09-21T19:50:16+09:00
draft: false
description: CentOS Stream 8にJavaをインストールする方法
---

## インストール
CentOS Stream 8の場合は、dnfを使用してインストールするのが良いと思います。  
このコマンドを実行すると、Java 17がインストールされます。
```bash
$ sudo dnf install java-17-openjdk -y
```

古いバージョンのJavaを使用したい場合は、「17」の部分を他の数字に置き換えてください。
```bash
$ sudo dnf install java-11-openjdk -y
```
```bash
$ sudo dnf install java-1.8.0-openjdk -y
```

## バージョンを確認
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。  
ダブルクオーテーションで囲まれた部分がバージョンです。
```bash
$ java -version
openjdk version "17-ea" 2021-09-14
OpenJDK Runtime Environment 21.9 (build 17-ea+33)
OpenJDK 64-Bit Server VM 21.9 (build 17-ea+33, mixed mode, sharing)
```