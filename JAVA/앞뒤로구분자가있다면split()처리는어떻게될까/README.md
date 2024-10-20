# 구분자가 맨 앞 또는 맨 뒤에 있는 경우, split()의 결과

다음과 같은 문자열을 구분자로 나눌 때 실행 결과를 알아보자.

1. `,2,3`

2. `2,3,`

위 둘의 차이점은 `콤마(,)`가 맨 앞과 맨 뒤에 존재한다. 이 때 `split()`의 결과 값을 알아 본다.

# 1. 맨앞에 있는 경우
```JAVA
String test = ",2,3";

String[] split = test.split(",");
System.out.println(Arrays.toString(split));
```

```
[,2,3]
```

위의 결과 값이 나온다.

,의 앞에도 빈 공백문자로 인식한다. 따라서 `split()`을 호출했을 때 3개의 원소가 반환된다.

# 맨 뒤에 있는 경우
```JAVA
String test = "2,3,";

String[] split = test.split(",");
System.out.println(Arrays.toString(split));
```

```
[2,3]
```

맨 앞의 경우와는 달리 맨 뒤에 구분자가 오면 앞의 2와 3 두 개의 값으로만 나누어진다.

# 정리

* 구분자가 맨 앞에 오는 경우 - `2,3`

    앞의 공백도 문자로 인식한다.

* 구분자가 맨 뒤에 오는 경우 - `2,3,`

    앞의 2와 3 두 개의 값만 인식한다.

[Java 21 API split() 문서](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/String.html#split(java.lang.String))