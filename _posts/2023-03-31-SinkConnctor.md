---
layout: single
title:  "Sink Connctor 를 이용한 데이터 동기화"
categories: MSA
tag: [code]

author_profile: false
sidebar:
    nav: "counts"
---

# Sink Connctor 를 스프링에 적용하기

## 목적

- 각각의 서비스가 다른 데이터베이스를 사용할 때 데이터 동기화 문제를 Sink Connector 를 이용해서 해결
- 이력서를 저장하는 로직에서 데이터베이스에 바로 저장하는 것이 아닌
- 토픽에 데이터를 전달하고 그 토픽을 sink connector 를 이용해서 db 에 저장하는 로직을 구성

## 방법

1. zookeeper 를 실행
2. kafka 를 실행
3. kafka connector 를 실행

  - [사전 설정]
  - JDBC Connector 설치
  - 카프카 커넥터의 etc/kafka/connect-distributed.properties 파일 마지막에 아래 plugin 정보 추가
  - ![image](https://user-images.githubusercontent.com/108928206/229086729-137473a6-cf2a-42c7-9f13-6d48955fa331.png)
  - 카프카 커넥터가 jdbc connector 플러그인을 가지고 있어야 한다.
  - 또한 카프카 커넥터가 MariaDB 사용하기 위해 mariadb 드라이버 복사
  - ./share/java/kafka/ 폴더에 mariadb-java-client-2.7.2.jar 파일 복사

4. 프로듀서 쪽(이력서 서비스)에서 토픽에 정해진 format 에 맞춰서 데이터를 토픽에 전송을 해야한다.
5. 코드

![image](https://user-images.githubusercontent.com/108928206/229087652-5d3e132d-ad17-4e92-83bf-491fe502bae9.png)

6. 적용

![image](https://user-images.githubusercontent.com/108928206/229087747-685d69f6-0787-4999-9bd2-4981ce21140c.png)


