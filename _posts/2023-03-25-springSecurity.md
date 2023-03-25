---
layout: single
title:  "Spring Security"
categories: SpringSecurity
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# 스프링 시큐리티

## Spring Security princal 객체

userDetails 객체 혹은 Oauth2User 객체가 담기게 됩니다.

SecurityContext 는 Authentication 정보가 있다.

Authentication 는 principal 객체와 GrantAuthority 정보가 있다.

![image](https://user-images.githubusercontent.com/108928206/227717677-7c60173e-0fce-4481-b031-09e9055f0a1d.png)

SecurityContextHolder 안에는 Authentication 정보를 가지고 있는 SecurityContext 가 존재하고 

Authentication 영역안에는 Principal 객체와 GrantAutnority 정보가있습니다.

principal 객체는 userDetails 혹은 Oauth2User객체가 입니다.

## Spring Security의 어노테이션

`@EnableWebSecurity` : 스프링 시큐리티 필터가 스프링 필터체인에 등록이 됩니다.

`@EnableGlobalMethodSecurity` : `secured 어노테이션 활성화, preAuthorize 어노테이션 활성화`

`@AuthenticationPrincipal` : Authentication 영역안의 principal 객체를 가져온다.

`@Secured` , `preAuthorize` : 권한처리를 가능하게 해준다.
