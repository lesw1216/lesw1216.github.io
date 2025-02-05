# MyBatis 세팅

## MyBaits 파일 위치

커스텀 위치 설정을 사용하여 편리하게 `Mapper.xml` 파일을 저장 할 수 있다.

```properties
mybatis.mapper-locations=classpath:mappers/*.xml
```

위처럼 위치를 지정하면 `resources/mappers/` 아래에 Mapper 파일을 생성하면 자동으로 스프링 부트가 인식한다.

## 언더바 케이스를 카멜 형식으로 자동 변환 설정

언더바로 선언된 컬럼들을 객체의 카멜케이스로 자동 변환해준다.

```properties
mybatis.configuration.map-underscore-to-camel-case=true
```

## Mapper.xml 파일을 생성 후 내부 구조

아래 `<mapper></mapper>` 안에 쿼리문을 작성한다.

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="mapper.class의 실제 위치">

</mapper>
```