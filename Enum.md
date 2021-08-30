# Enum
열거형에 대하여...
- `enum`은 타입이므로 대문자 카멜케이스를 사용하여 이름을 정의하며 각 case는 그 자체가 고유의 값입니다.

### Definition
```swift
enum 이름 {
    case 이름1
    case 이름2
    case 이름3, 이름4, 이름5
```

### Example
```swift
enum Weekday{
    case dec, jan, feb
    case sep, oct, nov
    case jun, jul, aug
    case mar, apr, may
    
    func printMessage(){
        switch self {
            case .mar, .apr, .may:
                print("따스한 봄~")
            case .jun, .jul, .aug:
                print("여름 더워요~")
            case .sep, .oct, .nov:
                print("가을은 독서의 계절!")
            case .dec, .jan, .feb:
                print("추운 겨울입니다")
        }
    }
}

var day: Weekday = Weekday.mon
day = .tue
```
- 열거형을 사용한 간단한 예이다.
