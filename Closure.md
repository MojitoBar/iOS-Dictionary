# Closure
코드의 블럭, 클로저에 대하여...
### Definition
```swift
{ (매개변수 목록) -> 반환타입 in
    실행 코드
}
```
- 클로저는 크게 `Named Closure`와 `Unnamed Closure` 두 가지로 나뉜다.
- 이름이 있는 클로저는 `Named Closure`이자 함수이다.
- 클로저는 축약과 생략의 미학이다.

### Closure as first-class objects
```swift
let closure = { () -> () in
    print("Closure")
}
```
- 클로저는 [1급 객체](https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B8%89_%EA%B0%9D%EC%B2%B4)로서 매개변수로 넘기기, 수정하기, 변수에 대입하기와 같은 연산을 지원한다.
- 위 예제는 `closure`라는 변수에 매개변수가 없고, 반환 값이 `Void`이며, `Closure`를 출력하는 클로저를 대입한 것이다.

### 클로저의 경량 문법
- 클로저가 함수의 마지막 전달인자라면 마지막 매개변수 이름을 생략한 후 함수 소괄호 외부에 클로저를 구현할 수 있다.

```swift
func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int{
    return method(a, b)
}

// Inline Closure
var result = calculate(a: 10, b: 10, method: { (left: Int, right: Int) -> Int in
    return left + right
}) 

// Trailing Closure
var result = calculate(a: 10, b: 10) { (left: Int, right: Int) -> Int in
    return left + right
}
```
- 일반적인 `Inline Closure`를 사용하면 `})` 로 괄호가 끝나는 것도 그렇고 가독성도 떨어진다.
- 반면에 `Trailing Closure` 형태로 축약하면 보다 더 알아보기 쉽다.

```swift
// 반환타입 생략
var result = calculate(a: 10, b: 10) { (left: Int, right: Int) in
    return left + right
}
```
- 클로저의 반환타입은 이미 정해져 있기 때문에 생략이 가능하다. (후행 클로저와 함께 사용할 수도 있다.)

```swift
// 단축 인자이름
var result = calculate(a: 10, b: 10) {
    return $0 + $1
}
```
- 클로저의 매개변수는 이미 정해져 있기 때문에 생략이 가능하다. (매개변수 순서대로 $0, $1,... 로 표현 가능.)

```swift
// 암시적 반환 표현
var result = calculate(a: 10, b: 10) { $0 + $1 }
```
- 클로저가 반환하는 값이 있다면 클로저의 마지막 줄의 결과값은 암시적으로 반환값으로 취급한다.
- 처음에 나온 클로저의 형태와 비교해보면 몰라보게 축약된 것을 알 수 있는데, 너무 축약해서 사용하면 오히려 어떤 의미인지 햇갈리는 경우가 생길수도 있음. **컴파일러가 알아 본다고 팀원이, 혹은 미래의 내가 알아본다고 확신할 수 없음.**


##### ❇︎autoclosure & @escaping 에 대한 내용 추가 필요.
