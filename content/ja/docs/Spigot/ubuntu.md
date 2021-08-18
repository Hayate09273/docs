---
title: "Ubuntuに構築する"
date: 2021-08-18T23:40:32+09:00
draft: false
description: UbuntuにSpigotサーバーを構築する方法についての解説
---

```bash
sudo apt install git
```

```bash
mkdir spigot && cd spigot
```

```bash
wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
```

```bash
ls
BuildTools.jar
```

```bash
java -Xmx1G -jar BuildTools.jar
```

```bash
nano start.sh
```

```bash
#!/bin/bash
java -Xms1G -Xmx1G -jar spigot-1.17.1.jar nogui
```

```bash
./start.sh
```

```bash
nano eula.txt
```

```bash
./start.sh
```