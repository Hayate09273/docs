---
title: "Javaのインストール"
date: 2021-08-13T17:23:33+09:00
draft: false
description: Javaのインストール方法
weight: 2
---

このページでは、サーバーを動作させるために必要なJavaのインストール方法について説明していきます。

> Java（ジャバ、ジャヴァ）は、汎用プログラミング言語とソフトウェアプラットフォームの双方を指している総称ブランドである。  
> 出典: [Java - Wikipedia](https://ja.wikipedia.org/wiki/Java)

## Ubuntuにインストールする
Ubuntuの場合は、aptを使用してインストールするのが良いと思います。  
このコマンドの場合は、Java 16がインストールされます。
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


## Tip: バージョンの選び方
2021年8月現在、サポートされているJavaのバージョンは、8、11、16の3つです。

Minecraft Java Edition 1.17ではJava 16以降が必要であるため、Minecraft Java Edition 1.17以降のサーバーが必要な場合、Java 16をインストールする必要があります。  

基本はJava 16で、必要に迫られた時のみJava 8か11を使用すると良いと思います。

### JavaとMinecraftサーバーのバージョン別互換性
JavaとMinecraftサーバーのバージョン別互換性についていくつかの組み合わせで検証し、下の表にまとめました。  
Javaには後方互換性があるため、最新のJava 16で古いソフトウェアを動作させることも可能です。
||Java 8|Java 11|Java 16|
|-|-|-|-|
|公式 1.2.1~1.16.5|O|O|O|
|公式 1.17.1|X|X|O|
|Spigot 1.8.8~1.16.5|O|O|O|
|Spigot 1.17~|X|X|O|
|BungeeCord #1598|O|O|O|

### JavaとBuildToolsのバージョン別互換性
Spigotを使用する場合、どのJavaバージョンでどのMinecraftバージョンのビルドが可能かを確認しておくと良いと思います。  
「ビルドはできないけど、実行はできる」ということもありますので、少し注意が必要です。
こちらもいくつかの組み合わせで検証しました。

||Java 8|Java 11|Java 16|
|-|-|-|-|
|1.8.8|O|X|X|
|1.10.2|O|X|X|
|1.12.2|O|X|X|
|1.14.4|O|O|X|
|1.16.5|O|O|O|
|1.17.1|X|X|O|