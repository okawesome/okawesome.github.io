# Pact

##### 1. Pact란?
```
Consumer-Driven Contract Testing을 위한 테스트 프레임워크
```
##### 2. 개념
```
API제공자와 사용자가 Pact를 활용하여 Contract(API명세규약)를 교환
```
##### 3. 동작 방식
```
1. 사용자가 제공자의 API를 호출하는 경우, Pact프레임워크를 사용하여 제공자의 API를 stubbing하여 테스트 코드를 작성
2. 작성 테스트코드 실행 시, Pact에서 Pactfile을 generate해줌 (Pactfile : json형태의 Contract명세파일)
3. Pactfile을 PactBroker에 업로드 (PactBroker : Pactfile 교환을 위한 repository)
4. 제공자가 PactBroker에서 Pactfile을 가져온 후, 실제 제공자의 API가 Pactfile의 명세와 일치하는 지 검증
```
##### 4. 예시
1. Pactfile 예시
```
{
  "provider" : {
    "name" : "Foo_Provider"
  },
  "consumer" : {
    "name" : "Foo_Consumer"
  },
  "interactions" : [ {
    "description" : "a request for Foos",
    "request" : {
      "method" : "GET",
      "path" : "/foos"
    },
    "response" : {
      "status" : 200,
      "headers" : {
        "Content-Type" : "application/json;charset=UTF-8"
      },
      "body" : [ {
        "value" : 42
      }, {
        "value" : 100
      } ]
    }
  } ],
  "metadata" : {
    "pact-specification" : {
      "version" : "2.0.0"
    },
    "pact-jvm" : {
      "version" : "2.1.7"
    }
  }
}
```
##### 5. 참고

- Pact Docs : https://docs.pact.io/documentation/
- Pact jvm + springBoot 예시 프로젝트 : https://github.com/mstine/microservices-pact
- Pact Broker 깃헙 : https://github.com/pact-foundation/pact_broker
- Pact Broker 사용 예 : https://blog.shanelee.name/2016/07/19/consumer-driven-contract-testing-using-pact/
