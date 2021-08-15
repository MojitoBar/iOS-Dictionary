# Console Log
여러가지 로그 확인 법에 대하여...
### print
- 가장 기본적인 로그 확인 방법이다.
- 출력하려는 인스턴스의 description 프로퍼티에 해당하는 내용을 출력한다.
```swift
// Example
var str: String = "Hello MojitoBar!"

print("Print Log!")
print(str)
print(1.0, 2.0, 3.0, 4.0, 5.0)
```
```console
// Output
Print Log!
Hello MojitoBar!
1.0 2.0 3.0 4.0 5.0
```
- Output을 보면 자동으로 개행이 되는 것을 볼 수 있는데, 이는 [함수 원형](https://developer.apple.com/documentation/swift/1541053-print)을 통해 확인해 볼 수 있다.
```swift
// Function Base
func print(_ items: Any..., separator: String = " ", terminator: String = "\n")
```
- 함수 원형을 보면 3번째 인자로 오는 terminator 매개변수에 개행문자가 이미 할당되어 있는 모습을 볼 수 있다.
- terminator 매개변수에 `""` 값을 직접 넣게 되면 개행을 취소할 수 있다.
- 첫 번째 매개변수는 Any타입의 [가변 매개변수]()로 이루어져 있기 때문에 `,`를 이용해 예제의 마지막 줄과 같이 여러개의 변수를 넣을 수 도 있다.
- 여담으로 print 함수는 Swift 1.2 까지는 println 이라는 이름으로 불리었다가 Swift 2.0 부터는 print 로 이름이 바뀌었다.

### debugPrint
- 출력하려는 인스턴스의 정보를 print 함수 보다 좀 더 자세하게 알 수 있다.
```swift
// Example
var s = "Hello"
print(s)
debugPrint(s)

print(1..<5)
debugPrint(1..<5)
```
```console
// Output
Hello
"Hello"

1..<5
Range(1..<5)
```
- debugPrint의 [함수 원형](https://developer.apple.com/documentation/swift/1539920-debugprint)은 print와 똑같다.
- 둘의 Output에 차이가 나는 것은 따르는 프로토콜의 차이 때문이다.<br> (print는 CustomStringConvertible을 따르고 debugPrint는 CustomDebugStringConvertible를 따른다.)

### dump
- 출력하려는 인스턴스의 자세한 내부 콘텐츠까지 출력한다.
```swift
// Example
class Person {
  var height: Float = 0.0
  var weight: Float = 0.0
}

let jito: Person = Person()
jito.height = 180.5
jito.weight = 75.5

print(jito)
dump(jito)
```
```console
// Output
__lldb_expr_25.Person         // print
▿ __lldb_expr_25.Person #0    // dump
  - height: 180.5
  - weight: 75.5
```
- print에선 알 수 없었던 내부 변수들의 값 까지 알 수 있다.
- dump의 [함수 원형](https://developer.apple.com/documentation/swift/1539127-dump)은 아래와 같다.
```swift
@discardableResult func dump<T>(_ value: T, name: String? = nil, indent: Int = 0, maxDepth: Int = .max, maxItems: Int = .max) -> T
```
- maxDepth와 maxItems를 통해 각각 구성 요소가 있는 값의 내용을 쓸 때 내려가는 최대 깊이와 기록할 최대 요소 수를 조절할 수 있다.<br> (둘 다 Int.max가 기본.)


