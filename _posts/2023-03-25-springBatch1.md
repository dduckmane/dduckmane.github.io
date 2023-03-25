---
layout: single
title:  "Spring Batch 메타 데이터 테이블"
categories: SpringBatch
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

# Spring Batch 메타 데이터 테이블

![image](https://user-images.githubusercontent.com/108928206/227715346-2707b4ac-1fda-4451-b8d4-e9507a7831d0.png)

**BATCH_JOB_INSTANCE : JobInstance 객체의 정보를 담고 있으며 Batch 계층 구조의 최상위에 위치한다**

**BATCH_JOB_EXECUTION_PARAMS : JobParameter 객체의 정보를 담고 있다. Job 실행 시 사용된 파라미터를 저장합니다.**

**BATCH_JOB_EXECUTION : JobExecution 객체의 정보를 가지고 있다. 매 Job이 run 할 때, 항상 JobExecution이 생성되며 이 테이블의 row에 추가된다**

**BATCH_STEP_EXECUTION : 하나의 JobExecution에 대해 적어도 하나의 Step이 생성되고, 생성된 Step만큼 이 테이블의 row에 추가된다.**

**BATCH_JOB_EXECUTION_CONTEXT : Job의 ExecutionContext와 대응된다. 정확히 하나의 JobExecution에 대하여 하나의 ExecutionContext가 존재하며, Job 레벨의 모든 데이터를 갖고 있다.**

**BATCH_STEP_EXECUTION_CONTEXT : Step의 ExecutionContext에 대응된다. StepExecution과 StepExecutionContext는 일대일로 존재하며, 특정 stepExecution을 위한 모든 데이터를 포함하고 있다.**
