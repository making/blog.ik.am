---
title: AWS CLIの使い方メモ
tags: ["AWS", "AWS CLI"]
categories: ["Dev", "AWS"]
date: 2015-04-15T23:59:32+09:00
updated: 2015-04-15T23:59:32+09:00
---

初歩的なメモ。

### インストール

``` console
$ brew install awscli
```

### 初回設定

``` console
$ aws configure
AWS Access Key ID [None]: *****
AWS Secret Access Key [None]: *****
Default region name [None]: ap-northeast-1
Default output format [None]: json
```

### 補完設定(bash)

``` console
$ complete -C aws_completer aws
```

### S3のバケット作成

``` conosle
$ aws s3 mb s3://xyz-boshrelease
make_bucket: s3://xyz-boshrelease/
```
