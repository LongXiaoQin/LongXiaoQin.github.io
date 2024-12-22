---
title: Activate
author: Jean
date: 2024-12-18
category: Tools
layout: post
---

> ##### DANGER
>
> 仅作个人学习记录，禁止用于商业用途.
{: .block-danger }

Typora
-------------

[参考文章]: https://blog.csdn.net/a79998/article/details/138564412

### 1.官网下载

`https://typoraio.cn/`

### 2.修改文件

- 打开/Applications/Typora.app/Contents/Resources/TypeMark/page-dist/static/LicenseIndex.XXXXX.chunk.js，做以下修改

修改前：

```javascript
e.hasActivated="true"==e.hasActivated
```

修改后：

```javascript
e.hasActivated="true"=="true"
```

- 打开/Applications/Typora.app/Contents/Resources/zh-Hans.lproj，做以下修改

修改前：

```javascript
"UNREGISTERED" = "未激活"
```

修改后：

```javascript
"UNREGISTERED" = ""
```

Jetbrains
-------------

[参考文章]: https://www.nowcoder.com/discuss/353157864313266176

### 1.适用范围

JetBrains 全系列产品 2018、2019及2020.1.1之前的版本

### 2.官网下载

[IDEA](https://www.jetbrains.com/zh-cn/idea/download/other.html)

[PyCharm](https://www.jetbrains.com/zh-cn/pycharm/download/other.html)

[WebStorm](https://www.jetbrains.com/zh-cn/webstorm/download/other.html)

### 3.脚本下载

百度网盘地址：`https://pan.baidu.com/s/1zgKIOxyGMy1anL3T_dIeSw`

密码：`2nr4`

### 4.破解步骤

- 将 jetbrains-agent-latest 文件夹中的破解补丁 jetbrains-agent.jar 拖入 IDEA 界面中

- 将文件夹中的ACTIVATION_CODE.txt粘贴至激活界面