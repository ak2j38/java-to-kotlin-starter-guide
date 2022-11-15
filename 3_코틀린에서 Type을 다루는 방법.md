- 코틀린은 선언된 기본값을 보고 타입을 추론한다.
- 코틀린에서 타입변환은 명시적으로 이루어져야 한다.
    - `.to변환타입()`을 사용해야 한다.
    
    ```kotlin
    val number1 = 3
    val number2: Long = number1.toLong()
    ```
    
- 변수가 nullable이면 적절한 처리 필요하다.
- `is, !is, as, !as`
- `Any`
    - Java의 Object 역할(모든 객체의 최상위 타입)
    - 모든 Primitive Type의 최상위 타입도 Any이다.
    - Any 자체로는 null을 포함할 수 없어 null을 포함하고 싶다면, Any?로 표현
    - Any에 equals, hashcode, toString 존재
- `Unit`
    - Unit은 Java의 void와 동일한 역할
    - void와 다르게 Unit은 그 자체로 타입 인자로 사용 가능하다
    - 함수형 프로그래밍에서 Unit은 단 하나의 인스턴스만 갖는 타입을 의미
    - 즉 코틀린의 Unit은 실제 존재하는 타입이라는 것을 표현
- `Nothing` → 잘 안씀
    - Nothing은 함수가 정상적으로 끝나지 않았다는 사실을 표현하는 역할
    - 무조건 예외를 반환하는 함수, 무한루프 등
- `String interpolation, String indexing`
    - 중괄호 없이 변수만 사용해도 되지만 통일성을 위해 중괄호 쓰는 것 추천

    ```kotlin
    val person = Person("박우진", 30)
    val log = "이름은 ${person.name}, 나이는 ${person.age}이다" 

    --------------------------------------------------------

    """
    ABC
    DEF
    박우진
    """
    -> 
    ABC
    DEF
    박우진

    --------------------------------------------------------

    val str = "ABCDE"
    val ch = str[1]
    -> B
    ```
