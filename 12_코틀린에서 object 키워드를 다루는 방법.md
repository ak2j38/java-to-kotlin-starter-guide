- `static 함수와 변수`
    
    ```kotlin
    class Person private constructor(
    	var name: String,
    	var age: Int,
    ) {
    	
    	companion object {
    		private const val MIN_AGE = 1
    		fun newBaby(name: String): Person {
    			return Person(name, MIN_AGE)
    		}
    	}
    }
    ```
    
    - Java의 static 변수와 함수를 만들려면, Kotlin에서는 `companion object`를 사용해야 한다.
    - companion object, 즉 동반객체도 하나의 객체로 간주된다. 때문에 이름을 붙일 수도 있고, interface를 구현할 수도 있다.
    - 자바에서 Kotlin companion object에 접근하려면 `@JvmStatic` 이라는 어노테이션을 붙이거나 `Person.Companion.newBaby()` 로 접근한다.
- `싱글톤`
    - 코틀린에서는 앞에 `object` 만 붙여주면 된다.
- `익명클래스`
    
    ```kotlin
    fun main() {
    	moveSomething(object : Movable
    		override fun move() {
    			println("무브 무브")
    		}
    
    		override fun fly() {
    			println("날다 날다")
    		}
    	})
    }
    
    private fun moveSomething(movable: Movable) {
    	movable.move()
    	movable.fly()
    }
    ```
