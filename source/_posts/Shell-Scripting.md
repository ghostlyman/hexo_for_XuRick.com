---
title: Shell Scripting
date: 2016-11-04 20:28:05
tags: [Shell, Linux]
---

Reference to 
[shiyanlou](https://www.shiyanlou.com/courses/5/labs/26/document)

<!-- more -->

# Shell Scripting tutorial

---
[TOC]

## 1. Bash 介绍与入门

--- 

### 简介
* Bash（GNU Bourne-Again Shell）是一个为GNU计划编写的Unix shell，它是许多Linux平台默认使用的shell。

* shell是一个命令解释器，是介于操作系统内核与用户之间的一个绝缘层。准确地说，它也是能力很强的计算机语言，被称为解释性语言或脚本语言。

* 事实上，所有的UNIX命令和工具再加上公共程序，对于shell脚本来说，都是可调用的

---

#### Hello World 
* 创建Hello World 脚本
```shell
$ vim hello.sh
>>>
#!/bin/bash
# This is the comment
echo Hello World
```
--- 

* 执行bash 脚本
```shell
$ sh hello.sh
>>>
$ bash hello.sh
>>>
```

---
 
* 添加可执行权限
```
$ chmod +x hello.sh
>>>
$ ./hello.sh
```

--- 

#### 使用脚本清除/var/log下的log文件
```shell
$ vim cleanlogs.sh
>>>
#!/bin/bash
# Initiling a variable
LOG_DIR=/var/log
cd $LOG_DIR

cat /dev/null > messages
cat /dev/null > wtmp

echo "Great, the logs have been cleaned up."
exit
```
---








