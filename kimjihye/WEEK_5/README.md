목적이 유사함에도 불구하고
환경과 상황에 따라 기술이 바뀌고,
그에 따라 다른 API를 사용하는 것은

<p align="left">
<img width="80" src="../images/icons/tired.png"><br>
</p>

매우 피곤하다..

# 서비스 추상화
> 스프링이 어떻게 성격이 비슷한 여러 종류의 기술을 추상화하고
> 이를 일관된 방법으로 사용할 수 있도록 지원하는지를 살펴보자.

### `UserDao`
```
User 객체에 담겨있는 사용자 정보를
등록, 조회, 수정, 삭제하는 (일명 CRUD) 가장 기초적인 작업만 가능.
비즈니스 로직 X
```
[비즈니스 로직을 추가해보자](01.md)<br>

이제
사용자 레벨 관리 기능에 대한 구현을 마쳤고,
테스트를 통한 검증도 끝났다.

```
"어떤 작업을 수행하는 도중에 네트워크가 끊기거나 서버에 장애가 생겨서
작업을 완료할 수 없다면, 그때까지 변경된 것들은 그대로 둘까요?
아니면 모두 초기 상태로 되돌려 놓아야 할까요?"
```

[트랜잭션 서비스 추상화](02.md)<br>






### 스프링의 서비스 추상화
비즈니스 로직을 담은 UserService 클래스를 만들고 트랜잭션을 적용한다.





03 [서비스 추상화와 단일 책임 원칙](03.md)<br>
04 [메일 서비스 추상화](04.md)<br>


- 비즈니스 로직을 담은 코드는 데이터 액세스 로직을 담은 코드와 깔끔하게 분리되는 것이 바람직하다. 비즈니스 로직 코드 또한 내부적으로 책임과 역할에 따라서 깔끔하게 메서드로 정리돼야 한다.

- 이를 위해서는 DAO의 기술 변화에 서비스 계층의 코드가 영향을 받지 않도록 인터페이스와 DI를 잘 활용해서 결합도를 낮춰줘야 한다.

- DAO를 사용하는 비즈니스 로직에는 단위 작업을 보장해주는 트랜잭션이 필요하다

- 트랜잭션의 시작과 종료를 지정하는 일을 트랜잭션 경계설정이라고 한다.
  트랜잭션 경계설정은 주로 비즈니스 로직 안에서 일어나는 경우가 많다.

- 시작된 트랜잭션 정보를 담은 오브젝트를 파라미터로 DAO에 전달하는 방법은 매우 비효율적이기 때문에 스프링이 제공하는 트랜잭션 동기화 기법ㅇ을 활용하는 것이 편리하다.

- 자바에서 사용되는 트랜잭션 API의 종류와 방법은 다양하다. 환경과 서버에 따라서 트랜잭션 방법이 변경되면 경계설정 코드도 함께 변경돼야 한다.

- 트랜잭션 방법에 따라 비즈니스 로직을 담은 코드가 함께 변경되면 단일 책임 원칙에 위배되며, DAO가 사용하는 특정 기술에 대해 강한 결합을 만들어낸다.

- 트랜잭션 경계설정 코드가 비즈니스 로직 코드에 영향을 주지 않게 하려면 스프링이 제공하는 트랜잭션 서비스 추상화를 이용하면 된다.

- 서비스 추상화는 로우레벨의 트랜잭션 기술과 API의 변화에 상관없이 일관된 API를 가진 추상화 계층을 도입한다.

- 서비스 추상화는 테스트하기 어려운 JavaMail 같은 기술에도 적용할 수 있다.
  테스트를 편리하게 작성하도록 도와주는 것만으로도 서비스 추상화는 가치가 있다.

- 테스트 대상이 사용하는 의존 오브젝트를 대체할 수 있도록 만든 오브젝트를 테스트 대역이라고 한다.

- 테스트 대역은 테스트 대상 오브젝트가 원활하게 동작할 수 있도록 도우면서 테스트를 위해 간접적인 정보를 제공해주기도 한다.

- 테스트 대역 중에서 테스트 대상으로부터 전달받은 정보를 검증할 수 있도록 설계된 것을 목 오브젝트라고 한다.