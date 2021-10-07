---
title: "Windowsに公式サーバーを構築"
linktitle: "Windows"
date: 2021-09-11T22:24:43+09:00
draft: false
description: Windowsに公式サーバーを構築する方法
weight: 40
---

## 拡張子を表示
Windowsでは、拡張子をデフォルトで表示しない設定になっています。  
エクスプローラーを開き、上部にある「表示」タブの、「ファイル名拡張子」にチェックを入れてください。

## サーバーファイルのダウンロード
1. サーバーのファイルを保管するためのフォルダを好きな場所に作成してください。
2. Minecraft Launcherを開き、「起動構成」タブ、「New installation」をクリックします。
3. バージョンの欄でお好きなバージョンを選び、右上の「サーバー」をクリックします。
4. 1.で作成したフォルダの中にserver.jarを保存します。

|現在のフォルダの中身|
|---|
|server.jar|

## サーバーを実行
### スタートスクリプトを作成  
server.jarと同じフォルダ内に、スタートスクリプトを作成します。  
名前は「start.bat」など分かりやすいものに変更してください。  
拡張子は一度txtファイルを作成してから、batに変更してください。
### 作成したスタートスクリプトを編集  
拡張子が.batの場合、ダブルクリックするとコマンドプロンプトが起動するので、編集する場合はstart.batを選択して右クリック→編集(E)をクリックしてください。
```bash
@ECHO OFF
java -Xms1G -Xmx1G -jar server.jar nogui
PAUSE
```

|現在のフォルダの中身|
|---|
|server.jar|
|start.bat|
### start.batを実行  
start.batを実行してください。  
コマンドプロンプトが起動しますが、怖くありません。  
初回起動時には「You need to agree to the EULA in order to run the server. Go to eula.txt for more info.」という表示が出て、強制的に終了されます。  
これは、「EULAに同意してください」というメッセージです。  
EULAに同意するために、「eula.txt」を編集します。
eula=falseをeula=trueに変更し、保存します。

|現在のフォルダの中身|
|---|
|logs|
|eula.txt|
|server.jar|
|server.properties|
|start.bat|
### もう一度start.batを実行
もう一度start.batを実行します。  
設定が読み込まれ、ワールドが生成されます。「Done!」と表示されていたらOKです！

|現在のフォルダの中身|
|---|
|logs|
|world|
|banned-ips.json|
|banned-players.json|
|eula.txt|
|ops.json|
|server.jar|
|server.properties|
|start.bat|
|usercache.json|
|whitelist.json|
### サーバーを終了する
コンソールに「stop」と入力してEnterキーを押してください。  
データが保存された後、「続行するには何かキーを押してください」と表示されたら、何かキーを押してウインドウを閉じます。