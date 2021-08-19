# Type Casting
타입 캐스팅에 대하여
### Type Casting이란?
- `is` 로 인스턴스의 타입을 확인하거나, `as` 로 슈퍼클래스 또는 서브클래스 타입처럼 다루는 것을 말한다.

### Defining a Class Hierarchy for Type Casting
- 타입 캐스팅을 위한 예제로 먼저 미디어라는 클래스를 정의한다.
```swift
class MediaItem {
    var name: String
    init(name: String) {
      self.name = name
    }
}
```
- `MediaItem` 클래스는 String 형식의 name 프로퍼티와 생성자 하나를 갖는 클래스다.

```swift
class Movie: MediaItem {
    var director: String
    init(name: String, director: String) {
        self.director = director
        super.init(name: name)
    }
}

class Song: MediaItem {
    var artist: String
    init(name: String, artist: String) {
        self.artist = artist
        super.init(name: name)
    }
}
```
- 그리고 `MediaItem` 클래스를 상속받는 `Movie` 클래스와 `Song` 클래스를 만든다.

```swift
let library = [
    Movie(name: "Casablanca", director: "Michael Curtiz"),
    Song(name: "Blue Suede Shoes", artist: "Elvis Presley"),
    Movie(name: "Citizen Kane", director: "Orson Welles"),
    Song(name: "The One And Only", artist: "Chesney Hawkes"),
    Song(name: "Never Gonna Give You Up", artist: "Rick Astley")
]
```
- 그리고 `library` 배열을 만들어 위에서 선언한 클래스들을 생성하면 `library` 배열은 `MediaItem` 타입의 배열이 된다.
- `Movie` 와 `Song` 클래스가 `MediaItem` 을 상속받는 클래스이기 때문에 이러난 형변환이다.
- 만약 `library` 배열에 한 가지 클래스만 들어있다면 해당 클래스 타입의 배열이 된다.
- 만약 `library` 배열에 같은 부모 클래스를 상속 받지 않는 클래스들이 들어있다면 `Any` 타입의 배열로 초기화 하라는 오류 메시지가 뜬다.

### Checking Type
- 타입을 확인할 때는 `is` 연산자를 사용한다.

```swift
for item in library {
    if item is Movie {
        movieCount += 1
    } else if item is Song {
        songCount += 1
    }
}

print("Media library contains \(movieCount) movies and \(songCount) songs")
```
- 위에서 생성했던 libaray를 돌며 `is` 연산자를 사용하여 `Count`를 측정하는 예제이다.
- `is` 로 연산된 결과는 [`Bool`](https://github.com/MojitoBar/iOS-Dictionary/blob/main/BasicDataType.md#basic-datatype-1) 타입으로 리턴된다.

### Downcasting
- 
