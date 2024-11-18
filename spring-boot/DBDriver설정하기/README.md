# DB Driver 설정하기

## H2
```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
```
* `mem` : 인메모리 
* `username` : SA인 경우 패스워드는 필요 없음
* `spring.h2.console.enabled=true` : 인메모리로 실행하였을 때 콘솔 모드를 사용할 수 있는 옵션