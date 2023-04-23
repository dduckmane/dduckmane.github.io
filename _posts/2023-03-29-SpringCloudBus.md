---
layout: single
title:  "Spring Cloud Bus"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# config server + Spring Cloud Bus

## 도식도

![image](https://user-images.githubusercontent.com/108928206/228541229-0c0bb030-3640-4689-8277-499dc61dbdd4.png)

1. git 변경
2. spring-boot-starter-actuator 종석성 추가를 한 api gateway 에 /actuator/busrefresh post 요청
3. actuator 가 api gateway 에 설정된 config 정보의 변경을 감지 최신화
4. Spring cloud bus 를 통해 연결된 노드에게 데이터 변경사항 최신화를 요청
5. 이 때 rabbitmq 를 통해 amqp 프로토콜을 통해 전달
6. 연결된 노드의 설정 최신화
