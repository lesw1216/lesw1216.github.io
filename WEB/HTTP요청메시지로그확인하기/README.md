---
layout: default
---

# HTTP 메시지 로그로 확인하는 방법
`application.properties`에 아래와 같이 작성
```properties
logging.level.org.apache.coyote.http11=trace
```
* 스프링 부트 3.2 이전은 `debug`
* 3.2 이후 부터는 `trace`

> [!CAUTION]
> 운영 서버에서 모든 요청 정보를 남기면 성능 저하가 발생할 수 있다. 개발 단계에서만 사용하는 것을 권장.