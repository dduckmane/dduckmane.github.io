---
layout: single
title:  "포트원(구 아임포트) db와 가맹점 db의 동기화"
categories: TroubleShooting
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

[문제]

- 현재는 가맹점db와 아임포트의 db는 결제 한 건당 동기화를 진행
- 하지만 불특정하게 동기화가 안되는 경우가 발생
- 혹은 서버가 불안정하여 웹 훅 요청으로 인한 동기화가 원활히 이루어지지 않아 데이터 정합성에 문제가 있을 수 있다고 판단

[해결]

- Spring Batch로 특정 시간대에 동기화 작업을 진행

[코드]

1) 동기화 Job을 생성

```
@StepScope
    @Bean
    @Transactional
    public Tasklet OrderJobTasklet() {
        return (contribution, chunkContext) -> {
            // orders Table 순회
            // orders 의 merchant_uid 로 pg 사 결제 상태를 조회
            // 둘의 상태가 다르다면 동기화
            List<SafekingPayment> result = safekingPaymentRepository.findAll();

            for (SafekingPayment safekingPayment : result) {
                Payment response = client
                        .paymentByImpUid(safekingPayment.getImpUid())
                        .getResponse();

                String iamPortStatus = response.getStatus();

                String dbStatus = safekingPayment.getStatus().getDescription();
                String DBStatus = changeStatus(dbStatus);

                if (iamPortStatus != DBStatus) {

                    safekingPayment.changeSafekingPayment(changeIamPortStatus(iamPortStatus) , response);
                }
            }

            return RepeatStatus.FINISHED;
        };
    }
```

2) BatchScheduler에 Job 을 적용

```
@Scheduled(cron = "0 35 4 ? * *")
    public void OrderJobRun()
            throws JobInstanceAlreadyCompleteException
            , JobExecutionAlreadyRunningException
            , JobParametersInvalidException
            , JobRestartException {
        log.info("OrderJob BATCH");
        JobParameters jobParameters = new JobParameters(
                Collections.singletonMap("requestTime", new JobParameter(LocalDateTime.now().format(DateTimeFormatter.ofPattern("yyyy-MM-dd"))))
        );
        jobLauncher.run(OrderJob,jobParameters);
        log.info("success OrderJob");
    }
```

