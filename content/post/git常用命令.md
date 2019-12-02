---
title: git常用命令
date: 2019-11-29 16:33:37
draft: false
tags: ["git", "linux"]
---
* 暂存区文件的撤消 
```shell
git reset HEAD ... 
```

* 撤消文件修改 
```shell
git checkout ...
```

* 添加子项目
```shell
git submodule add 地址 模块名称
```

* 删除子项目
```shell
git rm --cached path_to_submodule
```