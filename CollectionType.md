# Collection Type
컬렉션 타입에 대하여...
### Array
- 순서가 있는 같은 타입의 값들의 컬렉션.

빈 배열의 생성
```swift
var someInts = [Int]()
```
리터럴을 이용한 배열의 생성
```swift
var shoppingList: [String] = ["Eggs", "Milk"]
```
```swift
var shoppingList = ["Eggs", "Milk"]
```
배열의 원소 개수 확인
```swift
print("\(shoppingList.count) items.")           // Output: 2 items.
```
배열이 비었는지 확인
```swift
if shoppingList.isEmpty{
    print("empty.")
} else {
    print("not empty.")                       // Output: not empty.
}
```
배열에 원소 추가
```swift
shoppingList.append("Four")
```
```swift
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
```
배열의 특정 위치의 원소 접근
```swift
var firstItem = shoppingList[0]               // firstItem: "Eggs"
```
```swift
shoppingList[4...6] = ["Bananas", "Apples"]    // 4, 5, 6번째 인덱스 아이템을 Banana, Apples로 변환
                                               // 4, 5번 인덱스를 변환하고 6번 인덱스는 삭제
```
특정 위치에 원소 추가/삭제/접근
```swift
shoppingList.insert("Maple Syrup", at: 0)
```
```swift
let mapleSyrup = shoppingList.remove(at: 0)
```
```swift
firstItem = shoppingList[0]
```
```swift
let apples = shoppingList.removeLast()
```
배열의 순회
```swift
for item in shoppingList {
    print(item)
}
```
```swift
for (index, value) in shoppingList.enumerated() {
    print("Item \(index + 1): \(value)")
}
```

### Set
- 순서가 없고 중복된 값을 가지지 않는 컬렉션이다.
집합 선언과 초기화 방법들
```swift
let fruitsSet: Set<String> = ["Apple", "Orange", "Melon"]
let numbers: Set = [1, 2, 3, 3, 3]
let emptySet = Set<String>()
```

집합의 특징
```swift
var number: Set = [1, 2, 3]
number.insert(1)                        // 1을 추가했으나,
print(number)                           // 결과는 [1, 2, 3]로 동일하다.
```

두 집합 비교
```swift
var favoriteFruits = Set(["Apple", "Orange", "Melon"])
var tropicalFruits = Set(["Orange", "Melon", "Apple"])

if favoriteFruits == tropicalFruits {
    print("favoriteFruits == tropicalFruits")          // 각 배열의 요소들은 동일하게 가지고 있기 때문에 True.
} else {
    print("favoriteFruits != tropicalFruits")
}

if favoriteFruits.elementsEqual(tropicalFruits) {      // .elementsEqual 은 비교 대상끼리의 '==' 비교에다가 내부 요소의 순서까지 같아야 한다고 보면 된다.
    print("favoriteFruits == tropicalFruits")
} else {
    print("favoriteFruits != tropicalFruits")          // 요소의 순서가 같지 않으므로 이 부분 실행.
}
```
기본적인 집합 연산
```swift
let setA: Set<Int> = [1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7]

let union: Set<Int> = setA.union(setB)                  // 합집합 연산
let sortedUnion: [Int] = union.sorted()                 // union 집합을 정렬 후 배열로 변환
let intersection: Set<Int> = setA.intersection(setB)    // 교집합 연산
let subtracting: Set<Int> = setA.subtracting(setB)      // 차집합 연산
```

- 이외의 값 추가, 수정, 접근 등의 연산자는 배열과 대동소이 하다.

### Dictionary
- 순서가 없는 키와 값의 쌍으로 이루어진 컬렉션이다.
- 유일한 제약사항으로, `KeyType`은 [`Hashable`]() 타입이어야 합니다.

Dictionary 생성하는 방법
```swift
var dic: [Int : String] = [:]
```
```swift
var dic = [Int : String]()
```
```swift
var dic: Dictionary = [Int : String]()
```
```swift
var dic: Dictionary<Int, String> = Dictionary<Int, String>()
```

Dictionary 값 추가 및 수정
```swift
var dic : [Int : String] = [1:"Jito", 2:"swift", 3:"iOS"]

dic.updateValue("fun", forKey: 3)
print(dic)                              // [1:"Jito", 2:"swift", 3:"fun"]

dic[3] = "iOS"                          // 여기서 3은 순서가 아니라 key값을 의미한다.
print(dic)                              // [1:"Jito", 2:"swift", 3:"iOS"]
```
- 해당 `key`값이 없으면 값이 추가되고, `key`값이 있으면 수정이 된다.
- `updateValue`는 `Optinal`값을 반환한다.

Dictionary 값 접근
```swift
var dic : [Int : String] = [1:"zedd", 2:"swift", 3:"iOS"]

print(dic[1]!)//zedd
print(dic[2]!)//swift
print(dic[3]!)//iOS

var dic2 : [String : Int] = ["zedd":30, "swift":40,"iOS":50]

print(dic2["zedd"]!)                    // 30
print(dic2["swift"]!)                   // 40
print(dic2["iOS"]!)                     // 50

// key의 값으로 접근이 가능
var dic3 : [String : String] = ["zedd":"30", "swift":"40","iOS":"50"]

print(dic3["30"])                       // nil. "30"을 Value로 가지는 쌍은 있지만, "30"을 Key로 가지는 쌍이 없기때문. 
                                        // 무조건 Key값으로 접근해야 Value를 얻어올 수 있음.
```

Dictionary 탐색
```swift
dic = [1:"zedd", 2:"swift", 3:"iOS", 4:"fun", 5:"Hello"]

for (key,value) in dic{
    print(key)                          // 1 2 3 4 5
}
```

Dictionary 삭제
```swift
dic = [1:"jito", 2:"swift", 3:"iOS", 4:"fun", 5:"Hello"]
dic.removeValue(forKey: 5)

print(dic)                              // [1:"jito", 2:"swift", 3:"iOS", 4:"fun"]

dic.removeAll()                         // Dictionary의 모든 Key와 Value를 삭제
print(dic)                              // [:]

dic = ["zedd": 1]                       // error! [Int:String]타입의 Dictionary였으므로. 타입을 바꿔줄 수 없다.
```
