---
title: "バージョンの選び方"
date: 2021-08-16T18:23:15+09:00
draft: false
description: Javaバージョンの選び方の解説
---

## バージョンの選び方
2021年8月現在、サポートされているJavaのバージョンは、8、11、16の3つです。  

{{% alert title="Info" %}} 次期バージョンのJava 17は2021年9月にリリースされる予定です。 {{% /alert %}}

Minecraft Java Edition 1.17ではJava 16以降が必要なので、Minecraft Java Edition 1.17以降のサーバーが必要な場合、Java 16をインストールする必要があります。  

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

## 参考にしたサイト
[Java - Wikipedia](https://ja.wikipedia.org/wiki/Java)

[Javaバージョン履歴 - Wikipedia](https://ja.wikipedia.org/wiki/Java%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E5%B1%A5%E6%AD%B4)
