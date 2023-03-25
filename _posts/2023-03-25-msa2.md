---
layout: single
title:  "API Gateway Service"
categories: MSA
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# API Gateway Service란

## API Gateway Service 필요성

마이크로 서비스가 많아지면서 클라이언트는 각각의 마이크로 서비스의 엔드포인트를 알아야한다는 단점이 존재 따라서 단일 진입점을 가진 형태로 개발하기 위해서 API Gateway service 가 필요합니다.

## API Gateway Service 정의

각각의 마이크로 서비스에 대한 단일 진입점 역할을 하여 서비스 검색을 통합해주고 인증 및 권한을 담당하는 트레픽 관리자입니다.

## API Gateway Service 역할/특징

인증 밎 권한 부여, 서비스 검색 통합, 부하 분산 등이 있습니다.
