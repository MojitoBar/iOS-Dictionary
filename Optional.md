# Optional
옵셔널과 옵셔널 체이닝에 대하여...
- Swift가 가지고 있는 가장 큰 특징 중 하나가 바로 `Optional`이다.

### Optional의 필요성
- `nil`의 가능성을 문서화 하지 않아도 코드만으로 충분히 표현가능하다.
- 전달받은 값이 옵셔널이 아니라면 `nil` 체크를 하지 않더라도 안심하고 사용할 수 있다.
- [옵셔널](https://developer.apple.com/documentation/swift/optional#declaration)은 ExpressibleByNilLiteral 프로토콜을 따르는 열거형과 제너릭의 합작품이다.

### 옵셔널의 원형 & 사용법
```swift
enum Optional<Wrapped> : ExpressibleByNilLiteral {
    case none
    case some(Wrapped)
}

// init
let optionalValue: Optional<Int> = nil
let optionalValue: Int? = nil
```

### 암시적 추출 옵셔널
```swift
var optionalValue: Int! = 100

switch optionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}
```
-  `optionalValue = optionalValue + 1` 와 같이 기존의 변수처럼 사용 가능하다.

```swift
var optionalValue: Int? = 100

switch optionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}
```
-  `optionalValue = optionalValue + 1` 와 같이 기존의 변수처럼 사용할 수 없다.<br>
옵셔널이라는 아예 새로운 타입이 되기 때문이다.

### 옵셔널 체이닝
- 옵셔널 요소 내부의 프로퍼티로 또 다시 옵셔널이 연속적으로 연결되는 경우 유용하게 사용할 수 있다.
```swift
class Person {
    var name: String
    var job: String?
    var home: Apartment?

    init(name: String){
        self.name = name
    }
}

class Apartment{
    var buildingNumber: String
    var roomNumber: String
    var `guard`: Person?
    var owner: Person?

    init(dong: String, ho: String) {
        buildingNumber = dong
        roomNumber = ho
    }
}

// 옵셔널 체이닝을 사용하지 않는다면...
// 경비원의 직업을 구하는 함수
func guardJob(owner: Person?) {
    if let owner = owner{
        if let home = owner.home{
            if let `guard` = home.`guard`{
                if let guardJob = `guard`.job{
                    print("우리집 경비원의 직업은 \(guardJob)입니다.")
                } else {
                    print("우리집 경비원은 직업이 없어요.")
                }
            }
        }
    }
}

// 옵셔널 체이닝을 사용한다면...
func guardJobWithOptinalChaining(owner: Person?){
    if let guardJob = owner?.home?.guard?.job{
        print("우리집 경비원의 직업은 \(guardJob)입니다.")
    } else {
        print("우리집 경비원은 직업이 없어요.")
    }
}
```
- 옵셔널 체이닝을 사용한 함수가 훨씬 가독성이 뛰어난 것을 볼 수 있다.
- 엮인 여러 변수 중 하나라도 `nil`값에 해당 한다면 `else`코드 블럭을 실행 한다.
