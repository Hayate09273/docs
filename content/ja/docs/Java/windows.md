---
title: "WindowsにJavaをインストール"
linktitle: "Windows"
date: 2021-09-11T22:27:45+09:00
draft: false
description: WindowsにJavaをインストールする方法
---

## インストーラーのダウンロード
[Oracleの公式サイト](https://www.oracle.com/jp/java/technologies/javase-downloads.html)からJavaをダウンロードします。  
バージョンは8、11、17がありますが、Minecraft Java Edition 1.17ではJava 16以上が要件となっているので、17をお勧めします。  
**Java SE Development Kit 17.0.1 downloads**の下にある**Windows**タブをクリックし、**x64 Installer**の右にあるURLをクリックします。  
これでインストーラーがダウンロードできます。

## インストール
1. 先ほどダウンロードしたインストーラーを起動します。ユーザーアカウント制御の確認画面が表示されたら「はい」をクリックしてください。セットアップが始まります。
2. この画面では、次へをクリックしてください。  
![Javaのインストール画面1](/images/java_win_install1.png)
3. インストールフォルダを選択する画面です。このままで大丈夫であれば、次へをクリックするとインストールが始まります。  
![Javaのインストール画面2](/images/java_win_install2.png)
4. インストールが終了するとこの画面が表示されます。閉じるをクリックしてください。  
![Javaのインストール画面3](/images/java_win_install3.png)

## JavaのPATHの確認
1. スタートボタンを右クリックし、「Windows PowerShell(I)」をクリックします。
2. 「java -version」と入力してEnterキーを押します。
3. Javaのバージョンが表示されていたらOKです。
```powershell
PS C:\Users\user> java -version
java version "17.0.1" 2021-10-19 LTS
Java(TM) SE Runtime Environment (build 17.0.1+12-LTS-39)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.1+12-LTS-39, mixed mode, sharing)
```