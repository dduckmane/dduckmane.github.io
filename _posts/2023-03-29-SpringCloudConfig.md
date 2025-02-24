---
layout: single
title:  "Spring Cloud Config"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# Config Server

## Config Server란

- 설정 정보를 하나의 중앙화된 저장소에서 관리가 가능하다.
- 각 서비스를 다시 빌드하지 않고 수정가능하다.

## Spring Cloud Config 사용법

1) Config 서버를 생성한다.

![image](https://user-images.githubusercontent.com/108928206/228293359-6b4a9a35-28ff-4600-b16e-aa6be4a71d73.png)

- @EnableConfigServer 를 적용한다.

2) 서버의 yml 파일을 수정한다.

![image](https://user-images.githubusercontent.com/108928206/228293516-213f7f0a-507a-48bc-803c-3f1fecdb31b1.png)

3) 클라이언트쪽에서 종속성 추가를 한다.

![image](https://user-images.githubusercontent.com/108928206/228293720-633bfff2-5e42-4be1-97fc-397d1a930c41.png)

4) bootstrap.yml 파일을 생성한다.

![image](https://user-images.githubusercontent.com/108928206/228293811-9fee0802-d4fc-4075-a456-7a46c6877a5d.png)

5) 사용

![image](https://user-images.githubusercontent.com/108928206/228294326-078c8210-4abf-4551-8a53-ee7a19e0e611.png)

![image](https://user-images.githubusercontent.com/108928206/228293869-c2cdf7d5-8d6d-4c8c-80c8-045bfc9e0a1b.png)

## 설정 정보를 바꾸는 방법

1) 서버 재기동
2) Spring Boot Actuator에서 제공하는 Actuator refresh
3) Spring cloud bus






