---
layout:     post
title:      Mac 使用SVN
subtitle:   SVN 使用
date:       2022-04-18
author:     skyunique
header-img: img/post-bg-os-metro.jpg
catalog:    true
tags:
    - MACOS
    - SVN
---


# 前言

##  Mac 使用SVN

# 正文
    > Mac 使用SVN
- 初始化本地项目到SVN 

  ```
  svn import /Users/...(项目路径) svn://localhost/...(svn地址) --username='用户名' --password=密码 -m "初始化导入"
  ```

- 拉取项目代码到本地

  ```
  svn checkout svn://localhost/mycode --username='账户' --password='密码' /Users/....(本地路径)
  ```

- 提交更改过的代码到服务器

  ```
  # 进入项目路径
  # 终端命令,讲所有修改提交到服务器
  svn commit -m "备注说明"
  ```

- 更新服务器端的代码到本地

  ```
  svn update
  ```

  

