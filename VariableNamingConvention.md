# Variable Naming Convention
여러가지 명명 규칙에 대하여...
### Basic
- 기본적으로 Swift는 [Camel Case](https://ko.wikipedia.org/wiki/%EB%82%99%ED%83%80_%EB%8C%80%EB%AC%B8%EC%9E%90)를 따른다. (대소문자를 구별한다는 뜻.)
- <b>Lower Camel Case</b> 에는 function, method, variable, constant 등이 있다.
- <b>Upper Camel Case</b> 에는 type(class, struct, enum, extension) 등이 있다.

### Initializers
- 초기화 구문에서 명확하게 하기 위해 저장된 속성에 직접 해당하는 이니셜라이저 인수는 속성과 이름이 같게 하는 것을 선호한다.
```swift
public struct Person {
  public let name: String
  public let phoneNumber: String

  public init(name: String, phoneNumber: String) {    
    self.name = name                              // GOOD.
    self.phoneNumber = phoneNumber                // GOOD.
  }
}
```
```swift
// AVOID Example.
public struct Person {
  public let name: String
  public let phoneNumber: String

  public init(name otherName: String, phoneNumber otherPhoneNumber: String) {
    name = otherName                              // AVOID.
    phoneNumber = otherPhoneNumber                // AVOID.
  }
}
```

### Static and Class Properties
- 선언 형식의 인스턴스를 반환하는 정적 및 클래스 속성에는 형식 이름이 접미사로 붙지 않는 것을 선호한다.
```swift
public class UIColor {
  public class var red: UIColor {                // GOOD.
    // ...
  }
}

public class URLSession {
  public class var shared: URLSession {          // GOOD.
    // ...
  }
}
```
```swift
public class UIColor {
  public class var redColor: UIColor {           // AVOID.
    // ...
  }
}

public class URLSession {
  public class var sharedSession: URLSession {   // AVOID.
    // ...
  }
}
```
