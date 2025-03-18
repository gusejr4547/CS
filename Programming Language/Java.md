## 자바에서 Checked Exception과 Unchecked Exception
Checked Exception은 컴파일 시점에 확인되는 예외. 수정되지 않으면 실행할 수 없습니다. IOException, SQLException 등이 있습니다. throws 나 try-catch를 사용해서 예외처리를 반드시 해야합니다.

Unchecked Exception은 런타임에 확인되는 예외. RuntimeException을 상속한 예외들이 속합니다. NullPointerException 등등.

## Error와 Exception의 차이는 무엇인가요?
Error는 프로그램에 심각한 영향을 미치는 오류입니다. OutOfMemoryError, StackOverflowError 등이 있습니다.

Exception은 프로그램 실행중에 발생할 수 있는 오류입니다. 프로그램에서 예외처리를 통해 회복 가능성이 있습니다.

## 얕은 복사, 깊은 복사

자바에서 객체 복사할 때 2가지 방법이 있다. 

얕은 복사는 원본과 동일한 주소를 가리킨다. 동일한 참조값을 가지는 것. shallowCopy()

깊은 복사는 같은 값을 가진 객체를 새로 생성하는 것. deepCopy()

## equals와 hashCode는 왜 함께 정의해야 하는가?
둘 다 객체의 동일함을 비교하기 위한 메서드입니다. 하지만 함께정의하지 않으면 예상하지 못한 결과가 발생할 수 있습니다.

HashMap이나 HashSet 등등 해시값을 사용하는 자료구조를 사용하는 경우 hashCode를 사용해 객체를 비교한 뒤 equals를 사용해 같음을 판단합니다. hashCode를 정의하지 않으면 Object클래스의 hashCode를 사용하게 되는데, 이거는 객체의 할당 주소를 반환하기 때문에 객체마다 다른 값을 반환합니다.