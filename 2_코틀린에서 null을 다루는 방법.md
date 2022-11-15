- Safe Call
    - null이 아니면 실행하고, null이면 실행하지 않는다
    
    ```kotlin
    val str: String? = "ABC"
    str.length // 불가능
    str?.length // 쌉가능
    ```
    
- Elvis 연산자 → `?:`
    - 앞의 연산 결과가 null이면 뒤의 값을 사용
    - Elvis 연산은 early return에도 사용할 수 있다!
    
    ```kotlin
    val str: String? = "ABC"
    str?.length ?: 0
    ```
    
- 널 아님 단언 → `!!`
    - nullable type이지만 아무리 생각해도 null이 될 수 없는 경우
    - 정말 확실한 경우에만 사용해야 함. 혹시나 null이 들어오면 바로 NPE 터짐!
    
    ```kotlin
    fun startsWithA1(str: String?): Boolean {
    	return str!!.startsWith("A")
    }
    ```
    
- 플랫폼 타입
    - kotlin에서 java 코드를 가져다 사용할 때 어떻게 처리될까?
    - 플랫폼 타입이란 코틀린이 null 관련 정보를 알 수 없는 타입
        - Runtime시 Exception이 날 수 있다.
