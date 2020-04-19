---
title: "Hadoop Cluster 測試 – HDFS"
date: 2019-04-17
image_webp: 
image: /images/blog/HDFS/1.png
author: stemlab
---

在各 Node 上，必須先確認其 IP 與 hostname

可下指令修改 hostname

```
sudo hostnamectl set-hostname vm1
```

再利用指令尋找 Node 的 IP

```
ip addr
```

![](/images/blog/HDFS/1.png)

如下圖已修改 hostname 為 vm1，且得知 IP 為 192.168.56.102

將 IP 位置與命名加入各 node 的 /etc/hosts 檔案中

![](/images/blog/HDFS/2.png)

在各個 node 加入名為 hadoop 的使用者，並設定密碼

```
sudo -u root useradd hadoop
sudo -u root passwd hadoop
```

以 hadoop 使用者登入主要的 node，並建立 ssh key

```
ssh-keygen -t rsa (一路 ENTER 下去）
```

再把 ssh key 送到各個 node 上

```
ssh-copy-id hadoop@vm0
ssh-copy-id hadoop@vm1
```

![](/images/blog/HDFS/3.png)

用 hadoop ssh 登入 vm0，並下載 hadoop，解壓，與重新命名 binary： http://ftp.tc.edu.tw/pub/Apache/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz

```
wget http://ftp.tc.edu.tw/pub/Apache/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz
tar -xzf hadoop-3.1.2.tar.gz
mv hadoop-3.1.2 hadoop
```

![](/images/blog/HDFS/4.png)

調整 JAVA_HOME 至 /usr/lib/jvm/jre

```
vi hadoop/etc/hadoop/hadoop-env.sh
```

![](/images/blog/HDFS/5.png)

在各 Node 設定 NameNode （~/hadoop/etc/hadoop/core-site.xml)

```
vi ~/hadoop/etc/hadoop/core-site.xml
```

![](/images/blog/HDFS/6.png)

同樣的，設定 HDFS Path

![](/images/blog/HDFS/7.png)

設定 yarn

```
vi ~/hadoop/etc/hadoop/mapred-site.xml
```

![](/images/blog/HDFS/8.png)

```
vi ~/hadoop/etc/hadoop/yarn-site.xml
```

![](/images/blog/HDFS/9.png)

設定 workers

```
vi ~/hadoop/etc/hadoop/workers
```

![](/images/blog/HDFS/10.png)

設定記憶體相關（DEFAULT 值給 8G RAM 用的）

```
vi ~/hadoop/etc/hadoop/yarn-site.xml
```

![](/images/blog/HDFS/11.png)

```
vi ~/hadoop/etc/hadoop/mapred-site.xml
```

![](/images/blog/HDFS/12.png)

致此，設定完成

將相關的設定檔案 COPY 至每個 Node

```
scp hadoop-*.tar.gz vm1:/home/hadoop
```

![](/images/blog/HDFS/13.png)

SSH 連進 Node

```
ssh vm1
```

![](/images/blog/HDFS/14.png)


解壓，重命名，然後離開

```
tar -xzf hadoop-3.1.2.tar.gz
mv hadoop-2.8.1 hadoop
exit
```

![](/images/blog/HDFS/15.png)

```
for node in node1 node2; do
scp ~/hadoop/etc/hadoop/* $node:/home/hadoop/hadoop/etc/hadoop/;
done
```

![](/images/blog/HDFS/16.png)

格式化 HDFS (在 vm0 上） hadoop/bin/hdfs namenode -format

![](/images/blog/HDFS/17.png)

然後啟動 HDFS

```
hadoop/sbin/start-dfs.sh
```

![](/images/blog/HDFS/18.png)

可連上網頁觀看 http://vm0:9870

![](/images/blog/HDFS/19.png)

此至，HDFS 設定完成