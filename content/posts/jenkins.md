---
title: "Hello Jenkins"
date: 2021-07-01T11:26:51+08:00
lastmod: 2020-07-08T14:52:31+08:00
draft: true
author: "ssfzxc"
description: "安装 Jenkins 时的一些笔记"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Jenkins", "CI/CD", "运维"]
categories: ["Jenkins"]

lightgallery: true
---


# Hello Jenkins


> 安装 Jenkins 时的一些笔记



## 坑

- Jenkins Job 启动后服务自动随 Job 执行完毕后关闭

  - Pipeline：新增 withEnv(['JENKINS_NODE_COOKIE=background_job'])

    ```groovy
    pipeline {
        agent any

        stages {
            stage('startup service local') {
                steps {
                    script {
                        withEnv(['JENKINS_NODE_COOKIE=background_job']) {
                            sh 'echo hello'
                        }
                    }
                }
            }
        }
    }
    ```

  - FreeStyle: 脚本最前面新增 BUILD_ID

  ```sh
  BUILD_ID=donotKillMe
  echo 'hello'
  ```

