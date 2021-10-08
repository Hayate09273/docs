---
title: "WindowsにSpigotサーバーを構築"
linktitle: "Windows"
date: 2021-10-07T19:42:59+09:00
draft: false
description: WindowsにSpigotサーバーを構築する方法
weight: 40
---

## 拡張子を表示
Windowsでは、拡張子をデフォルトで表示しない設定になっています。  
エクスプローラーを開き、上部にある「表示」タブの、「ファイル名拡張子」にチェックを入れてください。

## Gitをインストール
Spigotサーバーを構築するには、ビルドという工程を踏む必要があります。 ビルドをするためにはGit for Windowsが必要なので、[こちら](https://gitforwindows.org/)のサイトからダウンロードします。

1. Downloadボタンをクリックして、インストーラーをダウンロードします。
2. ダウンロードしたインストーラーを実行します。ユーザーアカウント制御の確認ダイアログが表示されたら、はいを押してください。
3. 重要なことが書いてあるらしいです。Nextを押します。  
![Git](/images/git_win_install1.png)
4. インストール先を選択します。デフォルトの場所でOKならNext、変更したい場合はBrowseを押してインストール先を選択してください。  
![Git](/images/git_win_install2.png)
5. インストールするコンポーネントを選択する画面です。デフォルトで大丈夫なのでNextを押してください。  
![Git](/images/git_win_install3.png)
6. スタートメニューにフォルダーを作成するかの画面です。デフォルトで大丈夫だと思いますので、Nextを押してください。  
![Git](/images/git_win_install4.png)
7. Gitで使用するエディタを選択する画面です。デフォルトの**Vim**で大丈夫であれば、Nextを押してください。  
![Git](/images/git_win_install5.png)
8. デフォルトのブランチ名を選択する画面です。デフォルトの「**Let Git decide**」で大丈夫だと思いますので、Nextを押してください。  
![Git](/images/git_win_install6.png)
9. コマンドプロンプトやPowerShellでGitが使えるようにするかを選択する画面です。デフォルトの「**Git from the command line and also from 3rd-party software**」で大丈夫なのでNextを押してください。  
![Git](/images/git_win_install7.png)
10. Gitが使用するSSHを選択する画面です。デフォルトの「**Use bundled OpenSSH**」で大丈夫なのでNextを押してください。  
![Git](/images/git_win_install8.png)
11. GitがHTTPS接続に使用するSSLライブラリを選択する画面です。デフォルトの「**Use the OpenSSL library**」で大丈夫なのでNextを押してください。  
![Git](/images/git_win_install9.png)
12. 改行コードの設定です。一応「**Checkout as-is, commit Unix-style line endings**」に変更してNextを押してください。  
![Git](/images/git_win_install10.png)
13. Gitで使用する端末エミュレータを選択する画面です。デフォルトの「**Use MinTTY**」で大丈夫なので、Nextを押してください。 
![Git](/images/git_win_install11.png)
14. 「git pull」を実行したときの動作を選択する画面です。デフォルトの「**Default (fast-forward or merge)**」で大丈夫であれば、Nextを押してください。  
![Git](/images/git_win_install12.png)
15. 認証関係の設定画面です。デフォルトの「**Git Credential Manager Core**」で大丈夫なので、Nextを押してください。  
![Git](/images/git_win_install13.png)
16. オプションの機能の設定画面です。デフォルトで大丈夫だと思いますので、Nextを押してください。  
![Git](/images/git_win_install14.png)
17. こちらもオプションの機能の設定画面です。デフォルトのどちらにもチェックが入っていない状態で大丈夫だと思います。**Install**をクリックすると、インストールが始まります。  
![Git](/images/git_win_install15.png)
18. インストールが完了するとこちらの画面が表示されます。チェックボックスは外して**Finish**を押してください。  
![Git](/images/git_win_install16.png)

## BuildToolsをダウンロード
1. まず、サーバーのファイルを保管するためのフォルダを好きな場所に作成してください。
2. [こちら](https://hub.spigotmc.org/jenkins/job/BuildTools/)のサイトからBuildToolsをダウンロードします。画面中央の「最新成功ビルドの成果物」の下の「BuildTools.jar」をクリックしてください。  
3. 先ほど作成したフォルダの中にBuildTools.jarを保存してください。
## ビルドする
1. 先ほど作成したフォルダをエクスプローラーで開き、ファイルが表示される場所のなにもないところを右クリックし、「Git Bash Here」をクリックします。  
2. このコマンドを実行すると、最新バージョンのSpigotのビルドが始まります。  
少し時間がかかりますので、気長に待ちましょう。
```bash
$ java -jar BuildTools.jar
```
### バージョンを指定する方法
上のコマンドの末尾に、「–rev」を追加することで、バージョンを指定できます。  
例えば、1.16.5のSpigotをビルドしたい場合は、このコマンドを実行します。
```bash
$ java -jar BuildTools.jar --rev 1.16.5
```
## サーバーを実行する
### スタートスクリプトを作成  
spigot-1.xx.x.jarと同じフォルダ内に、スタートスクリプトを作成します。  
名前は「start.bat」など分かりやすいものにしておくと良いと思います。  
拡張子は、一度start.txtを作成してから、start.batに変更してください。
### 作成したスタートスクリプトを編集  
拡張子が.batの場合、ダブルクリックするとコマンドプロンプトが起動するので、編集する場合はstart.batを選択して右クリック→編集(E)をクリックしてください。
```bash
@ECHO OFF
java -Xms1G -Xmx1G -jar spigot-1.xx.x.jar nogui
PAUSE
```