# Swift
## 1.언어 특징
### 1) 정적언어 => 컴파일 단계에서 변수 및 상수의 형 정보를 결정 => 런타임 오작동 안정성 보장
### 2) nil
#### Objective-C 에서는 포인터를 지원하기 때문에 다음의 4가지를 사용.
#### (1) nil
##### Object의 부재
```
NSString * strObject = nil;
```
#### (2) Nil
##### Class의 부재
```
Class myClass = Nil
```
#### (3) NULL
##### C-Pointer의 부재
```
int *intPtr = NULL;
```
#### (4) NSNull
##### NSObject를 상속받는 객체로 collection item을 null로 설정할 필요가 있을때 사용
```
[myArray addObject:[NSNull null]];
if ([myArray objectAtIndex:0] == [NSNull null])
```




### 3) 형추론
```
let a = 1234 // int 
let b = "test" //String
let c // 컴파일러는 점쟁이는 아님. 값을 할당 안해줄 때에는 어노테이션작성!
let c : String
```
### 4) Objective-C 연동
```
@objc fun~~~
```

## 2.기초 문법
Swift 자료형 Tuple
제어문 for while switch

Function vs Method
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
