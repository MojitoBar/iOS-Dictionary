# Struct
구조체에 대하여...
### Definition
```swift
struct 이름 {
    // 코드
}
```

### 프로퍼티 및 메서드
```swift
struct Sample {
    var mutableProperty: Int = 100        // 가변 프로퍼티
    let immutableProperty: Int = 100      // 불변 프로퍼티
    
    static var typeProperty: Int = 100    // 타입 프로퍼티
    
    // 인스턴스 메서드
    func instanceMethod() {
        print("instance method")
    }
    // 타입 메서드
    static func typeMethod() {
        print("type method")
    }
```
- 타입 프로퍼티와 타입 메서드의 경우 `Sample`이라는 타입 자체에서만 사용가능하고 인스턴스에서는 사용이 불가능하다.

# Class
클래스에 대하여...
### Definition
```swift
class 이름: 상속 {
    // 코드
}
```
