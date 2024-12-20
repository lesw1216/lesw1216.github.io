# Profile 설정 구성하기

`application-[profile].properties`를 사용해 profile 별 설정을 구성할 수 있다.

|profile|properties name|
|---|---|
|dev|application-dev.properties|
|prod|application-prod.properties|

# Profile 사용자 지정

메인 파일인 `application.properties`에 다음과 같이 설정하자

```properties
spring.config.location=classpath:config/
```

위처럼 설정하면 `/resources/config/` 아래에 profile.propreties 파일들을 위치 시켜 놓으면 스프링 부트가 자동으로 읽어 설정을 처리한다.

# 현재 활성화 profile 설정하기

`application.propreties`에 다음과 같이 작성한다.

```properties
spring.profiles.active=dev
```

위의 설정은 `application-dev.properties`을 사용해 profile을 dev로 설정한다.

### 테스트 패키지 내부에도 똑같은 구조로 파일을 그대로 복사하여 위치시켜 두어야 테스트 시 적용된다.