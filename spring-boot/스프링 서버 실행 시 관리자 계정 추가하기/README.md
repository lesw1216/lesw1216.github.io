# 스프링 서버 실행 시 관리자 계정 추가하기
서버를 실행 할 때 관리자 계정을 기본적으로 추가해야 한다. 

스프링 부트는 서버가 실행되면서 같이 코드를 실행할 수 있게 지원해주는데 이는 `CommandLineRunner`, `ApplicationRunner` 인터페이스를 구현하여 수행 할 수 있다.

이 두개의 인터페이스는 `SpringApplication.run()`이 완료되기 전에 호출된다.

이 둘의 차이점은 다음과 같다.

* `CommandLineRunner` - application argument에 String array가 들어온다.

* `ApplicationRunner` - application argument에 `ApplicationArgument` 타임의 객체가 들어온다.

> `ApplicationArgument` 인터페이스 
>
> `SpringApplication.run()`의 매개변수로 받은 문자열 배열과 파싱된 option, non-option 인자에 대한 액세스를 제공하는 인터페이스다. 구현체는 `DefaultApplicationArgument`가 있다.

## 다수의 CommandLineRunner, ApplicationRunner가 존재하는 경우

다수의 구현체들이 존재하는 경우 `configure`를 생성하여 실행되는 순서를 지정할 수 있다. 이때, `Ordered` 인터페이스를 구현하거나, `Order` 어노테이션을 사용한다.

# CommandLineRunner 실제 적용하기
```java
@Slf4j
@Component
@RequiredArgsConstructor
public class AdminAccountInitializer implements CommandLineRunner {

    private final MemberService memberService;

    @Override
    @Transactional
    public void run(String... args) throws Exception {
        String adminEmail = "관리자 계정 아이디";
        String password = "관리자 계정 비밀번호";

        MemberIdPwdDTO memberIdPwdDTO = MemberIdPwdDTO.builder()
                .email(adminEmail)
                .password(password)
                .build();

        Member savedAdmin = memberService.save(memberIdPwdDTO, 1, 1);
        log.info("Saved admin: {}", savedAdmin);
    }
}
```

관리자를 저장하기 위해 `MemberService`를 주입해주었다. 주의할 점은 `AdminAccountInitializer`는 bean으로 등록되어야 한다.