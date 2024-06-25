### 리플렉션에 대해 설명해 주세요.

꼬리질문

1. 스프링에서 DI 시 리플렉션을 어떻게 사용하는지 설명해주세요.



- **힙 영역에 로드 된** class 타입의 객체를 통해 원하는 클래스의 인스턴스를 생성할 수 있도록 지원

- 인스턴스의 필드와 메소드를 **접근제한자와 상관없이** 사용할 수 있도록 지원하는 API

- **구체적인 클래스 타입을 몰라도** 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API
- **런타임**에 클래스와 인터페이스 등을 검사하고 조작할 수 있는 기능


→ 작성 시점에는 어떤 클래스를 사용해야할지 모르지만 런타임 시점에 가져와 실행해야하는 경우에 사용

ex) IntelliJ 자동완성 기능, 스프링 어노테이션


리플렉션으로 조작할 수 있는 정보

필드, 클래스, 생성자, 메서드, 어노테이션

장점

- 구체적인 클래스를 몰라도 동적으로 클래스를 만들어서 의존 관계 맺을 수 있음

- 접근 제한자가 private여도 접근해서 조작 가능 → private 메서드도 테스트 가능

+) 좀 더 쉬운 설명

일반적인 코드에서 클래스 사용 시 이름 알아야함

리플렉션 사용 시 런타임에 클래스 이름을 몰라도 클래스를 불러오거나 클래스 안에 있는 메서드, 변수 조작 가능

→ 프로그램이 스스로 자신의 코드를 볼 수 있는 것 같은 느낌