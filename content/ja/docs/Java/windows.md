---
title: "Windowsにインストールする"
date: 2021-09-11T22:27:45+09:00
draft: false
description: WindowsにJavaをインストールする方法
---

### インストーラーのダウンロード
[Oracleの公式サイト](https://www.oracle.com/jp/java/technologies/javase-downloads.html)からJavaをダウンロードします。  
バージョンは8、11、16がありますが、Minecraft Java Edition 1.17ではJava 16が要件となっているので、16をお勧めします。  
「JDK Download」をクリックし、「Windows x64 Installer」の右にあるファイル名をクリックします。  
チェックボックスにチェックを入れて同意し、緑色のダウンロードボタンをクリックします。  

### インストール
先ほどダウンロードしたインストーラーを起動します。ユーザーアカウント制御の確認画面が表示されたら「はい」をクリックしてください。
セットアップが始まります。

「Java SE Development Kit 16.0.2のインストール・ウィザードへようこそ

このウィザードでは、Java SE Development Kit 16.0.2のインストール・プロセスを順を追って説明します。」  
この画面では次を選択します。


「プライベートJREおよびsrc.zipを含むJava(TM) SE Development Kit 16.0.2 (64-bit)。
ハードドライブに420MBが必要です。インストール・フォルダを変更するには、『変更』ボタンをクリックします。」  
この画面では、インストールフォルダを変更しない場合は次を選択します。

コンピューターにJavaがインストールされるので、少し待ちます。

「Java(TM) SE Development Kit 16.0.2 (64-bit)が正常にインストールされました」  
この画面が表示されたら、閉じるを選択して終了します。

### JavaのPATHの確認
1. スタートボタンを右クリックし、「Windows PowerShell(I)」をクリックします。
2. 「java -version」と入力してEnterキーを押します。
3. Javaのバージョンが表示されていたらOKです。