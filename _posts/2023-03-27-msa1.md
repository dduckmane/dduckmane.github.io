---
layout: single
title:  "Spring Cloud Gateway Filter"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# Spring Cloud Gateway 에서 Filter의 역할

## Spring Cloud Gateway Filter 동작원리

- Gateway Handler Mapping : 요청이 오면 헨들러를 찾고
- predicate : 해당하는 predicate 를 본다.
  
  - 각 path 와 매치하는 uri 로 요청이 간다.

- uri 호출 전에 **사전 필터가 작동한다.
- 응답을 받고
- **사후 필터가 작동

## 필터의 종류

- 제공하는 필터
- Custom Filter
- Global Filter

## 제공하는 필터

![image](https://user-images.githubusercontent.com/108928206/227859671-f59274b3-be85-44b8-90df-253edc185b42.png)

- 제공하는 옵션을 이용하여 헤더에 추가등을 할 수가 있고
- 왼쪽이 키 값, 오른 쪽이 value 값이다.

## Custom Filter

![image](https://user-images.githubusercontent.com/108928206/227859933-fa046f61-41f9-467b-8b70-671b4b836f95.png)

1) AbstractGatewayFilterFactory<CustomFilter.Config>

- AbstractGatewayFilterFactory 를 상속을 받고
- 타입 설정을 해줄 수 있다. 이때의 Config 정보가 오버라이딩 메서드에 매개변수로 작동
- 보통 필터안에 이너 클래스로 정의

2) 생성자

![image](https://user-images.githubusercontent.com/108928206/227860276-e21a636a-225d-48af-bc56-0909ec179dc7.png)

3) apply 메소드

- 사전 필터와 사후 필터를 적용할 수 있다.

![image](https://user-images.githubusercontent.com/108928206/227860515-cd5536cb-32e2-4ad5-b443-4977fc7ec3fe.png)

**Exchange 객체

- Spring webflux 를 사용하면 기존의 mvc 방식에서 사용이 되었던 httpServlet request,response 를 지원하지 않고 server request,response 를 지원하게 된다.
- 그 request,response 를 사용하게 해주는 것이 exchange 객체이다.

- 또한 필터의 순서를 정할 수 있다.

![image](https://user-images.githubusercontent.com/108928206/227861295-e157eb70-b705-4213-adde-a03abb6d2f64.png)

4) 그리고 yml 파일에서 적용을 하면 된다.

- 그냥 적용

![image](https://user-images.githubusercontent.com/108928206/227861451-d880bdac-74bc-4444-8f6b-709fad366fa9.png)

5) config 파일 매개변수와 함께 적용

![image](https://user-images.githubusercontent.com/108928206/227861578-827d0b62-3e04-4a50-8d9b-67f5ac060276.png)

## Global Filter

- 위에서 만든 Custom 필터를 전역으로 처리하게 할 수 있다.

![image](https://user-images.githubusercontent.com/108928206/227861723-9f7f7f63-1ba0-46a8-b6de-f07cc9fe51c6.png)






