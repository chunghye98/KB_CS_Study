7. Synchronized 키워드에 대해 설명해 주세요.
> 면접
멀티스레드 환경에서 동시에 여러 스레드가 동일한 자원에 접근하는 것을 제어하기 위해 사용하는 키워드입니다.
synchronized 메서드나 블록은 해당 객체 또는 클래스에 대한 락을 획득해야 실행이 가능하며
다른 스레드가 이미 락을 획득한 상태라면, 현재 스레드는 락이 해제될 때까지 대기해야 합니다.
즉, 자원에 대한 접근을 1개의 스레드만 가능하게 만들어서 데이터 일관성을 유지해줍니다.

> 공부
멀티스레드 환경에서 동기화된 블록/메서드를 정의하여 동시에 여러 스레드가 동일한 자원에 접근하는 것을 제어하기 위해 사용.
-> 자원에 대한 접근을 1개의 스레드만 가능하게 만들어 데이터의 일관성 유지

-------------------

- Synchronized 키워드가 어디에 붙는지에 따라 의미가 약간씩 변화하는데, 각각 어떤 의미를 갖게 되는지 설명해 주세요.
> 면접
인스턴스 메서드에 붙일 시 그 메서드를 호출하면 현재 객체(this)에 대한 락을 획득합니다. 이는 객체 레벨에서 동기화가 이뤄집니다.
정적 메서드에 붙일 시 해당 클래스 객체(class, object)에 대한 락을 획득합니다.
특정 블록에 지정하여 특정 코드 블록만 동기화할 수 있습니다. 해당 객체에 대한 락을 사용하지만,
메서드 전체가 아닌 특정 부분만 동기화할 수 있습니다.

> 공부
1) 인스턴스 메서드
메서드 호출 시 현재 객체(this)에 대한 락을 획득
멀티스레드 환경에서 해당 메서드에 하나의 스레드만 접근 가능

2) 정적 메서드
해당 클래스 객체(Class, object 등)에 대한 락을 획득

3) 블록
특정 코드 블록 실행 시 지정한 블록에 대한 락을 획득

-------------------

- 효율적인 코드 작성 측면에서, Synchronized는 좋은 키워드일까요?
> 면접&공부
코드 작성 측면에서는 재진입이 가능하기에 Synchronized 키워드를 한번만 사용해도 동기화할 수 있어서 좋다고 생각합니다.

하지만 코드 작성 측면이 아닌 다른 부분을 고려했을 때
스레드가 락을 획득/해제하는 데 오버헤드가 발생하고 불필요하게 많은 부분을 동기화하면 성능이 저하될 수 있습니다.
또, 락을 획득하기 위해 대기하는 시간이 길어질 수 있고, 그 때 데드락 상황이 발생할 위험이 있기에 단점이 더 커서 좋은 키워드라고 생각하지 않습니다.

-------------------

- Synchronized 를 대체할 수 있는 자바의 다른 동기화 기법에 대해 설명해 주세요.
> 면접&공부
1) ReentrantLock
synchronized 블록과 비슷하게 동기화를 제공
락을 시도해 보고 실패하는 경우 다른 작업을 수행하는 등의 로직을 구현 가능
2) ReadWriteLock
읽기 작업과 쓰기 작업을 분리하여 동기화
다수의 스레드가 동시에 읽을 수 있지만, 쓰기 작업이 있을 때는 하나의 스레드만 접근 가능
3) java.util.concurrent 패키지
여러 동시성 컬렉션 제공
내부적으로 동기화가 되어 있어, 별도의 동기화 없이 멀티스레드 환경에서 안전하게 사용 가능
ex) ConcurrentHashMap, CopyOnWriteArrayList, ConcurrentLinkedQueue

-------------------

- Thread Local에 대해 설명해 주세요.
> 면접
스레드 로컬 변수를 생성할 수 있도록 도와주는 유틸리티 클래스 입니다.
스레드 로컬 변수는 각 스레드마다 독립적인 값을 저장할 수 있게 합니다. 다른 스레드와 공유되지 않습니다.
이는 멀티스레드 환경에서 데이터 일관성을 유지할 수 있습니다.
스레드 종료 시 ThreadLocal 변수는 자동으로 정리되어 메모리 누수를 방지합니다.

> 공부
스레드 로컬 변수를 생성할 수 있도록 도와주는 유틸리티 클래스
1) 스레드 로컬 변수는 각 스레드마다 고유한 값을 가지며, 다른 스레드와 공유되지 않음 -> 멀티스레드 환경에서 데이터 일관성 유지
2) ThreadLocal은 기본값 제공을 위해 초기화 메서드 정의 가능 -> initialValue 메서드를 재정의하여 초기값을 제공하는 방법
3) 스레드 종료 시 ThreadLocal 변수는 자동 정리 -> 메모리 누수 방지
