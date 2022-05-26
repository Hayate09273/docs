---
title: "NFSが原因でLuckPermsが動かなかった話"
date: 2021-08-19T00:29:16+09:00
draft: false
description: NFSが原因でLuckPermsが動かなかったので、解決方法などを書きました。
---

## 症状
+ Spigot起動時に「Could not load 'plugins/LuckPerms-Bukkit-5.3.47.jar' in folder 'plugins'」というエラーが出る。
+ pluginsディレクトリ内にLuckPermsディレクトリが生成されない。

## 発生した環境
+ さくらのVPS V5 4Gプラン
+ Ubuntu 20.04 LTS
+ オプションの追加ストレージ(NFS)を使用

## 原因
NFSを/mntディレクトリにマウントしていたから。

## 解決方法
/mntディレクトリではない場所にNFSをマウントするようにすることで解決しました。  
ここでは、/home/ubuntu/nfsにマウントするように変更しました。
```bash
$ sudo unmount /mnt
$ sudo mount -t nfs 192.168.1.2:/export /home/ubuntu/nfs

$ sudo crontab -e
@reboot mount -t nfs 192.168.1.2:/export /home/ubuntu/nfs
```

## エラーログ
```bash
[16:26:32] [Server thread/ERROR]: Could not load 'plugins/LuckPerms-Bukkit-5.3.47.jar' in folder 'plugins'
org.bukkit.plugin.InvalidPluginException: me.lucko.luckperms.common.loader.LoadingException: Unable to create a temporary file
	at org.bukkit.plugin.java.JavaPluginLoader.loadPlugin(JavaPluginLoader.java:133) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at org.bukkit.plugin.SimplePluginManager.loadPlugin(SimplePluginManager.java:329) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at org.bukkit.plugin.SimplePluginManager.loadPlugins(SimplePluginManager.java:251) [spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at org.bukkit.craftbukkit.v1_11_R1.CraftServer.loadPlugins(CraftServer.java:301) [spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at net.minecraft.server.v1_11_R1.DedicatedServer.init(DedicatedServer.java:204) [spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at net.minecraft.server.v1_11_R1.MinecraftServer.run(MinecraftServer.java:544) [spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at java.base/java.lang.Thread.run(Thread.java:831) [?:?]
Caused by: me.lucko.luckperms.common.loader.LoadingException: Unable to create a temporary file
	at me.lucko.luckperms.common.loader.JarInJarClassLoader.extractJar(JarInJarClassLoader.java:135) ~[?:?]
	at me.lucko.luckperms.common.loader.JarInJarClassLoader.<init>(JarInJarClassLoader.java:61) ~[?:?]
	at me.lucko.luckperms.bukkit.loader.BukkitLoaderPlugin.<init>(BukkitLoaderPlugin.java:40) ~[?:?]
	at java.base/jdk.internal.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method) ~[?:?]
	at java.base/jdk.internal.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:78) ~[?:?]
	at java.base/jdk.internal.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45) ~[?:?]
	at java.base/java.lang.reflect.Constructor.newInstanceWithCaller(Constructor.java:499) ~[?:?]
	at java.base/java.lang.reflect.ReflectAccess.newInstance(ReflectAccess.java:128) ~[?:?]
	at java.base/jdk.internal.reflect.ReflectionFactory.newInstance(ReflectionFactory.java:350) ~[?:?]
	at java.base/java.lang.Class.newInstance(Class.java:642) ~[?:?]
	at org.bukkit.plugin.java.PluginClassLoader.<init>(PluginClassLoader.java:76) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at org.bukkit.plugin.java.JavaPluginLoader.loadPlugin(JavaPluginLoader.java:129) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	... 6 more
Caused by: java.nio.file.AccessDeniedException: /tmp/luckperms-jarinjar7200033458096106022.jar.tmp
	at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:90) ~[?:?]
	at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:106) ~[?:?]
	at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111) ~[?:?]
	at java.base/sun.nio.fs.UnixFileSystemProvider.newByteChannel(UnixFileSystemProvider.java:219) ~[?:?]
	at java.base/java.nio.file.Files.newByteChannel(Files.java:375) ~[?:?]
	at java.base/java.nio.file.Files.createFile(Files.java:652) ~[?:?]
	at java.base/java.nio.file.TempFileHelper.create(TempFileHelper.java:135) ~[?:?]
	at java.base/java.nio.file.TempFileHelper.createTempFile(TempFileHelper.java:158) ~[?:?]
	at java.base/java.nio.file.Files.createTempFile(Files.java:917) ~[?:?]
	at me.lucko.luckperms.common.loader.JarInJarClassLoader.extractJar(JarInJarClassLoader.java:133) ~[?:?]
	at me.lucko.luckperms.common.loader.JarInJarClassLoader.<init>(JarInJarClassLoader.java:61) ~[?:?]
	at me.lucko.luckperms.bukkit.loader.BukkitLoaderPlugin.<init>(BukkitLoaderPlugin.java:40) ~[?:?]
	at java.base/jdk.internal.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method) ~[?:?]
	at java.base/jdk.internal.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:78) ~[?:?]
	at java.base/jdk.internal.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45) ~[?:?]
	at java.base/java.lang.reflect.Constructor.newInstanceWithCaller(Constructor.java:499) ~[?:?]
	at java.base/java.lang.reflect.ReflectAccess.newInstance(ReflectAccess.java:128) ~[?:?]
	at java.base/jdk.internal.reflect.ReflectionFactory.newInstance(ReflectionFactory.java:350) ~[?:?]
	at java.base/java.lang.Class.newInstance(Class.java:642) ~[?:?]
	at org.bukkit.plugin.java.PluginClassLoader.<init>(PluginClassLoader.java:76) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	at org.bukkit.plugin.java.JavaPluginLoader.loadPlugin(JavaPluginLoader.java:129) ~[spigot-1.11.2.jar:git-Spigot-3fb9445-6e3cec8]
	... 6 more
```

## 参考にしたサイト
+ [追加ストレージ（NFS） | さくらの VPS マニュアル](https://manual.sakura.ad.jp/vps/support/technical/nfs.html)  
+ [さくらのVPSで追加ストレージ(NFS)を利用してみた - saitodev.co](https://saitodev.co/article/%E3%81%95%E3%81%8F%E3%82%89%E3%81%AEVPS%E3%81%A7%E8%BF%BD%E5%8A%A0%E3%82%B9%E3%83%88%E3%83%AC%E3%83%BC%E3%82%B8%28NFS%29%E3%82%92%E5%88%A9%E7%94%A8%E3%81%97%E3%81%A6%E3%81%BF%E3%81%9F/)