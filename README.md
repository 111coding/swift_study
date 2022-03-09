# Swift

## 1.언어 특징


### 1) 정적언어 
#### => 컴파일 단계에서 변수 및 상수의 형 정보를 결정 
#### => 런타임 오작동 안정성 보장


### 2) nil
#### Objective-C 에서는 포인터를 지원하기 때문에 다음의 4가지를 사용.
#### Swift에서는 <span style="color:red">nil</span>만 사용!
|nil|Nil|NULL|NSNull|
|---|---|---|---|
|Object의 부재|Class의 부재|C-Pointer의 부재|NSObject를 상속받는 객체로 collection item을 null로 설정할 필요가 있을때 사용|
|```NSString * temp = nil;```|```Class temp = Nil```|```int *temp = NULL;```|```[temp addObject:[NSNull null]];```<br/>``` if ([temp objectAtIndex:0] == [NSNull null])```|



### 3) 형추론
#### 컴파일 시점에서 변수의 타입을 지정
```
let a = 1234 // int 
let b = "test" //String
```
#### 하지만 아래와같이 사용하면 컴파일 시 어떤타입으로 지정할지 알 수 없음. 컴파일러가 점쟁이는 아니므로 값을 할당하지 않을거면
```
let c
```
#### 아래와 같이 타입을 지정(어노테이션)!
```
let c : String
```


### 4) Objective-C 연동
#### Swift에서 Objective Function을 사용할 수도 있고, Objective-C에서 Swift Function을 사용할 수 있다.
#### 단 Swift4 이상에서는 함수앞에 @objc Inference(추론)을 사용하여 사용하여야 한다.
```
@objc func mySwiftFn() {
    print("funking swift")
}
```

### 5) 함수가 1급 객체!


## 2.기초 문법
#### 1) 제어문
#### while Loop
```
var i = 0
while i < 10 {
    print(i)
    if i == 5 {
        break
    }
    i += 1
}
```
#### for Loop
```
// 1부터 10까지
for i in 1...10{ 
    print(i) 
}
// 0부터 9까지
for i in 0..<10{ 
    print(i) 
}
// where 조건을 만족하면 실행
for i in 1...10 where i % 2 == 0 { 
    print(i) 
}
// 10부터 1까지 반대로
for i in stride(from: 10 , to: 1, by: -1) {
   print(i)
}
```
#### switch Loop
```
let num = 10

switch num {
case 0:
    print("--> 0 입니다")
case 5...8:
    print("--> 5 ~ 8사이 입니다")
case 10:
    print("--> 10 입니다")
default :
    print("--> 나머지 입니다")
}
```
Swift 자료형 Tuple


Closure (익명함수)
함수리턴 -> 타입
파라미터 기본 상수, 변수르 쓰려면 _ value:inout Int 이런식
전달인자 
```
// 1. 일반적 함수
func normalFunc(name: String) {
}
// 함수호출
normalFunc(name: "나리")
// 함수이름: normalFunc(name:)

// 2. 전달인자 레이블을 사용한 함수
func usingArgumentLabelFunc(to name: String) {
}
// 함수호출
usingArgumentLabelFunc(to: "나리")
// 함수이름: usingArgumentLabelFunc(to:)


// 3. 전달인자 레이블을 와일드카드 식별자로 사용하는 함수 - 함수호출 시 자바에서처럼 호출
func usingWildCardLabelFunc(_ name: String) {
}
// 함수호출
usingWildCardLabelFunc("나리")
// 함수이름: usingWildCardLabelFunc(_:)
```

옵셔널 

컬렉션

구조체 vs 클래스

프로퍼티 게터 세터 윌셋 딛셋



## 3.ARC (Automatic Reference Counting)
## *ARC VS JAVA GC VS DART GC VS JS GC
