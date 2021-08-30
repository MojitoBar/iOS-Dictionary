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

### 프로퍼티 및 메서드
```swift
class Sample {
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
- `class`는 전체적으로 `struct`와 매우 유사하다.
- 차이점으로는 구조체는 값 타입, 클래스는 참조 타입이다.
- 구조체는 상속할 수 없고, 타입 캐스팅은 클래스의 인스턴스에만 허용된다.

### 구조체를 사용하는 것이 유리한 경우
1. 연관된 간단한 값의 집합을 **캡슐화하는 것만이 목적**일 때
2. 캡슐화한 값을 참조하는 것보다 **복사하는 것이 합당할 때**
3. 구조체에 저장된 **프로퍼티가 값 타입**이며 참조하는 것보다 복사하는 것이 합당할 때
4. 다른 타입으로부터 **상속받거나 자신을 상속할 필요가 없을 때**
- 애플은 다음 조건 중 하나 이상에 해당한다면 구조체를 사용하는 것을 권장한다.
