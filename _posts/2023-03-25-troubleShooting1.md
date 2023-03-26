---
layout: single
title:  "csrf 403 Error 해결"
categories: TroubleShooting
tag: [code]

author_profile: false
sidebar:
    nav: "counts"
---

## 적용코드

```
httpSecurity.csrf()
               .ignoringAntMatchers("/api/**")
               .ignoringAntMatchers("/user/**")
               .csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse()); 
```

## 개발 환경과 적용 이유

1) 개발 환경
- Same-Origin Policy(SOP)
- 동일한 출처(프로토콜, 호스트, 포트)에서만 요청과 응답
- session 기반 인증
- 기존 코드
  ```
  httpSecurity.csrf().disable();
  ```
- csrf.able
    - 장점:  csrf 공격을 막아준다.
    - 단점: csrf Token 이 없이 요청한다면 403 Error 발생
    
2) 적용이유 

- 기존에는 csrf().disable() 로 설정해놓았기 때문에 csrf 토큰 여부와 상관없이 요청과 응답을 하였다.
- 하지만 나의 에플리케이션은 세션 기반인증이기 때문에 csrf를 disable로 설정 시에 csrf 공격에 안전할 수가 없다.

3) 코드 분석

- ignoringAntMatchers: 여기에 설정한 url 은 csrf protection 에 있어서 예외처리가 된다.
	
    - 그래서 나의 에플리케이션 api는 모두 /api 로 시작하고
    - controller에서 post, put, delete 요청은 /user 로 받기 때문에 두가지 부분을 예외 처리 시켜주었다.
    
- csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse()): csrf 토큰을 자동 생성해준다.

4) 참고

https://graykang.tistory.com/68
