---
layout: single
title:  "Api gateway & Load Balancer & Service Discovery"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# 스프링에서 제공하는 Api gateway & Load Balancer & Service Discovery 에 대해서 알아보자

![image](https://user-images.githubusercontent.com/108928206/227872379-4f765b43-5548-4efd-8a4a-255e179135b8.png)

## Service Discovery

- Eureka 를 이용하여 마이크로서비스를 등록한다.
- 또한 각 서비스에 대해서 여러개으 인스턴스를 생성하여 등록을 한다.

![image](https://user-images.githubusercontent.com/108928206/227872841-7c03c715-0f1a-4a35-99f1-990a51575823.png)

## Load Balancer

- Api Gateway 에서는 라운드 로빈 스케쥴링 기법을 이용하여 Load Balancer 기능도 제공한다.
- 예시

![image](https://user-images.githubusercontent.com/108928206/227873081-0263dfce-fb51-4067-8b6a-bef3bda47cd3.png)

- 결과

![image](https://user-images.githubusercontent.com/108928206/227873148-529bdfad-7aeb-49fe-9773-e108274d321c.png)
![image](https://user-images.githubusercontent.com/108928206/227873187-6d3b456a-7974-4e10-a0ec-bf4dabed617f.png)

: 번갈아 가면서 요청

## Api gateway

- Api gateway 도 유레카에 등록을 한다.
- 이름으로 접근이 가능하다.

![image](https://user-images.githubusercontent.com/108928206/227873456-0804581e-675d-4162-b8af-cf6bbcca808b.png)

- path 로 오는 요청에 대해서
- 이름으로 service discovery 를 통해서 해당 서비스를 호출한다.
