---
title : nginx 설치
categories : [nginx]
tags : [nginx]
---
## NGINX 설치  
### 작업
#### 1. yum util 설치
````bash
sudo yum install yum-utils
````
#### 2. 파일 생성 및 기록
파일 경로 : `/etc/yum.repos.d/nginx.repo`

````bash
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key

[nginx-mainline]
name=nginx mainline repo
baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://nginx.org/keys/nginx_signing.key
````


## 참조
[nginx 공식 홈페이지]: http://nginx.org/en/linux_packages.html