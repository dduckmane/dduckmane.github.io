---
layout: single
title:  "MSA Connection 에러"
categories: TroubleShooting
tag: [code]

author_profile: false
sidebar:
    nav: "counts"
---

# MSA 기반 프로젝트 Connection Exception

## 현재 MSA 구조

![Unknown](https://user-images.githubusercontent.com/108928206/229394917-cc55e733-fd8f-49ae-9fcc-50611ed579bc.png)


- 각각의 서비스들은 모두 config server 를 참조

## 예외 사항

1. config server 를 참조하고 있는 서비스들의 BeanCreationException
  
  : config server 의 데이터를 참조하고 있지만 config 서버가 먼저 실행되지 않았기 때문에 BeanCreationException 발생
  
2. TransportException

  - api gateway 는 discovery service 를 참조
  - discovery service 가 선 실행이 되야함
  - 마찬기지로 user-service 도 discovery service 를 참조

## 해결

: 순서가 중요!!

- 별개로 데이터베이스 실행
- config 서버 실행
- discovery service 실행
- api gateway 실행
- 각각의 마이크로 서비스 실행
