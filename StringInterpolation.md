# String Interpolation
문자열 보간법에 대하여...
### Basic
- 문자열 보간법은 문자열 내부에 변수와 상수를 결합하는 것이다.
- `\()`를 이용하는 방법과 `+`를 이용하는 방법이 있다.
```swift
// \()를 이용하는 방법
var name = "Mojito"
var age = 25
print("Your name is \(name)")
print("Your name is \(name), your age is \(age)")

// Output
// Your name is Mojito
// Your name is Mojito, your age is 25
```
```swift
// +를 이용하는 방법
var name = "Mojito"
print("Your name is " + name)
print("Your name is " + name + "your age is " + age)    // Error

// Output
// Your name is Mojito
// *Error*
```
- `+`를 이용한 문자열 보간법은 `String`끼리만 가능하다.
- 예제에선 `age`의 자료형이 `Int`이기 때문에 에러가 발생한다.
