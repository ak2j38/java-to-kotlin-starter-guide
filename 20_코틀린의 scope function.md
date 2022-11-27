- `scope function이란?` 
    - 일시적인 영역을 형성하는 함수
    - 람다를 사용해 일시적인 영역을 만들고 코드를 더 간결하게 만들거나, method chaning에 활용하는 함수를 scope function이라고 합니다.
    
    ```kotlin
    // let은 scope function의 한 종류
    fun printPerson(person: Person?) {
    	person?.let {
    		println(it.name)
    		println(it.age)
    	}
    }
    ```
    
- `scope function의 종류`
    - let, run → 람다의 결과
    - also, apply → 객체 그 자체
    - with(확장함수 아님)
- `언제 어떤 scope function을 사용해야 할까?`
    - let
        - 하나 이상의 함수를 call chain 결과로 호출할 때
        - non-null 값에 대해서만 code block을 실행시킬 때
        
        ```kotlin
        val strings = listOf("Apple", "Car")
        strings.map { it.length }
        	.filter { it > 3 }
        	.let(::println)
        ```
        
    - run
        - 객체 초기화와 반환 값의 계산을 동시에 해야할 때
    - apply
        - test fixture를 만들 때
    - also
        - 객체 그 자체가 반환된다.
        - 객체를 수정하는 로직이 call chain 중간에 필요할 때
    - with
        - 특정 객체를 다른 객체로 변환해야 하는데, 모듈 간의 의존성에 의해 정적 팩토리 혹은 toClass 함수를 만들기 어려울 때
- `scope function과 가독성`
    
    ```kotlin
    // 1번 코드
    if (person != null && person.isAdult) {
    	view.showPerson(person)
    } else {
    	viewe.showError()
    }
    
    // 2번 코드
    perseon?.takeIf { it.isAdult }
    	?.let(view::showPerson)
    	?. view.showError()
    ```
