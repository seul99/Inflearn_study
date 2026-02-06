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

## Array

## Null Safety

## 함수

## Class

## data class

## getter, setter

## getter, setter 제어

## 상속 extends

## interface

## 타입 체크 is

## 강제 타입 변환 as

## 콜백 합수(고차함수)

## 코루틴


