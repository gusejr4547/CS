## Spring Data JPA에서 새로운 Entity인지 판단하는 방법은 무엇일까요?

새로운 Entity인지 아닌지 판단해야하는 상황

save() 호출할때 이 엔티티가 새로운것인지 기존 데이터인지 판단해야한다.

일반적으로 @Id 값이 null 인 경우 새로운 엔티티로 판단한다. DB에 insert 수행한다.

@Id 값이 있는 경우에는 DB에 조회를 한 뒤 있으면 update, 없으면 insert를 수행한다.

Spring Data JPA에서 새로운 엔티티를 판단하는 메서드는 isNew() 메서드이다.

### 새로운 Entity인지 판단하는게 왜 중요한가?

save()에서 isNew()를 사용해 persist할것인지 merge할것인지 결정하는데 ID를 직접 지정하는 경우 새로운 엔티티여도 merge를 수행하기 때문에 DB에서 조회가 발생해 비효율적으로 동작한다.

직접 ID를 할당하는 경우에는 엔티티 클래스를 만들때 @Version을 사용하거나 직접 isNew를 오버라이딩해서 로직을 구현하는 방법이 있다.