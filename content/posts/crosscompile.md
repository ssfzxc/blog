---
title: "Cross Compile"
date: 2021-09-07T11:00:00+08:00
lastmod: 2021-09-07:11:00+08:00
draft: true
author: "ssfzxc"
description: "关于在 ArchLinux 上使用 Rust 进行交叉编译"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["rust", "linux"]
categories: ["linux"]

lightgallery: true
---

# ArchLinux + Musl

## 安装依赖

`pacman -S musl kernel-headers-musl`

-   musl: musl 主体依赖
-   kernel-headers-musl: musl 使用的 linux-headers

## Rust

`rustup target add x86_64-unknown-linux-musl`

# 参考案例: openssl

```
    mkdir /musl 

    wget http://github.com/openssl/openssl/archive/OpenSSL_1_1_1l.tar.gz
    tar zxvf OpenSSL_1_1_1l.tar.gz
    cd OpenSSL_1_1_1l.tar.gz

    CC="musl-gcc -fPIE -pie" ./Configure no-shared no-async --prefix=/musl --openssldir=/musl/ssl linux-x86_64
    make depend
    make -j$(nproc)
    make install

    export PKG_CONFIG_ALLOW_CROSS=1
    export OPENSSL_STATIC=true
    export OPENSSL_DIR=/musl
    cargo build --target x86_64-unknown-linux-musl 
```

# TODO: 直接使用 glibc 进行静态编译
