---
title: "Hello ArchLinux"
date: 2021-07-14T17:16:46+08:00
lastmod: 2021-08-02T14:17:00+08:00
draft: true
author: "ssfzxc"
description: "安装ArchLinux"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["运维", "linux"]
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

## 折腾AwesomeWM

- awesome 使用 `sudo pacman -S awesome-git`, 特性更为全面

- 锁屏工具 `i3clock`

- 窗口合成器, 实现半透明等等功能 `picom`

- 全局应用搜索 `rofi`

- terminal `kitty || alacritty`

