# WAS와 멀티 스레드
클라이언트가 서버에 요청하고 응답을 받는 과정에서 서블릿 객체가 어떻게 호출되는지 알아보자.


# 서블릿과 스레드
클라이언트의 요청은 스레드로 서버 내에서 실행된다. 그래서 하나의 스레드 내에서 서블릿을 사용한다.

그래서 스레드를 사용할 때 주의할 점은 싱글톤 객체 사용에 유의해야 한다. 하나의 객체를 여러 스레드가 공유하기 때문에 잘못된 데이터가 사용될 수 있기 때문이다.

## 단일 스레드 사용 시 문제점
요청1과 요청2가 있다고 가정하자. 요청1이 서버에 요청을 보냈다. 이 때 스레드가 서블릿 객체를 호출하는데 어떤 문제가 있어 요청 처리에 지연이 생기게 되었다. 그 후에 요청2가 서버에 요청을 보냈을 때 요청2는 요청1의 작업을 스레드가 마쳐야 스레드를 할당 받을 수 있다.
 
  
그렇게 되면, 요청1, 요청2 둘다 타임 아웃이 발생한다.

## 해결법은?
요청이 들어오는 수 만큼 스레드를 생성할 수 있다.
 

위의 방법은 많은 요청이 들어오면 메모리에서 감당 할 수 없게되어 서버가 다운되는 문제가 발생한다.

## 그러면?
`스레드 풀`을 사용하자
 

일정 개수 이상의 스레드를 생성하여 풀에 넣어 두고 요청이 들어올 때 마다 요청에 스레드를 할당하는 방식이다. 후에 요청 작업을 완료했다면 스레드를 다시 풀에 반납하면 된다.


이렇게 스레드 풀을 사용하면 스레드를 생성하고 종료하는 비용이 절약되고 응답이 빨라진다. 

## 스레드 풀의 스레드 개수 설정

1. 스레드의 개수를 낮게 설정 할 경우

    클라이언트의 동시 요청이 많아지면 요청들이 스레드를 사용하고 반납 할 때 까지 다른 요청들이 대기하거나 거부 당하는 문제가 발생한다.

2. 스레드의 개수를 높게 설정 할 경우

    동시 요청이 서버의 자원을 넘어서 들어올 경우 서버가 다운됨.
    
톰캣의 경우 스레드 풀의 기본 개수가 100개 정도로 되어 있음. 이러한 스레드 풀의 적정 수는 성능 테스트를 하며 정해야 한다. 성능 테스트를 위한 툴은 아파치 ab, 제이미터, nGrinder 등이 있다.

# 정리
서블릿 객체의 사용은 스레드 단위로 사용되고 이로 인하여 싱글톤 객체 사용시에 주의를 해야한다. 그리고 이러한 스레드는 일정 수를 미리 만들어 보관하는 스레드 풀을 기능을 사용하여 요청을 처리한다. 이러한 스레드의 수는 성능테스트를 통하여 적절한 값을 찾아야한다.