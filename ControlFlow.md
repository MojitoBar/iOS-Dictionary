# ControlFlow
여러가지 제어문들에 대하여...

### 조건문
- Swift에서 조건문은 `if-else`문과 `switch`문이 있다.

**if-else**
```swift
let someInteger = 100

if someInteger < 100 {
    print("100 미만")
} else if someInteger > 100 {
    print("100 초과")
}
else {
    print("100")
}
```
- Swift 조건문에는 항상 `Bool` 타입이 들어와야 한다.
- 다른 언어와 차이점으로는 조건의 소괄호가 선택사항이라는 것이다. <br>
하지만 자동완성을 했을 때 소괄호 없이 완성되는 것을 보면 없이 쓰는 것을 권장하는 것 같다.

**switch**
```swift
switch someInteger {
case 0:
    print("zero")
case 1..<100:
    print("1 ~ 99")
case 100:
    print("100")
case 101...Int.max:
    print("over 100")
default:
    print("unknown")
}
```
- [범위 연산자]()와 함께 사용하면 유용하다.
- [Hashable Protocol]()을 따르는 타입은 모두 사용 가능하다.
- 모든 `case`가 명시되지 않는 한 `default`구문을 반드시 작성해야한다.
- 명시적으로 `break`를 걸지 않아도 자동으로 걸리게 된다.
- 여러가지 `case`를 동시에 처리하려면 `,` 연산자를 사용하는 방법이 있다.

### 반복문
- Swift에서 반복문은 `for-in`, `while`, `repeat-while`이 있다. 

**for-in**
```swift
var someArray = [1, 2, 3]

for item in someArray {
    print(item)
}

// Output: 1 
           2 
           3
```
- 기본형은 `for item in items {}`와 같다.
```swift
for (index, item) in someArray.enumerated() {
    print("\(index)번째 item은 \(item)")
}

// Output: 0번째 item은 1
           1번째 item은 2 
           2번째 item은 3
```
- `enumerated()`함수를 사용하면, `(index, value)` 튜플형식으로 구현된 리스트형이 리턴되므로 `index`와 `value`를 동시에 사용가능하다.

**while**
```swift
while integers.count > 1 {
    integers.removeLast()
}
```
- 기본형은 `while condition {}`와 같다.

**repeat-while**
```swift
repeat {
    integers.removeLast()
} while integers.count > 0
```
- 기본형은 `repeat {} while condition`와 같다.
- `repeat-while`문은 다른 언어의 `do-while`문과 같다.<br>
swift에는 `do-while`문이 없다.

### ETC...
**guard**
- 어떤 `Bool`타입 조건에 대해 방어하는 역할을 한다.
- `if-else`로 완벽하게 대체 가능하지만 가독성이 좋다는 이유로 사용되는 문법이라 한다.

```swift
func guardInFunc (string: String?) {
    guard string != nil else { return }

    print(string!)
}

guardInFunc(string: "Hello!")
```
- 위 예제는 `string` 매개변수가 `nil` 값 일때를 방어한 코드이다.
- `nil`이 아닐 경우 `guard`문을 패스하고, `nil`일 경우 `{ code }`를 실행한다.

**if-let**
- `if-let`은 [`Optional`]() 값을 `Unwrapping` 하는 과정이다.

```swift
let string: String? = "Jito"

var names :[String] = []
if string != nil {            // nil 값 체크.
    names.append(string!)     // !로 unwrap 해야함.
}
else {
    print("String is nil")
}
```
```swift
let string: String? = "Jito"

var names :[String] = []
if let name = string{
    names.append(name)
} else {
    print("string is nil")
}
```
- 두 코드를 비교해 보면 `if-let`의 활용도를 바로 알 수 있다.
- `Optional` 변수를 다루게 되면 첫 번째 예제에서와 같이 `nil`값 체크와 `!`로 unwrap해주는 과정이 필요하다.
- `string`이 `nil`이면 `else` 코드 블럭을 실행한다.
- `if-let`을 사용하면 `string`이 `nil`이 아닐 때만 `name`이라는 `non-optional` 변수로 값이 복사되고 `if` 코드블럭을 실행한다.
- `if-let`을 사용하면 `Optional` 변수의 사용을 줄일 수 있고, 코드 가독성이 높아진다.
