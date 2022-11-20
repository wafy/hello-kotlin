# 코틀린 기본 문법

[1. 메인함수](#메인함수)
[2. 변수선언](#변수선언)
[3. 상수선언](#상수선언)
[4. 컴파일타입상수](#컴파일타입상수)
[5. 형변환](#형변환)
[6. 문자열](#문자열)
[7. 숫자다루기](#숫자다루기)
[8. 키보드입력받기](#키보드입력받기)
[9. 조건문](#조건문)
[10. 삼항연산](#삼항연산)
[11. 반복문](#반복문)
[12. 컬랙션](#컬랙션)
[13. 예외처리](#예외처리)
[14. 널세이프티](#널세이프티)
[15. 함수](#함수)
[16. 클래스](#클래스)
[17. 상속](#상속)
[18. 인터페이스](#인터페이스)
[19. 타입체크](#타입체크)
[20. 제네릭](#제네릭)
[21. 콜백함수](#콜백함수(고차함수))

## 메인함수

```kotlin

fun main() {
    println("hello world")
}
```

## 변수 선언

- 타입추론 기능이 있어서 형을 선언하지 않아도 된다.
- 모든타입이 레퍼런스 타입이다

```kotlin

fun main() {
    var i = 10
    var name = "호순이"
    var point = 3.3
    //명시적 변수 선언 
    var i: Int = 10
    var name: String = "호순"
    var point: Double = 3.3
}
```

## 상수 선언

```kotlin

fun main() {
    val num = 20 //final
}
```

## 컴파일타입 상수

- 클래스가 필수로 필요하지 않다.
- 함수 밖에 상수를 선언할 수 있다.

```kotlin
const val num = 20
fun main() {

}
```

## 형변환

```kotlin
fun main() {
    var i = 10
    var l = 20L
    var name = ""
    name = i.toString()

    var name = "10"
    i = name.toInt()
    l = i.toLong()
    i = l.toInt()
}
```

## 문자열

```kotlin
fun main() {
    var name = "hello"
    //대소문자 변화
    print(name.uppercase())
    print(name.lowercase())
    //문자열 접근
    println(name[0])

    //문자열 합치기 
    name = "호순"
    println("제 이름은 $name 입니다.")  //공백 있을 경우
    println("제 이름은 {$name}입니다.") //공백 없을 경우            
}
```

## 숫자 다루기

```kotlin
import java.lang.Integer.max

fun main() {
    var i = 10
    var j = 20

    //두개 중 큰 값을 얻을때
    println(max(i, j))
    println(Manth.max(i, j)) //코틀린에서는 사용하지 않도록 한다.

    //랜덤
    val randomNumber = Random.nextInt()
    //0~100까지 숫자중 랜덤 수 추출 
    val randomNumber1 = Random.nextInt(0, 100)
    println(randomNumber)
    println(randomNumber1)
}
```

## 키보드 입력받기

```kotlin
fun main() {
    val reader = Scanner(System.`in`)
    reader.nextInt()
    reader.next()
}
```

## 조건문

```kotlin
fun main() {
    var i = 5
    // if 문
    if (i > 10) {
        println("10보다 큽니다.")
    } else if (i > 5) {
        println("5보다 큽니다.")
    } else {
        println("")
    }

    // when 문 
    when {
        i > 10 -> {
            println("10보다 큽니다.")
        }
        i > 5 -> {
            println("5보다 큽니다.")
        }
        else -> {
            println("")
        }
    }

    //결과 리턴 받기 (식으로 취급)
    var result = if (i > 10) {
        "10 보다 크다 "
    } else if (i > 5) {
        "5보다 크다 "
    } else {
        "!"
    }
    println(result)

}
```

## 삼항연산

```kotlin
fun main() {
    var i = 5
    val result = if (i > 10) true else false
}
```

## 반복문

```kotlin
fun main() {
    val items = listOf(1, 2, 3, 4, 5)
    for (item in itmes) {
        println(item)
    }

    //foreach
    items.forEach { item ->
        println(item)
    }
    //for i
    for (i in items.size) {
    }
    for (i in 0..3) {

    }
    for (i in 0..(items.size - 1)) {
        println(items[i])
        break
        continue
    }
}
```

## 컬랙션

```kotlin
fun main() {
    //리스트
    val items = listOf(1, 2, 3, 4, 5) //변경불가 
    val items1 = mutableListOf(1, 2, 3, 4, 5) //변경가능 
    items1.add(6)
    items1.remove(5)

    //배열 
    val items = arrayOf(1, 2, 3)
    items.size //배열 크기 
    items.[0] = 10 //값대입    

}
```

## 예외처리

```kotlin
fun main() {
    val items = listOf(1, 2, 3)
    try {
        val item = items[4]
    } catch (e: Exception) {
        print(e.message)
    }
}
```

## 널세이프티

```kotlin
fun main() {
    val name: String = null //불가 
    val name: String? = null //가능 타입뒤에 ?
    name = "호순"

    // ?타입과 그냥 타입은 다른 타입으로 보기 때문에 null체크 필요
    var name1: String = ""
    name2 = name //불가 
    if (name != null) {
        name2 = name
    }

    //강제 타입 변환 
    name2 = name!! // 안티패턴 

    //내장함수 
    name?.let { //null아 아니면 블럭 실행
        name2 = name
    }
}
```

## 함수

```kotlin

fun main() {
    printn(sum(10, 20))
}

//탑래밸 함수 어느곳에서 사용 가능 
fun sum(a: Int, b: Int): Int {
    return a + b
}

//내용이 하나라면 간력히 사용 
fun sum(a: Int, b: Int) = a + b

//함수 오버로드 디폴트값 명시 
fun sum(a: Int, b: Int, c: Int = 0) = a + b + c

파리머터 변수 지정
sum(a = 10, b = 20)
sum(b = 20, a = 10) //파리미터 순서 바꾸어도 가능 
```

## 클래스

-- getter, setter 별도 필요 없다.

```kotlin

fun main() {
    val 호순이 = Persion("호순이", 8)
    println(호순이.name) //수정불가  
    println(호순이.age)
}

//자바스타일 
class Person {
    val name: String
    val age: Int
}

//코틀린 스타일 
//기본 생성자 바로 선언 가능
class Person(val name: String, var age: Int)

//getter 미사용 
class Person(
    private val name: String,
    var age: Int
)
// eqauls and hashcode 재정의 
// 클래스 앞에 data 명시

data class Person(
    val name: String,
    var age: Int
)

//생성자에 로직 추가 
// init 사용 
class Person(
    val name: String,
    var age: Int
) {
    init {
        println("init")
    }
}

//변수 사용 
class Person(
    val name: String,
    var age: Int
) {
    var hobby = "집돌이" //클래스 외부에서 변경 가능 
        //var hobby = "집돌이" private set  //외부에서 set 불가능 
        //getter 재정의 
        get() = "취미 : $field"

    init {
        println("init")
    }

    fun some() {
        hobby = "나가놀기"
    }
}
```

## 상속

- 자식클래스의 오버라이드는 기본으로 닫혀 있고 open 키워드를 써야만 가능하다.

```kotlin

fun main() {

}

abstract class Animal {
    //자식 클래스 오버라이드 가능 open
    open fun move() {
        //dosomthing
    }
}

class Dog : Animal() {
    override fun move() {
        super.move()
    }
}

class Cat : Animal()

//상속 가능 
open class Person
```

## 인터페이스

```kotlin

fun main() {

}

interface Drawable {
    fun draw()
}

class Dog : Drable {
    override fun draw() {

    }
}
```

## 타입체크

```kotlin

fun main() {
    val dog = Dog()
    val cat = Cat()
    //is 
    if (dog is Dog) {
        println("같다")
    }
    
    val dog: Animal = Dog()
    if (dog is Dog) {
        print("같다")
    }    
    
    // 타입 캐스팅 as
    cat as Dog
}

interface Drawable {
    fun draw()
}

class Dog : Drawable {
    override fun draw() {

    }
}

class Cat : Drawable {
    override fun draw() {

    }
}
```
## 제네릭 
```kotlin

fun main() {
    val box = Box<Int>(10) 
    //Int 생략가능 
    val box = Box(10)
    println(box.value)
}

class Box<T>(val value: T)  
```

## 콜백함수(고차 함수)
```kotlin
fun main() {
    myFunc({
        println("함수 호출")
    })
    //추천식 
    myFunc() {
        println("함수 호출")
    } 
    
    //함수하나만 있을 경우 () 생략 가능
    myFunc {
        println("함수 호출")
    }
    
    myFunc(10) {
        
    }    
}


//input이 없고 리턴이 void 
fun myFunc(callBack: () -> Unit) {
    println("함수 시작")
    callback()
    println("함수 끝")
}

//suspend 함수 선언 
//함수가 끝날때까지 대기 
//메인 함수에서 사용할 수 없다.
suspend fun myuFunc{ }

```