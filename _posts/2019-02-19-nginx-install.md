---
title : nginx 설치
categories : [web]
tags : [nginx]
---
# NGINX 설치  (Package Manager 사용)
## # 작업 (Cent OS 및 yum 사용)
### 1. yum util 설치
````bash
sudo yum install yum-utils
````
### 2. 파일 생성 및 기록
#### 2.1. 경로 
````bash
/etc/yum.repos.d/nginx.repo
````

#### 2.2. 내용
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
### 3. nginx package (선택)
* yum install시 기본적으로 `nginx-stable package`가 적용됩니다.
* `nginx-mainline package` 적용을 원할 경우 아래의 command를 실행하면 됩니다.  
* [serverfault](https://serverfault.com/questions/715049/what-s-the-difference-between-the-mainline-and-stable-branches-of-nginx/715126#715126) 에 따르면 `nginx-mainline package` 사용을 권고합니다. 

````bash
sudo yum-config-manager --enable nginx-mainline
````

### 4. yum install
````bash
sudo yum install nginx
```` 
### 5. systemctl 등록 (선택)
* 시스템 부팅시 nginx daemon을 자동실행시키고 싶다면 아레 command를 실행하면 됩니다.

````bash
sudo systemctl enable nginx.service
````
### 6. nginx  daemon 실행
* 1, 2번 command 중 택일 실행하면 됩니다.

````bash
1. sudo systemctl start nginx.service
2. sudo service nginx start
````
 
### 7. 참조
nginx 공식 홈페이지 : <http://nginx.org/en/linux_packages.html>