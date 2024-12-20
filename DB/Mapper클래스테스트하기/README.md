# Mapper 클래스 테스트 하기

Mapper를 사용하면서 작성하는 테스트는 다음과 같이 나눌 수 있다. 아래의 방법 모두 MyBatis를 사용한 테스트는 `@MyBatisTest`를 이용해 테스트를 진행 할 수 있다.

## 1. Mapper 클래스 단독 사용

```java
@MyBatisTest
public class test {
    
    @Autowired
    Mapper mapper;

    // 이하 생략 ...
}
```

## 2. Repository 내부에 Mapper 클래스 사용

```java
@MyBatisTest
@Import(Repository.class) // 실제로 들어가는 값은 Mapper를 주입 받는 구현체 클래스. 예) @Import(WorkoutRepository.class)
public class test {
    
    @Autowired
    Repository repository; // 인터페이스 사용

    // ...
}
```

`@MyBatisTest`는 MyBatis 테스트만을 위한 필수 값만을 빈으로 등록한다. 따라서 1번과 같은 Mapper 단독은 `@MyBatis`만 사용하여도 되지만, 2번과 같은 Mapper를 주입 받는 Repository를 사용한다면 해당 Repository를 개별적으로 추가해주어야 한다.