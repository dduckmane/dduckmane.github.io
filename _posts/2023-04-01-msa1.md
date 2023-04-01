---
layout: single
title:  "CircuitBreaker"
categories: MSA
tag: [code, 개념]

author_profile: false
sidebar:
    nav: "counts"
---

# 장애 처리

## 필요성

- 마이크로 서비스간의 통신이 있을 시에
- 예를 들어 feign client로의 통신이 있다.
- 다른 마이크로 서비에서 장애가 발생을 한다면 연쇄 오류가 발생을 할 수가 있다.
- 따라서 다른 마이크로 서비스에서 장애 시에 연결을 끊고 디폴트 값을 전달하여
- 연쇄 오류를 막고 클라이언트쪽에 오류를 전달하지 않는 기법

## 설정

- 종석성 추가

![image](https://user-images.githubusercontent.com/108928206/229259237-4ebd65a6-7c76-49f5-8e3c-594225d19622.png)

- 설정 파일 추가(따로 지정안할 시에는 디폴트 값)

![image](https://user-images.githubusercontent.com/108928206/229259276-7fdda5a0-5b2a-4eb5-b1a6-1ef6a66c4b42.png)

- 로직

![image](https://user-images.githubusercontent.com/108928206/229259285-f5b2eef3-7d9d-43fb-a364-f6d4656f6c05.png)

![image](https://user-images.githubusercontent.com/108928206/229259304-af70100d-ad4c-46bf-902b-fae93f483fb2.png)




