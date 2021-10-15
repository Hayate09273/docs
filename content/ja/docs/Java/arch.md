---
title: "Arch LinuxにJavaをインストール"
linktitle: "Arch Linux"
date: 2021-09-17T17:34:33+09:00
draft: false
description: Arch LinuxにJavaをインストールする方法
---

## インストール
Arch Linuxの場合は、pacmanを使用してインストールするのが良いと思います。Arch Linuxは、Java 7、8、11、17を公式でサポートしています。  

このコマンドを実行すると、最新のJavaがインストールされます。
2021年10月15日現在では、Java 17がインストールされました。
```bash
# pacman -S jre-openjdk
```

古いバージョンのJavaを使用したい場合は、「jre」の部分を「jre11」などに変更してください。
```bash
# pacman -S jre11-openjdk
```
```bash
# pacman -S jre8-openjdk
```
## バージョンを確認
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。  
ダブルクオーテーションで囲まれた部分がバージョンです。
```bash
$ java -version

openjdk version "17" 2021-09-14
OpenJDK Runtime Environment (build 17+35)
OpenJDK 64-Bit Server VM (build 17+35, mixed mode)
```

## 参考にしたサイト
[Java - ArchWiki](https://wiki.archlinux.org/title/Java)