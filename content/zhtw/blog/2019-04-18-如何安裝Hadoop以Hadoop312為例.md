---
title: "如何安裝 Hadoop – 以 Hadoop3.1.2 為例"
date: 2019-04-18
image_webp: 
image: /images/blog/full-logo.png
author: stemlab
---
安裝好 Fedora 後（詳見這篇），接著要安裝 Hadoop

首先，連到網頁下載 Hadoop binary 的網址

在 fedora 下指令：

```
wget http://apache.stu.edu.tw/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz
```

等待下載完成

![](/images/blog/Hadoop/1.png)

並解壓縮：

```
tar vzxf hadoop-3.1.2.tar.gz
```

然後參考 https://hadoop.apache.org/docs/r3.1.2/hadoop-project-dist/hadoop-common/SingleCluster.html

進行設定與操作

安裝 JAVA

```
sudo dnf install java-11-openjdk
```

設定 PATH

![](/images/blog/Hadoop/2.png)

在下指令：

```
bin/hadoop
```

來確認可以使用

![](/images/blog/Hadoop/3.png)