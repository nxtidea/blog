---
title: 怎样在Windows下使用zsh
summary: 怎样在 Windows 下使用 zsh。非 WSL 方案。
date: 2024-03-01
tags: ["工具使用", "Windows"]
draft: false
---
## Zsh 安装[^1]

[^1]: https://zhuanlan.zhihu.com/p/455925403

1. 下载 [msys 版 zsh](https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64)
2. 解压，获得 `usr` `etc` 
3. 将 `usr` `etc` 分别放入 `git bash` 根目录下，与原有同名文件夹合并

## Zsh-autosuggestions[^2]

[^2]: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#manual-git-clone

1. 利用 Git 下载插件
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```
2. 在 `.zshrc` 中添加下面一行
```shell
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```

## Zsh-syntax-highlighting[^3]

[^3]: https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md

1. 利用 Git 下载插件
```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
```
2. 在 `.zshrc` 中添加下面一行
```shell
source ./zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
