---
layout:     post
title:      卸载JDK（Mac系统环境）
subtitle:   卸载JDK（Mac系统环境）
date:       2022-03-17
author:     skyunique
header-img: img/post-bg-os-metro.jpg
catalog: 	 true
tags:
    - MACOS
    - CENTOS7
---

# 正文

卸载JDK（Mac系统环境）

```
sudo rm -fr /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin 

sudo rm -fr /Library/PreferencesPanes/JavaControlPanel.prefpane

ls /Library/Java/JavaVirtualMachines/

sudo rm -rf /Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk
```

