### 인터페이스와 추상 클래스의 차이에 대해 설명해 주세요.

꼬리질문
1. 인터페이스에 디폴트, 정적 메서드가 추가된 이유? 추상 메서드를 사용하면 되는 것 아닌가요?
2. 인터페이스와 추상클래스 각각 어떤 상황에서 사용하면 좋을까요?
3. DI에서 인터페이스가 중요한 이유가 무엇인가요?

<img src="./Day01_difference.PNG"/>

- 인터페이스에 디폴트, 정적 메서드가 추가된 이유? 추상 메서드를 사용하면 되는 것 아닌가요?
    
    디폴트 추가 이유 → 기존 인터페이스에 새로운 메서드 추가 시 인터페이스를 구현하는 모든 클래스에 영향을 주지 않고 새로운 메서드를 추가할 수 있음
    
    정적 메서드 → 인터페이스와 관련된 유틸리티 메서드 제공 가능
    
- 인터페이스와 추상클래스 각각 어떤 상황에서 사용하면 좋을까요?
    
    인터페이스 → 다중 상속이 필요할 때 (여러 행동 구현)
    
    추상클래스 → 여러 클래스에 걸쳐 공통된 코드가 있는 경우 추상클래스에 넣어 중복 줄임, 상태와 행위를 함께 정의해야할 때
    
- DI에서 인터페이스가 중요한 이유가 무엇인가요?

    객체지향 설계원칙(SOLID) 중 개방 폐쇄 원칙, 의존성 역전 원칙을 기반한 전략 패턴
    
    1. 개방 폐쇄의 원칙(Open-Closed Principle) 준수

    컨트롤러 입장에서는 Service 클래스의 비즈니스 로직에 대해서는 관심이 없다.그냥 인터페이스에 있는 메소드를 이용해 로직을 구성할 뿐이기 때문에 Service 클래스의 내부 로직이 어떻게 변하던 영향을 받지 않는다. (변화에 닫혀 있다.)반대로 Service 클래스는 인터페이스에서 규정된 규칙만 잘 지키면 언제든 로직을 변경할 수 있고,인터페이스를 구현한 새로운 클래스를 하나 만들어서 기존 클래스를 대체할 수도 있다. (확장에는 열려 있다.)

    2. 의존성 역전 원칙(Dependency Inversion Principle) 준수

    Service 클래스가 인터페이스를 구현하고 있다면 코드 상에서 컨트롤러는 인터페이스만을 바라보고 있다.인터페이스는 컴파일 시점에 어떤 클래스를 담을지 결정하지 않고 런타임 시점에 스프링 컨테이너에 존재하는 인터페이스 구현체 빈 중 하나를 주입받게 된다.즉, 구현체가 런타임 시점에 지정되므로 컨트롤러는 실제 구현 클래스가 누군지 런타임 시점까지 알지 못하며, 컨트롤러와 서비스는 느슨한 결합도를 가지게 된다.
    
    코드 유연성 높임 : 구현 클래스 쉽게 교체 가능
    
    새로운 기능 쉽게 추가 : 새로운 인터페이스 추가하는 것으로 기능 확장 가능