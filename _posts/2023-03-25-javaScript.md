---
layout: single
title:  "AWS-EC2"
categories: AWS
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

## 진행 이유
: postman 으로만 test 하였지만 cors 문제가 항상 터졌다 ㅜㅜ
그 이후로는 중요한 api test 들은 자바스크립트를 이용하여 test 를 해본다.

## 설명

: get 과 post 요청을 편히 할 수 있도록 형식을 만듦

## 코드

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

</body>

<script>
  function post() {
    const URL = '';
    let data = {
      username : "testUser1"
      ,password : "testUser1*"
    }
    const reqInfo = {
      method: 'POST'
      , headers: {
        'content-type': 'application/json'
      }
      , body: JSON.stringify(data)
    }
      fetch(URL, reqInfo)
          .then(res => res.status)
          .then(result => console.log("status= "+result));

    fetch(URL, reqInfo)
            .then(res => res.headers.get('Authorization'))
            .then(result => console.log("jwtToken= "+result));

    fetch(URL, reqInfo)
            .then((response) => response.json())
            .then((data) => {
                  console.log('ResponseBody:', data);
            })
  }

  function get() {
      const URL = '';

      const reqInfo = {
          method: 'GET'
          , headers: {
              'content-type': 'application/json'
              , 'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbjEyMzQiLCJpZCI6MSwiZXhwIjoxNjczMDc2ODk5LCJ1c2VybmFtZSI6ImFkbWluMTIzNCJ9._c3AWCni7qW6fKMruUauQ-DQlFuvAdrn9MYbBcIoP-1EWbYrStR2QoWtjDS-PgNAQg2CFeXUw8nF-M0wEStZrw'
          }
      }
      fetch(URL, reqInfo)
          .then(res => res.status)
          .then(result => console.log("status= "+result));

      fetch(URL, reqInfo)
          .then(res => res.headers.get('Authorization'))
          .then(result => console.log("jwtToken= "+result));

      fetch(URL, reqInfo)
          .then((response) => response.json())
          .then((data) => {
              console.log('ResponseBody:', data);
          })
  }

  (function () {
  // 태스트 해보고 싶은 method 를 메인 실행부에 적는다.
  })();
</script>

</html>
```

