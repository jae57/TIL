####스프링이란,
##" 어떻게 오브젝트가 설계되고, 만들어지고, 어떻게 관계를 맺고 사용되는지에 관심을 갖는 프레임워크 "

스프링의 관심은 **오브젝트와 그 관계** 다.

---
오브젝트를 어떻게 설계하고, 분리하고, 개선하고, 어떤 의존관계를 가질지 결정하는 일은
스프링이 아니라 개발자의 역할이며 책임이다.

```
스프링은 단지 원칙을 잘 따르는 설계를 적용하려고 할 때
필연적으로 등장하는 번거로운 작업을 편하게 할 수 있도록 도와주는 도구일 뿐이다. (p.143)
```
```Java
제어자 정리 + 자바 8 인터페이스 관련 변경사항
protected abstract vs public abstract
```
01 [초난감 DAO](01.md)
02 [DAO의 분리](02.md)
03 [DAO의 확장](03.md)
04 [제어의 역전](04.md)
05 [스프링의 IoC](05.md)
06 [싱글톤 레지스트리와 오브젝트 스코프](06.md)
07 [의존관계 주입(DI)](07.md)
08 [XML을 이용한 설정](08.md)

[용어 정리](keyword.md)

_ 제어의 역전 / IoC

오브젝트가 생성되고 여타 오브젝트와 관계를 맺는 작업의 제어권을 별도의 오브젝트 팩토리를 만들어 넘겼다.
또는 오브젝트 팩토리의 기능을 일반화한 IoC 컨테이너로 넘겨서 오브젝트가 자신이 사용할 대상의 생성이나 선택에 관한 책임으로부터
자유롭게 만들어줬다.

_싱글톤 레지스트리

전통적인 싱글톤 패턴 구현 방식의 단점을 살펴보고, 서버에서 사용되는 서비스 오브젝트로서의 장점을 살릴 수 있는 싱글톤을
사용하면서도 싱글톤 패턴의 단점을 극복할 수 있도록 설계된 컨테이너를 활용하는 방법에 대해 알아봤다.

_의존관계 주입 / DI

설계 시점과 코드에는 클래스와 인터페이스 사이의 느슨한 의존관계만 만들어놓고, 런타임시에 실제 사용할 구체적인 의존 오브젝트를 제3자(DI 컨테이너)의 도움으로 주입받아서 다이내믹한 의존관계를 갖게 해주는 IoC의 특별한 케이스를 알아봤다.

_생성자 주입과 수정자 주입

의존 오브젝트를 주입할 때 생성자를 이용하는 방법과 수정자 메서드를 이용하는 방법을 알아봤다.

_XML 설정

XML을 이용해 DI 설정정보를 만드는 방법과 의존 오브젝트가 아닌 일반 값을 외부에서 설정해서 런타임 시에 주입하는 방법을 알아봤다.

용어 정리