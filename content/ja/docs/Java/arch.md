---
title: "Arch Linux"
date: 2021-09-17T17:34:33+09:00
draft: false
description: Arch LinuxにJavaをインストールする方法
---

## インストール
Arch Linuxの場合は、pacmanを使用してインストールするのが良いと思います。
Arch Linuxは、Java 7、8、11、16を公式でサポートしています。  
このコマンドを実行すると、最新のJavaがインストールされます。
2021年9月17日現在では、Java 16がインストールされました。
```bash
$ sudo pacman -S jre-openjdk
```

古いバージョンのJavaを使用したい場合は、「jre」の部分を「jre11」などに変更してください。
```bash
$ sudo pacman -S jre11-openjdk
```
```bash
$ sudo pacman -S jre8-openjdk
```
## バージョンを確認
「java -version」でバージョンを確認します。このように表示されたらインストール完了です。  
ダブルクオーテーションで囲まれた部分がバージョンになります。これはインストール時期によって違うかもしれません。
```bash
openjdk version "16.0.2" 2021-07-20
OpenJDK Runtime Environment (build 16.0.2+7)
OpenJDK 64-Bit Server VM (build 16.0.2+7, mixed mode)
```

## 参考にしたサイト
[Java - ArchWiki](https://wiki.archlinux.org/title/Java)