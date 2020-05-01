---
title: "如何安裝 Linux 系統 – 以 Fedora 為例"
date: 2019-04-16
image: images/blog/Fedora/1.png
author: stemlab
---


首先，先到官網選擇適合的 ISO，本篇以 Fedora 29 Server 的 DVD ISO 為例

![](/images/blog/Fedora/1.png)

接著使用 VirtualBox 進行安裝與測試 使用 2G 的 ram 與 8G 的硬碟。

設定 Nat Network 後，進行連結與設定，放入先前抓下來的 ISO。按下 Start 即可開始安裝

![](/images/blog/Fedora/2.png)

選擇 「Install Fedora 29」

![](/images/blog/Fedora/3.png)

出現友善的安裝畫面，選擇 English，English (United States) –〉continue

![](/images/blog/Fedora/4.png)

調整 Installation Destination，選擇 Custom –〉Done

![](/images/blog/Fedora/5.png)

Standard Partition，/boot/swap 空間如圖設定（請盡量用 EXT4 格式）–〉Done –〉accept change –〉Begin installation

![](/images/blog/Fedora/6.png)

![](/images/blog/Fedora/7.png)

就開始裝了，要同時設定 root 密碼與建立使用者帳號，就等待安裝完成吧 –〉Reboot（記得把光碟退掉）

![](/images/blog/Fedora/8.png)

更新指令

```
sudo dnf update -y
```

等他完成，就可以開始使用啦！