# Functions
함수(function)에 대하여...
### Defining and Calling Functions
- 함수를 선언할 때는 가장 앞에 `func` 키워드를 붙이고 `(person: String)` 파라미터와 형 그리고 `-> String` 형태로 반환형을 정의합니다.
```swift
// Example
func greet(person: String) -> String {
 let greeting = "Hello, " + person + "!"
 return greeting
}
```
### 함수 파라미터와 반환 값
파라미터가 없는 함수
```swift
func sayHelloWorld() -> String {
    return "hello, world"
}
print(sayHelloWorld())
// Output: "hello, world"
```

복수의 파라미터를 사용하는 함수
```swift
func greet(person: String, alreadyGreeted: Bool) -> String {
    if alreadyGreeted {
        return greetAgain(person: person)
    } else {
        return greet(person: person)
    }
}
print(greet(person: "Tim", alreadyGreeted: true))
// Output: "Hello again, Tim!"
```

반환 값이 없는 함수
```swift
func greet(person: String) {
    print("Hello, \(person)!")
}
greet(person: "Dave")
// Output: "Hello, Dave!"
```

복수의 값을 반환하는 함수
```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```

인자 라벨 지정
- 파라미터 앞에 인자 라벨을 지정해 실제 함수 내부에서 해당 인자를 식별하기 위한 이름과 함수 호출시 사용하는 이름을 다르게 해서 사용할 수 있습니다.
- 전달인자 라벨 사용 시 전달인자 라벨까지 함수 명으로 인식해 다른 함수로 인식한다.
```swift
func greet(person: String, from hometown: String) -> String {
    return "Hello \(person)!  Glad you could visit from \(hometown)."
}
print(greet(person: "Bill", from: "Cupertino"))
// Output: "Hello Bill!  Glad you could visit from Cupertino."
```

가변 매개변수
- 전달받을 매개변수의 개수를 알기 어려울 때 사용한다.
- 가변 매개변수의 타입은 배열이 된다.
```swift
func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}
print(sayHelloToFriends(me: "asdf", friends: "hana", "eric", "wing"))
// Output: Hello ["hana", "eric", "wing"]! I'm asdf!
```
