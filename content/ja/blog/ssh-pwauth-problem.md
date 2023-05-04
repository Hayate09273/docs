---
title: "sshd_configのPasswordAuthentication noが効かないときの対処法"
date: 2023-04-30T00:40:50+09:00
draft: false
description: 
---

## 対処法
**/etc/ssh/sshd_config.d/50-cloud-init.conf** をテキストエディタで開き、  
「PasswordAuthentication yes」と書いてあるのでコメントアウトする。

## 症状
sshd_configのPasswordAuthenticationをnoにしても何故かパスワード認証で接続できてしまう。
再読み込み、再起動等行っても直らず。

## 発生した環境
+ Ubuntu Server 22.04.3 (新規インストール直後)
+ OpenSSH ServerはOSインストール時に一緒にインストールした