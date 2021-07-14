---
title: "Hello ArchLinux"
date: 2021-07-01T11:26:51+08:00
lastmod: 2020-07-08T14:52:31+08:00
draft: true
author: "ssfzxc"
description: "安装ArchLinux"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["archliux", "linux"]
categories: ["linux"]

lightgallery: true
---

# Hello Archlinux



> 安装 ArchLinux 时的一些笔记



##  安装注意点

- USB 启动方式一定要是 UEFI 方式
- 安装 key 不存在, pacman-key 命令
- iwd(iwctl) wifi/wlan 链接 CLI, dhcpcd
- archlinuxcn 需要安装   ```sudo pacman -S archlinuxcn-keyring```
- 独立显卡损坏，启动 startx 需要先禁用



## 常用CLI

- jq: json formatter
- neofetch: 装逼神器
- bat: cat 替代品
- htop: top 替代品
- exa: ls 替代品
- iftop: net io 监控
- ack/ag(the_silver_searcher)/rg(ripgrep): grep
- global/ctags
- delta: diff
- paru: arch AUR
- fd: find 替代品



## AUR-keyring

- gpg --keyserver keyserver.ubuntu.com --recv-keys 5DECDBA89270E723

- gpg --keyserver keyserver.ubuntu.com --lsign-key 5DECDBA89270E723

- gpg --keyserver keyserver.ubuntu.com --finger 5DECDBA89270E723\

- ```
  pacman -Syu haveged
  systemctl start haveged
  systemctl enable haveged
  
  rm -fr /etc/pacman.d/gnupg
  pacman-key --init
  pacman-key --populate archlinux
  pacman-key --populate archlinuxcn
  ```

