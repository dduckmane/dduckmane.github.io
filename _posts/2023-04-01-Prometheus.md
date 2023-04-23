---
layout: single
title:  "Prometheus & Grafana"
categories: MSA
tag: [code, 개념]

author_profile: false
sidebar:
    nav: "counts"
---

# 모니터링 

## 필요성

- 마이크로서비스는 종종 분산 및 비동기 통신에 의존하기 때문에 문제가 발생할 때 추적하기 어려울 수 있다.
- 모니터링으로 서비스와 상호 작용의 성능 및 상태에 대한 가시성을 확보하기 위함이다.

## Prometheus란

- 시스템의 다양한 구성 요소에서 메트릭을 수집하고 분석하기 위해 마이크로 서비스 아키텍처에서 자주 사용되는 인기 있는 오픈 소스 모니터링 시스템
- 시스템 전체에서 메트릭을 수집하고 분석하는 중앙 집중식 플랫폼을 제공
- 메트릭 정보를 프로메테우스가 가져와서 자신만의 시계열 DB 에 저장하여 성능과 상태에 대한 가시성을 확보할 수 있도록 도와준다.

## Grafana

- 시계열 데이터를 시각화하기 위해서 사용

## Prometheus 설정

- Prometheus 를 설치
- prometheus.yml 파일 수정하여 어디서 시계열 데이터를 추출할 지 결정

<img width="612" alt="image" src="https://user-images.githubusercontent.com/108928206/229259685-031dd93a-0f9d-47e2-8561-c54432743279.png">

- 종속성 추가

![image](https://user-images.githubusercontent.com/108928206/229259756-b5545cd3-c0de-4a33-a409-c5cd933b7a54.png)

- 스프링에서 제공하는 acutator 를 이용하여 엔드포인트로 노출

![image](https://user-images.githubusercontent.com/108928206/229259775-d13f4df3-8da7-48e1-a22e-c8f96fa02eab.png)

- 서버를 실행

### @Timed

- 메트릭을 설정
- 시계열 데이터(메트릭의 실시간 데이터) 를 추출할 수 있다.
- 메서드에 정의

![image](https://user-images.githubusercontent.com/108928206/229259872-321a1847-7296-45a2-a561-a9074a74170a.png)



## Grafana 설정

- 설치 후 포트로 접속
- jvm, api-gateway, Prometheus 등 가져올 데이터를 설정



