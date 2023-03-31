---
layout: single
title:  "kafka 데이터 불일치 예외"
categories: TroubleShooting
tag: [code]

author_profile: false
sidebar:
    nav: "counts"
---

# kafka 토픽 정보가 db 정보와 맞지 않는다면

## 문제 사항

- payload 값에 정확한 값을 전달하지 못함

- 하지만 토픽에는 데이터가 쌓여 있기 때문에
 
- 다시 올바른 데이터를 전달한다해도 문제가 생김

## 해결 방안

- 토픽의 데이터를 삭제를 해야한다.
- 혹은 데이터 커넥터가 잘못된 정보를 가지고 있어도 문제가 생길 수 잇음

## 삭제 명령어

### 토픽 삭제

- ./kafka-topics.sh --delete --zookeeper localhost:2181 --topic 
- 여기서 joptsimple.UnrecognizedOptionException 오류가 표시되는 경우 이전 --zookeeper 옵션 대신 최신 --bootstrap-server 옵션을 사용한다.
- ./kafka-topics.sh --delete --bootstrap-server localhost:9092 --topic my_topic

## 커넥터 삭제

- curl -X DELETE http://localhost:8083/connectors/<connector-name>
- 혹은 커넥터를 삭제하지 않고 중지하려면 다음과 같이 DELETE 대신 PUT 메소드를 사용
- curl -X PUT -H "Content-Type: application/json" --data '{"connector.state":"STOPPED"}' http://localhost:8083/connectors/<connector-name>/state
