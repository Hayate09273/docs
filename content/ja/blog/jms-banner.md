---
title: "Japan Minecraft ServersのバナーをMarkdownで埋め込む"
date: 2021-09-18T23:43:56+09:00
draft: false
description:
---
## 導入
Japan Minecraft Serversは、Minecraftでマルチプレイを楽しんでいる人が一度は見たことがあると思います。  
Japan Minecraft Serversにはバナーという機能があり、これをWebサイトに埋め込むことで、現在のオンラインプレイヤー数やIPアドレスをお洒落に表示されることができます。

サーバーのページに飛び、「バナー」タブをクリックして、バナータイプを選択します。  
するとこのようなHTMLのコードが生成されます。
```html
<a href="リンク"><img src="画像リンク"/></a>
```
## Markdown
これをMarkdownで表示させるには、このようにします。
```md
[![](画像リンク)](リンク)
```