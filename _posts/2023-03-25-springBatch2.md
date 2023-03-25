---
layout: single
title:  "tasket model vs reader, processor, writer 의 차이점"
categories: SpringBatch
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

![image](https://user-images.githubusercontent.com/108928206/227715410-6a7e3e4f-9595-4f5b-aac1-8760583a41c4.png)

스프링 배치의 구조에는 jobRepository, job, step, jobLauncher로 구성되어 있습니다.

job repository 란 배치가 수행될 때의 메타데이터를 저장하고 배치 수행관련 데이터들을 저장

joblauncher 는 잡을 실행하는 역할을 합니다.

잡은 step 으로 이루어져있고 step은 item reader, item processor, itemWriter 로 구성되어 있거나 tasklet 방식으로 구성되어 있습니다.

첫번 째 구성방식은 itemReader 는 데이터를 청크 단위로 읽어 드리는 작업을 합니다. itemproccer 는 데이터를 가공하거나 필터링하는 역할을 하며 itemWriter는 데이터를 쓰는 역할을 하며 데이터를 데이터베이스에 저장하거나 파일에 저장하는 역할을 합니다.

두번 째 구성방식은 tasklet 방식으로 주로 가벼운 로직이 들어갈 때 많이 사용되는 방식으로 차례대로 beforeStep, execute, afterStep 순으로 실행됩니다.
