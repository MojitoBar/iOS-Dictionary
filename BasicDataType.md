# Basic DataType
여러가지 기본 데이터 타입들에 대하여...
### Constant, Variable
- 변수는 크게 상수(Constant)와 변수(Variable)로 나눠진다.
```swift
var variable: Int = 10
let constant: Int = 10

variable = 11
constant = 11     // Error
```
- 변수와 상수는 초기화 되는 값의 타입이 명확하다면 타입은 생략 가능하다.<br>
ex: `var variable = 10`
- 변수와 상수는 나중에 값을 할당할 수 있다. 이때 꼭 타입을 명시해주어야 한다.<br> 
(상수의 경우 선언만 한 후 값을 나중에 한 번 할당 한다는 뜻.)
- 변수는 차후에 값을 변경할 수 있고, 상수는 차후에 값을 변경할 수 없다.

### Why let?
- Swift에서 변수는 Variable의 축어 var을 사용하지만 상수는 어째서인지 Constant의 축어인 const를 사용하지 않는다. <br>
이와 관련해 몇 가지 설들이 있지만 명확한 이유를 아직 찾지 못했다. <br>
[링크](https://stackoverflow.com/questions/26063763/why-is-a-constant-declared-with-the-keyword-let-in-swift)는 StackOverflow에 올라온 관련 질문이다.

### Basic DataType
- 기본적인 데이터 타입으로는 `Bool`, `Int`, `UInt`, `Float`, `Double`, `Character`, `String`이 있다.
```swift
// true 또는 false 값을 가지는 데이터 타입
var boolean: Bool = true
// 정수 값을 가지는 데이터 타입
var integer: Int = -123
// 양의 정수 값만 가지는 데이터 타입
var unsignedInt: UInt = 123
// 32bit 부동소수형 타입
var float: Float = 123.4
// 64bit 부동소수형 타입
var double: Double = 123.45
// 문자 값을 가지는 데이터 타입
var character: Character = "A"
// 문자열 값을 가지는 데이터 타입
var string: String = "ABCD"
```
- swift에서는 다른 데이터 타입과의 암시적인 자료교환은 절대 불가능하다.
- 타입을 지정해주지 않고 양의 정수로 초기화 시 자동으로 `Int`타입으로 초기화 된다.
- 타입을 지정해주지 않고 실수로 초기화 시 자동으로 `Double`타입으로 초기화 된다.
- `Character`와 `String`타입 모두 큰 따옴표를 사용하며 작은 따옴표는 사용할 수 없다.
- 큰 따옴표 3개를 쓰면 여러 문자열을 사용할 수 있다.<br>
```swift
// Example
"""
Hi, My name is Mojito.
My age is 20.
Bye ~
"""
```
