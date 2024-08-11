---
title: 设置git提交使用不同用户名和邮箱
tags:
  - git
date: 2024-02-28 23:43:46
updated: 2024-02-28 23:43:46
---


# 应用场景

在公司项目中使用真实姓名和工作邮箱，在同一台电脑上向Github等公开仓库提交代码时使用其他昵称/邮箱。

# 设置方法

1. 全局设置

```shell
git config --global user.name xxxx
git config --global user.email xxxx@xxxx.com
```

2. 对本地git仓库单独设置用户名和邮箱
   
```shell
# 切换到本地git仓库地址后执行
git config user.name yyyy
git config user.email yyyy@yyyy.com
```

# 查看生效结果

可以通过查看本地仓库.git/config文件，检查用户名、邮箱配置

```
[user]
        name = xxxx
        email = xxxx@xxxx.com
```