## Hello World 출력
```
fun main() {
    print("Hello World")
    println()
}
```
### 자바와의 차이점
- 세미콜론(;)을 쓰지 않아도 된다
- print, println 둘 다 존재
- print : 줄바꿈 없음
- println : 줄바꿈 포함

## 변수와 상수
코틀린은 타입 추론(Type Inference) 을 지원해서 <br>
타입을 명시하지 않아도 자동으로 타입을 판단해준다.

`var i = 10`

타입을 명시적으로 지정하고 싶을 때 <br>
`var i: Int = 10`


코틀린의 기본 타입들은 모두 래퍼 클래스처럼 대문자로 시작 <br>
`Int`, `Long`, `Double`, `String` 등

자바의 `int`, `long `같은 `primitive` 타입 개념이 없다

```
var vs val
var i = 10
val name = "준석"
```

`var` : 변수 → 값 재할당 가능 <br>

`val` : 상수 → 값 재할당 불가능 <br>
→ 자바의 final 과 거의 동일한 개념

```
var i = 10
i = 20   // 가능

val name = "준석"
name = "영희" // ❌ 에러
```

## 톱레벨 상수 (Top-level Constant)
코틀린은 클래스 없이도 상수를 선언할 수 있다. <br>

```
const val NUM = 20
```

### 특징
- 파일 최상단에 선언
- `const val` 키워드 사용
- 자바처럼 항상 class 안에 있을 필요 ❌

> 이게 가능한 이유는 코틀린이 파일 단위로 코드를 관리하기 때문

### 변수 선언 예시
```
fun main() {
    var i: Int = 10
    var name: String = "준석"
    var point: Double = 3.3

    i = 20
}
```

타입을 명시해도 되고  <br>

안 해도 된다 (상황에 따라 선택)  <br>

## 형변환
코틀린은 자동 형변환을 지원하지 않는다.

```
fun main() {
    var i = 10
    var l = 20L

    l = i   // ❌ 에러
}
```

자바에서는 암묵적 형변환이 되지만, <br>
코틀린에서는 명시적으로 변환해야 한다. <br>

### 올바른 형변환 방법
```
fun main() {
    var i = 10
    var l = 20L

    l = i.toLong()
}
```

### 자주 쓰는 형변환 함수
- toInt()
- toLong()
- toDouble()
- toString()

> 타입 안정성을 굉장히 중요하게 보는 언어라서 일부러 이렇게 설계됨

## String 다루기
```
var name = "seulgi"

print(name.uppercase())
print(name.lowercase())
print(name[0])
print("제 이름은 " + name + "입니다.")
print("제 이름은 ${name}입니다.")
```

### 포인트 정리
- 문자열 관련 메서드는 자바에서 하던 거 거의 다 가능
- 문자열은 배열처럼 인덱스로 접근 가능 `(name[0])`
- 문자열 템플릿(String Template) 지원
- `${}` 안에 변수나 표현식 바로 사용 가능

`print("제 이름은 ${name}입니다.")`


> 자바에서 +로 이어 붙이던 거보다 훨씬 가독성 좋음

## max 함수
```
var i = 10
var j = 20

print(kotlin.math.max(i, j))
```

`Math.max()` 대신 `kotlin.math.max()` 사용  <br>

코틀린 표준 라이브러리에 포함돼 있음 <br>

## 랜덤 값 생성
```
import kotlin.random.Random

fun main() {
    val randomNumber = Random.nextInt(0, 100)
    print(randomNumber)
}

```

#### 범위 주의 ⚠️
- 0 포함
- 100 미포함

> 즉, 0 ~ 99 까지 나옴

## 키보드 입력
```
var reader = Scanner(System.`in`)
reader.nextInt()
reader.next()
```


자바에서 쓰던 `Scanner` 그대로 사용 가능 <br>

`System.in` → 코틀린에서는 ``` System.`in` ``` 처럼 백틱 사용

> 자바랑 거의 동일해서 진입장벽 낮음

## 조건문
```
val i = 5

if (i > 10) {
    print("10 보다 크다")
} else if (i > 5) {
    print("5 보다 크다")
} else {
    print("")
}
```

### when 표현식
```
when {
    i > 10 -> {
        print("10 보다 크다")
    }
    i > 5 -> {
        print("5 보다 크다")
    }
    else -> {
        print("")
    }
}
```

**switch** 대신 **when**
조건식 기반으로도 사용 가능해서 훨씬 유연함 <br>

**if는 “문”이 아니라 “식”**
```
val result = if (i > 10) {
    "10 보다 크다"
} else if (i > 5) {
    "5 보다 크다"
} else {
    "!!!!!"
}
```
> 코틀린에서는 if 자체가 값이라서 변수에 바로 저장 가능

#### 자바 vs 코틀린 비교
```
// Java
boolean result = i > 10 ? true : false;

// Kotlin
val result = if (i > 10) true else false
```
- 삼항 연산자 ❌
- if 식으로 충분히 대체 가능 ⭕

## 반복문
```
val items = listOf(1, 2, 3, 4, 5)
```

#### 기본 for-each
```
for (item in items) {
    print(item)
}
```

#### forEach 사용
```
items.forEach { item ->
    print(item)
}
```
> (람다식이라 더 코틀린스러움)

#### 범위 기반 반복문
```
for (i in 0..3) {
    print(i)
}
```
- 0..3 → 3 포함

#### 자바랑 가장 헷갈리는 포인트
```
for (i in 0 until items.size) {
    print(items[i])
}
```
- `until` 사용하면 마지막 값 미포함
- 자바 `i < length`랑 가장 유사

#### 기타
- break, continue → 자바랑 동일
- while 문도 동일하게 제공됨


## List
`val items = listOf(1, 2, 3, 4, 5)`  변경 불가능한 리스트 <br>
`listOf` → 읽기 전용 리스트 <br>
- 요소 추가 / 삭제 ❌

```
val items2 = mutableListOf(1, 2, 3, 4, 5)
items2.add(6)
items2.remove(3)
```

`mutableListOf` → 변경 가능한 리스트 <br>

`add`, `remove` 등 사용 가능 <br>

#### 타입 생략 가능
`val items = listOf(1, 2, 3)`

코틀린은 타입 추론을 지원하기 때문에 <br>
`List<Int>` 같은 타입을 굳이 안 써도 된다 <br>

> 이게 코틀린 코드가 깔끔해 보이는 이유 중 하나

## Array
`val items = arrayOf(1, 2, 3)`

#### 값 변경
```
items.set(0, 10)  // 자바 스타일
items[0] = 10     // 코틀린 스타일
```
둘 다 가능 <br>
하지만 실무에서는 배열보다 `List` 사용을 권장 <br>
- 크기 고정
- 컬렉션 함수 활용이 불편함
>  특별한 이유 없으면 List 쓰는 게 정석

## Null Safety

코틀린의 핵심 개념 중 하나  <br>
널을 넣을 수 있는 타입과 없는 타입을 아예 구분한다. <br>

```
var name: String? = null
name = "seulgi"
name = null
```
- `String?` → null 가능
- `String` → null 불가능

```
var name2: String = ""
```

### 강제 언래핑 (!!)
`name2 = name!!`
- !! → “절대 null 아니니까 믿고 써도 된다.”
- null이면 바로 런타임 에러

→ 에러 나면 100% 개발자 책임

> 실무에서는 가급적 ❌

#### if로 널 체크
```
if (name != null) {
    name2 = name
}
```
- 가장 직관적인 방식
- 스마트 캐스트 덕분에 name을 String으로 인식함

#### let을 활용한 널 체크
```
name?.let {
    name2 = it
}
```
- name이 null이 아닐 때만 실행
- 코틀린에서 가장 자주 쓰는 패턴 중 하나

> ?. + let 조합은 거의 필수 문법

## 함수
```
fun main() {
    print(sum(10, 20))
}
```

#### 기본 함수 선언
```
fun sum(a: Int, b: Int): Int {
    return a + b
}
```

#### 한 줄 함수
```
fun sum(a: Int, b: Int): Int = a + b
```
- 단일 표현식이면 `{} + return` 생략 가능
- 타입도 생략 가능하지만 가독성 때문에 종종 명시함

## 탑레벨 함수
- 코틀린 함수는 클래스 밖에서 선언 가능
- 같은 패키지면 어느 파일에서든 사용 가능

> 자바보다 구조가 훨씬 자유로움

#### 디폴트 파라미터
자바에서는 오버로딩으로 처리하던 걸 코틀린에서는 기본값으로 해결 가능

```
fun sum(a: Int, b: Int, c: Int = 0): Int = a + b + c

sum(1, 2)
sum(1, 2, 3)
```
- 함수 오버로드 필요 ❌
- 코드 훨씬 간결해짐 ⭕

```
이름 있는 파라미터 (Named Argument)
fun main() {
    print(sum(a = 10, b = 20))
}
```

#### 장점
- 파라미터 순서 헷갈릴 일 ❌
- 가독성 👍
- 유지보수할 때 실수 줄어듦

> 코틀린스럽게 쓸수록 명시적이고 안전한 코드가 된다

```
Class
fun main() {
    val john = Person("John", 20)
    print(john.name)
    print(john.age)
}

class Person(val name: String, var age: Int)
```

#### 포인트
- 생성자에서 바로 프로퍼티 선언 가능
- `val` → 읽기 전용 (수정 불가)
- `var` → 수정 가능
>  val, var 자체가 getter / setter 역할을 해준다
> (코틀린은 기본 getter / setter 자동 생성)

## 접근 제어자 & data class
```
class Person(
    private val name: String,
    var age: Int
)
```
- `private` 붙이면 외부 접근 불가
- 아무것도 안 쓰면 기본은 `public`

> 코틀린은 접근 제어가 훨씬 명확함

## 일반 class vs data class
### 일반 클래스
```
fun main() {
    val john = Person("John", 20)
    val john2 = Person("John", 20)

    println(john)
    println(john2)
    println(john == john2)
}
```
#### 출력 결과
```
com.mysite.Person@31befd9f
com.mysite.Person@1c20c684
false
```
- 주소값(해시값) 기준 비교
- 내용이 같아도 `== `결과는 `false`

### data class 사용
```
data class Person(
    val name: String,
    var age: Int
)
```
#### 출력 결과
```
Person(name=John, age=20)
Person(name=John, age=20)
true
```
**data class**가 자동으로 만들어주는 것들
- toString()
- equals()
- hashCode()
- copy()
- componentN()

> 값 비교용 객체는 거의 무조건 data class

## init 블록 & 프로퍼티
```
class Person(
    private val name: String,
    var age: Int
) {
    var hobby = "축구"

    init {
        print("init")
    }

    fun some() {
        hobby = "농구"
    }
}
```
- `init` → 생성자 호출 시 바로 실행
초기화 로직 넣을 때 사용

## getter / setter 제어
```
var hobby = "축구"
    private set
```
**getter**는 `public` <br>

**setter**만 `private` → 외부 수정 불가

### 커스텀 getter
```
var hobby = "축구"
    private set
    get() = "취미: $field"
```
- **field** → backing field (실제 값)
- 출력 포맷 제어 가능

## 상속 (extends)
코틀린은 기본적으로 모든 클래스는**final**
-> 상속하려면 **open** 필요

```
open class Person
```

### 추상 클래스
```
abstract class Animal {
    open fun move() {
        print("이동")
    }
}

class Dog : Animal() {
    override fun move() {
        println("껑충껑충")
    }
}

class Cat : Animal() {
    override fun move() {
        println("슬금슬금")
    }
}
```
> 자바보다 의도가 명확한 상속 구조

### Interface
```
interface Drawable {
    fun draw()
}

class Dog : Animal(), Drawable {
    override fun move() {
        println("껑충껑충")
    }

    override fun draw() {}
}
```
- **상속**은 `:` 사용
- **인터페이스**는 **콤마**로 여러 개 구현 가능

## 타입 체크 (is)
```
if (dog is Dog) {
    println("멍멍이")
}

if (dog is Animal) {
    println("동물")
}

if (dog is Cat) {
    println("고양이")
}
```
- **instanceof** 대신 **is**
타입 체크 후 자동 캐스팅됨 (스마트 캐스트)

## 강제 타입 변환 (as)
`cat as Dog`
- 잘못된 타입이면 런타임 에러

### 제너릭
```
fun main() {
    val box = Box(10)
    val box2 = Box("dfdfdf")

    print(box.value)
}

class Box<T>(var value: T)
```
- 타입에 독립적인 클래스 작성 가능
자바 제너릭이랑 거의 동일하지만 문법은 더 깔끔

## 고차 함수 (콜백 함수)
```
fun main() {
    myFunc(10) {
        println("함수 호출")
    }
}

fun myFunc(a: Int, callBack: () -> Unit = {}) {
    println("함수 시작!!!")
    callBack()
    println("함수 끝")
}
```

- 함수를 파라미터로 전달 가능
- 기본값 지정 가능
코틀린이 함수형 스타일에 강한 이유

## 코루틴 (Coroutine)
```
suspend fun myFunc() { }
```
- **suspend** 함수는 일반 **main**에서 바로 호출 ❌
- **코루틴 스코프 필요**

```
lifecycleScope.launch {
    myFunc()
}
```

**주의**
- **Android**에서는 **lifecycleScope** 사용
코루틴 사용하려면 의존성 추가 필수
> 비동기 처리에서 콜백 지옥 탈출 가능
