## @Component, @Controller, @Service, @Repository의 차이점

모두 Spring Bean으로 등록하는데 사용된다. 각각 특정한 기능을 담당한다. @Controller, @Service, @Repository는 내부적으로 @Component를 사용한다.

- @Component는 가장 일반적인 형태의 어노테이션으로, 특정 역할에 종속되지 않는 일반적인 Spring Bean을 나타냅니다. 공통 기능을 제공하는 유틸리티 클래스나, 특정 계층에 속하지 않는 일반적인 컴포넌트를 정의할 때 사용됩니다.

- @Service는 비즈니스 로직을 수행하는 클래스에 사용되며 서비스 레이어의 Bean을 나타냅니다.

- @Controller는 Spring MVC에서 웹 요청을 처리하는 컨트롤러 클래스에 사용되며 프레젠테이션 레이어의 Bean을 나타냅니다.

- @Repository는 데이터베이스와의 상호작용을 수행하는 클래스에 사용되며. 데이터 액세스 레이어의 Bean을 나타냅니다.

@Service, @Controller, @Repository는 각각 특정 계층을 나타내므로, AOP의 포인트컷을 정의할 때 유용하게 사용될 수 있습니다. @Component를 사용하면 이러한 계층 구분이 불분명해져 AOP 적용이 어려울 수 있습니다.