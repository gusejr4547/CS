## @Component, @Controller, @Service, @Repository의 차이점

모두 Spring Bean으로 등록하는데 사용된다. 각각 특정한 기능을 담당한다. @Controller, @Service, @Repository는 내부적으로 @Component를 사용한다.

- @Component는 가장 일반적인 형태의 어노테이션으로, 특정 역할에 종속되지 않는 일반적인 Spring Bean을 나타냅니다. 공통 기능을 제공하는 유틸리티 클래스나, 특정 계층에 속하지 않는 일반적인 컴포넌트를 정의할 때 사용됩니다.

- @Service는 비즈니스 로직을 수행하는 클래스에 사용되며 서비스 레이어의 Bean을 나타냅니다.

- @Controller는 Spring MVC에서 웹 요청을 처리하는 컨트롤러 클래스에 사용되며 프레젠테이션 레이어의 Bean을 나타냅니다.

- @Repository는 데이터베이스와의 상호작용을 수행하는 클래스에 사용되며. 데이터 액세스 레이어의 Bean을 나타냅니다.

@Service, @Controller, @Repository는 각각 특정 계층을 나타내므로, AOP의 포인트컷을 정의할 때 유용하게 사용될 수 있습니다. @Component를 사용하면 이러한 계층 구분이 불분명해져 AOP 적용이 어려울 수 있습니다.

## 스프링에서 비동기 처리
스프링에서는 @Async 어노테이션을 사용하여 비동기 처리를 수행할 수 있다. 

주의점이 있다. 기본적으로 @Async 가 적용된 메서드에서 발생하는 예외는 호출자에게 전파되지 않는다. 

비동기 메서드에서 예외를 정상적으로 처리하기 위해서는 별도의 비동기 예외 처리를 해야한다. 

그리고, 비동기 메서드 내에서 생성한 트랜잭션은 상위 트랜잭션과 무관한 생명주기를 가진다.

### ThreadPoolTaskExecutor를 활용한 스레드 관리
@Async 어노테이션을 사용할 때, 별도의 TaskExecutor를 설정을 해주지 않으면, SimpleAsyncTaskExecutor가 기본적으로 사용된다.

SimpleAsyncTaskExecutor는 스레드 풀을 사용하지 않고, 매 요청마다 새로운 스레드를 생성해 작업을 수행한다.

만약 1000명의 사용자가 동시에 인증 메일 전송 요청을 한다면, 1000개의 스레드를 생성하려하고 이는 리소스 부족 문제로 이어지기 쉽다.

따라서 ThreadPoolTaskExecutor와 같은 스레드 풀 기반의 TaskExecutor을 사용하도록 설정해야한다.