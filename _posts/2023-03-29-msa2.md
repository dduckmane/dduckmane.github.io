---
layout: single
title:  "Spring Cloud Config 네이밍 기법"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# Spring Cloud Config 의 이름 우선 순위

## 방법

1. config-server 의 이름만 적는다.

2. config-server 에 연결된 yml 파일의 이름만 적는다.

![image](https://user-images.githubusercontent.com/108928206/228517287-a33acce4-7402-4c0d-827c-8666281ba0a1.png)

- uri에 해당하는 config-server 를 찾는다.
- config - server 가 연결된 파일을 검색

![image](https://user-images.githubusercontent.com/108928206/228517761-2266c40b-cd58-4d69-8a6b-0aefa8548f6c.png)

config-server 는 git 과 연결이 되어있기 때문에 git 에서 찾는다.

- git에서 name과 같은 yml 파일을 검색

![image](https://user-images.githubusercontent.com/108928206/228518095-f7d62111-16b3-4b9d-836a-514a04647110.png)



3. config-server 에 연결된 yml 파일 + profie 을 지정한다.

![image](https://user-images.githubusercontent.com/108928206/228518241-69207391-1f36-4d4e-a51b-2465ce7ba468.png)

