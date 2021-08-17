# Basic DataType
여러가지 특별한 데이터 타입들에 대하여...
### Any
- `Any`는 함수타입을 포함하여 모든 타입의 인스턴스를 나타낼 수 있다.
```swift
// Example
var anyArr1: [Any] = [1, 2, "3", "4"]
var anyArr: Array<Any> = [1, 2, "3", "4"]
```
```swift
// Example
var a: Any = 1
var b: Int = 0
b = a               // error
```
- 첫 번째 예제와 같이 `Any`는 모든 타입에 대응하여 사용하는 것이 가능하다.
- 두 번째 예제에선 `b = a`에서 에러가 발생하게 된다. <br>
`Any` 타입은 런타임 시점에 타입이 결정되기 때문에 컴파일 시점에선 `a`가 어떤 타입인 지 알 수 없기 때문이다. <br>
이때 사용하는 것이 [Type Casting]()이다.

### AnyObject
- [AnyObject](https://developer.apple.com/documentation/swift/anyobject)는 모든 클래스가 암시적으로 준수하는 [Protocol]()이라 정의 되어있다.
```swift
// Example
class aType { }
class bType { }

var anyObjectArr : [AnyObject] = [aType(), bType()]
```
- `Any`와 마찬가지로 모든 클래스 타입이 저장될 수 있다.
- `Any`와 `AnyObject`는 잘 사용한다면 유용하지만 Swift가 타입에 민감할 뿐더러 런타임 시점에 타입이 결정나기 때문에, 만약 오류가 난다면 런타임 오류로 빠지게 된다.<br>
따라서 꼭 필요하지 않은 경우를 빼곤 남발하지 않는 것이 좋다.

### nil
- `nil`은 빈 값을 지칭한다.
- `Any`타입이 모든 값을 저장할 수 있지만 `nil`타입은 저장할 수 없다.
- `nil`값은 [Optional]()변수에서만 사용할 수 있다.

### Why nil?
- 빈 값을 나타내는 단어로는 `null`도 있지만 swift에서 `nil`을 사용하는 이유는 무엇일까?
- 간단하게 말해서 `null`은 임의의 C 포인터에 대한 리터럴 null 값이고 `nil`은 objective-c 개체의 리터럴 null 값이다.
- objective-c를 사용할 때는 `nill`과 `null` 모두 존재 했지만 swift로 넘어오며 `null`, `nill`구분이 필요 없어지며 `nil`만 사용하게 되었다.<br>
자세한 내용은 [링크](https://stackoverflow.com/questions/5908936/difference-between-nil-nil-and-null-in-objective-c/25761371) 참조.
