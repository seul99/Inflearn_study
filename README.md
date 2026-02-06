fun main() {
    print("Hello World")
    println
}

자바와 차이점 -> 세미콜론이 없다.
print, println 둘다 존재

### 변수 상수
코틀린은 별도로 타입을 지정안해도 된다.

    var i : Int = 10
    이런 식으로 명시적으로 지정 가능

    모두 래퍼클래스 처럼 대문자로 시작해서 명시적으로 지정해야함

    변수 : var
    상수 : val 
   차이점 : 변수는 재 대입 가능 상수는 불가능 (상수는 자바의 final 과 유사)

### 톱레벨 상수
제일 위에 const 를 붙여서 함수 생성
- 자바는 항상 class 필요
- 코틀린은 필요없음

- const val num = 20

fun main() {
    var i : Int = 10
    var name : String = "준석"
    var point : Double = 3.3

    i = 20


}

이런식 선언 가능

## 형변환
fun main() {

    var i = 10
    var l = 20L
    
    l = i
}

이렇게 있을때 형변환 안되서 임의로 변경해줘야함

  var i = 10
    var l = 20L

    l = i.toLong()

## 스트링
    var name = "seulgi"
    print(name.uppercase())
    print(name.lowercase())
    print(name[0])
    print("제 이름은 " + name + "입니다.")
    print("제 이름은 ${name}입니다.")

    자바에서 할 수 있는거 다 가능
    ${ } 를 통해서 변수 바로 선언 가능

## max 함수
    var i = 10
    var j = 20
    print(kotlin.math.max(i, j))

## random
import kotlin.random.Random
fun main() {
    var randomNumver = Random.nextInt(0, 100)

    print(randomNumver)
}
0 포함 100 포함안함

## 키보드 입력
    var reader = Scanner(System.in)
    reader.nextInt()
    reader.next()
자바에서 쓰는거 그대로 쓸 수 있다.

## 조건문
    val i = 5

    if(i > 10){
        print("10 보다 크다")
    } else if (i > 5){
        print("5 보다 크다")
    } else {
        print("")
    }

    when {
        i > 10 -> {
            print("10 보다 크다")
        }
        i > 5 -> {
            print("5 보다 크다")
        }else-> {
            print("")
        }
    }

    var result = if(i > 10){
        "10 보다 크다"
    } else if (i > 5){
        "5 보다 크다"
    } else {
        "!!!!!"
    }

    코틀린은 if 문이 식으로 취급받아서 변수에 저장이 가능하다.

    자바는 삼항연산자가 존재함
    자바 : boolean result = i > 10 ? true : false;
    코틀린 : val result = if(i > 10 ) true else false
    
    
## 반복문
    val items = listOf(1,2,3,4,5)

    for (item in items) {
        print(item)
    }

    items.forEach {
        item -> print(item)
    }

    // for(int i = 0; i < items.length; i++)
    for (i in 0..3) {
        print(i)
    }
    // 3포함함

    for (i in 0..(items.size-1)) {
        print(items[i])
        
    }

    break
        continue
        동일하게 제공함

        while 문도 동이랗게 제공함
        
## List
    val items = listOf(1,2,3,4,5) // 변경이 안되는 리스트

    val itmes2 = mutableListOf(1,2,3,4,5)
    itmes2.add(6)
    itmes2.remove(3)

    타입은 다 생략이 된다.
    코틀린은 타입이 생략가능한것이기 때문, 타입을 추론함


## Array
val items = arrayOf(1,2,3)
    items.set(0, 10) // 자바 형식

    items[0] = 10 // 코틀린형식

    // 배열은 잘 안쓰니까 왠만하면 리스트 사용하기
    
## Null Safety
코틀린에서는 널을 넣을려면 ? 를 대입해야함
? 여부에 따라서 타입이 다르게 된다.
널체크를 하거나 강제타입변환해야함

    var name : String? = null
    name = "seulgi"

    name = null

    var name2 : String = ""

    name2 = name!! // 강제로 타입 때기 -> 에러나면 개발자 책임이ㅣㄱ 때문에 널체크해야함

    // if 문으로 널체크 하기
    if (name != null) {
        name2 = name
    }

    // 널체크 문법
    name?.let {
        name2 = name
    }

## 함수

fun main() {
    print(sum(10, 20))

}

fun sum(a:Int, b:Int): Int {
    return a+b
}

or

fun sum(a:Int, b:Int): Int = a+b 

함수는 탑레벨 함수이기 때문에 어느 파일에서나 사용가능

자바는 오버로드를 통해서 같은 함수명에 다른 파라미터가 가능
fun sum(a:Int, b:Int, c: Int = 0): Int = a+b+c
코틀린에서는 디폴트값을 지정해서 가능

fun main() {
    print(sum(a = 10, b = 20))

}

이렇게 입력 파라미터를 명시적으로 지정이 가능하기 때문에 틀리기 쉽지않고 가독성도 좋다.

## Class

fun main() {
    val john = Person("John", 20)
    print(john.name)
    print(john.age)
}

class Person(val name:String, var age: Int)

val 로 선언한건 수정 불가능, var 로 만든건 수정 가능
val과 var 를 통해서 getter, setter 효과를 구현할 수 있다.

## data class
class Person(
    private val name:String, var age: Int)

    이렇게 private 을 붙이면 접근이 불가능하다.
    기본적으로는 public



## getter, setter

fun main() {
    val john = Person("John", 20)
    val john2 = Person("John", 20)
    println(john)
    println(john2)
    print(john == john2)
}
com.mysite.Person@31befd9f
com.mysite.Person@1c20c684
false

서로 해시값이 다르기 떄문에 == 비교 했을때 false 가 나옴

data class Person(
    private val name:String, var age: Int)

    클래스에 data 를 추가하면?

    Person(name=John, age=20)
Person(name=John, age=20)
true

이렇게 정리가 되서 출력됨

fun main() {
    val john = Person("John", 20)
    val john2 = Person("John", 20)
    println(john)
    println(john2)
    print(john == john2)

    john.hobby = "야구"
}

class Person(
    private val name:String, var age: Int) {

    var hobby = "축구"


    init {

        print("init")
    }

    fun some() {
        hobby = "농구"
    }
}



## getter, setter 제어

    var hobby = "축구"
        private set

이렇게 하면 외부에서 접근 불가능해짐
        var hobby = "축구"
            private set
            get() = "취미: $field" 
        이렇게 재 정


## 상속 extends

자바는 기본적으로 모든게 허용
코틀린은 닫혀있음 상속이 안됨
open 으로 오버라이드를 풀어줘야

open class Person 
abstract class Animal {
    open fun move() {
        print("이동")
    }
}

class SuperMan : Person() 


class Dog : Animal(){
    override fun move() {
        println("껑충껑충")
    }
}

class Cat : Animal() {
    override fun move() {
        println("슬금슬금")
    }
}

상속이 가능하다.

## interface

interface Drawable {
    fun draw()
}
abstract class Animal {
    open fun move() {
        print("이동")
    }
}

class Dog : Animal(), Drawable{
    override fun move() {
        println("껑충껑충")
    }

    override fun draw() {}
}


인터페이스는 콤마찍고 뒤에 이어서 상속 가

## 타입 체크 is
    // 타입 체크
    if(dog is Dog) {
        println("멍멍이")
    }
    if(dog is Animal) {
        println("멍멍이")
    }

    if(dog is Cat) {
        println("멍멍이")
    }


## 강제 타입 변환 as

cat as Dog

제너릭 선언 사용
fun main() {
    val box = Box(10)
    val box2 = Box("dfdfdf")

    print(box.value)
}

class Box<T>(var value: T) {

}


## 콜백 합수(고차함수)
fun main() {
    myFunc (10){
        println("함수 호출")
    }
}

fun myFunc(a: Int,  callBack : () -> Unit = {}) {
    println("함수 시작!!!")
    callBack()
    println("함수 끝")
}


## 코루틴
suspend 붙은 함수는 일반적으로 main에서 그냥 호출이 불가
lifecycleScope.launch {
        myFunc(10){
            
        }
    }

    이렇게 해야 사용가능

    의존성 주입 추가 필수
