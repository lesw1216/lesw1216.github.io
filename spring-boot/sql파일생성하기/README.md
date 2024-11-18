# SQL 파일 생성하기

* `schema.sql` : 테이블과 같은 스키마 정의

* `data.sql` : 초기 데이터를 삽입하는 SQL

기본적으로 파일 위치는 `/resources` 바로 아래에 두는 것이 원칙이다. 하지만 설정을 통해 스프링 부트가 스캔하는 위치를 지정 할 수 있다.

주의할 점으로는, 두개의 파일이 `db/`에 있다고 해서 `classpath:db/`로 설정 할 수 없다는 것이다. `schema.sql`과 `data.sql` 따로 위치를 지정해주어야 한다.

```properties
spring.sql.init.schema-locations=classpath:db/schema.sql
spring.sql.init.data-locations=classpath:db/data.sql
```

그리고 테스트에도 사용 될 수 있다.