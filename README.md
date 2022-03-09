# Swift
https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#ID545
https://jusung.gitbook.io/the-swift-language-guide/language-guide/07-closures
## 1.언어 특징


<details>
<summary style="font-size:x-large;font-weight:bold"> 1) 정적언어</summary>
<div markdown="1" style="font-size:large;">

##### -> 컴파일 단계에서 변수 및 상수의 형 정보를 결정
##### -> 런타임 오작동 안정성 보장
</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 2) nil</summary>
<div markdown="1" style="font-size:large;">

##### Objective-C 에서는 포인터를 지원하기 때문에 다음의 4가지를 사용.
##### Swift에서는 <span style="color:red">nil</span>만 사용!
|nil|Nil|NULL|NSNull|
|---|---|---|---|
|Object의 부재|Class의 부재|C-Pointer의 부재|NSObject를 상속받는 객체로 collection item을 null로 설정할 필요가 있을때 사용|
|```NSString * temp = nil;```|```Class temp = Nil```|```int *temp = NULL;```|```[temp addObject:[NSNull null]];```<br/>``` if ([temp objectAtIndex:0] == [NSNull null])```|
</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 3) 타입추론</summary>
<div markdown="1" style="font-size:large;">

```
// 변수
var a = 1;
// 상수
let b = 2;
```

##### 컴파일 시점에서 변수의 타입을 지정
```
let a = 1234 // int 
let b = "test" //String
```
##### 하지만 아래와같이 사용하면 컴파일 시 어떤타입으로 지정할지 알 수 없음. 컴파일러가 점쟁이는 아니므로 값을 할당하지 않을거면
```
let c
```
##### 아래와 같이 타입을 지정(어노테이션)!
```
let c : String
```
</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 4) Objective-C 연동</summary>
<div markdown="1" style="font-size:large;">

##### Swift에서 Objective Function을 사용할 수도 있고, Objective-C에서 Swift Function을 사용할 수 있다.
##### 단 Swift4 이상에서는 함수앞에 @objc Inference(추론)을 사용하여 사용하여야 한다.
```
@objc func mySwiftFn() {
    print("funking swift")
}
```
</div>
</details>

<details>
<summary style="font-size:x-large;font-weight:bold"> 5) 함수가 1급 객체</summary>
<div markdown="1" style="font-size:large;">

##### 변수에 할당 가능
##### 파라미터로 전달 가능
##### 함수를 리턴가능

</div>
</details>



## 2.기초 문법

<details>
<summary style="font-size:x-large;font-weight:bold"> 1) 제어문</summary>
<div markdown="1" style="font-size:large;">

##### while Loop
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
##### for Loop
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
##### switch Loop
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
</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 2) Swift 자료형 Tuple</summary>
<div markdown="1" style="font-size:large;">

##### 다양한 데이터들의 묶음 (여러 Type의 값을 하나로 묶어 사용)
```
var tuple = (1, "Hello, world!", true)
tuple.0 //1
tuple.1 //"Hello, world!"
tuple.2 //true

// 아래 처럼 파라메터에 이름 지정 가능!
var person = (name: "션", age: 15, isJammin: true)
```
</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 3) 함수</summary>
<div markdown="1" style="font-size:large;">

##### 표현식
###### Void (Return Type 생략가능)
```
func nothingReturn(person: String) {
    print("Hello, \(person)!")
}
// 호출
nothingReturn(person: "lee")
```
###### Return Type 지정
```
func stringReturn(person: String) -> String {
    return "test"
}
// 호출
print(nothingReturn(person: "lee"))
```

###### 위 함수 예제를 보면 함수를 호출할 때에 파라미터명을 입력을 해주는 것을 볼 수 있다. 이걸 <span style="color:red">Argument Label</span> 이라 하는데 아규먼트 레이블을 바꾸고 싶다면 파라미터명 앞에 입력해서 사용
```
func argLabelTest(from person: String){
    print(person)
}
// 호출
argLabelTest(from: "lee")
```

###### 함수 호출 시 <span style="color:red">Argument Label을 생략</span>하고 사용하려면 Argument Label 자리에 <span style="color:red;font-weight:bold;font-size:x-large">_</span>(언더바, underscore)를 붙여주면 호출시 생략 가능하다.
```
func nonArgLabelTest(_ person: String){
    print(person)
}
// 호출
nonArgLabelTest("lee")
```


파라미터는 기본적으로 상수, 변수로 쓰려면 파라미터 type 앞에 <span style="color:violet;font-weight:bold;">inout</span> 예약어 사용하여 함수 선언하고 호출 시 파라미터 변수 앞에 <span style="color:violet;font-weight:bold;">&</span>(ampersand) 사용
```
func toggle(value : inout Bool){
    value = !value
}
// 호출
var isStupid = false
toggle(value: &isStupid)
```

</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 4) Closure</summary>
<div markdown="1" style="font-size:large;">

##### 정의
```
“A closure is the combination of a function and the lexical environment within which that function was declared.”
클로저는 함수와 그 함수가 선언됐을 때의 렉시컬 환경(Lexical environment)과의 조합이다.
-> 클로저는 반환된 내부함수가 자신이 선언됐을 때의 환경(Lexical environment)인 스코프를 기억하여 자신이 선언됐을 때의 환경(스코프) 밖에서 호출되어도 그 환경(스코프)에 접근할 수 있는 함수
- MDN -

클로저는 어떤 상수나 변수의 참조를 캡쳐(capture)해 저장
- Swift -

일급 객체 함수의 처리를 위해 사용

// EX
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}

let incrementByTen = makeIncrementer(forIncrement: 10)
incrementByTen()
// returns a value of 10
incrementByTen()
// returns a value of 20
incrementByTen()
// returns a value of 30

let incrementBySeven = makeIncrementer(forIncrement: 7)
incrementBySeven()
// returns a value of 7
```

##### 종류
|Named Closure(우리가 알고있는 함수)|Unnamed Closer|
|---|---|
|```func doSomething() {print("Somaker")}```|```let closure = { print("Somaker") }```|

##### Unnamed Coloser에 대해서 알아봅시다
##### 표현식
```
{
    (Parameters) -> Return Type in
     실행 구문
}
```
```
 (Parameters) -> Return Type  // 클로저헤드
 in 실행 구문 // 클로저 바디

```
```
// Return X, Parameters X
{ () -> () in
    print("Closure")
}
// Return O, Parameters O
{ (name: String) -> String in
    return "Hello, \(name)"
}
```
##### Unnamed Closer에는 아규먼트 라벨(Argument Label) 사용X
```
let unnamedTest = { (name: String) -> String in
    return "Hello, \(name)"
}
unnamedTest("lee")
```

</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 5) 옵셔널</summary>
<div markdown="1" style="font-size:large;">

##### 값이 nil 일 수도 있는 변수
```
let name: String? = nil 
```

##### 옵셔널 값 사용법
1. 강제 언래핑 (Forced unwrapping)
```
let name: String?
name = "lee"
print(name!)
```
2. Optional binding (if let)
```
if let unwrappedName = name{
    print(unwrappedName)
}else{
    print("nil!")
}

// else 생략 가능
if let unwrappedName = name{
    print(unwrappedName)
}
```
3. Optional binding (guard)
```
func guardTest(name : String?) {
    guard let unwrapperedName = name else {
        print("nil!")
        return
    }
    print(unwrapperedName)
}
```
4. Nil coalescing
```
var name : String?
name = "lee"
let unwrapperedName = name ?? "kim"
```



</div>
</details>

<details>
<summary style="font-size:x-large;font-weight:bold"> 6) 컬렉션</summary>
<div markdown="1" style="font-size:large;">



</div>
</details>


<details>
<summary style="font-size:x-large;font-weight:bold"> 7) 구조체 vs 클래스</summary>
<div markdown="1" style="font-size:large;">



</div>
</details>

<details>
<summary style="font-size:x-large;font-weight:bold"> 8) 프로퍼티 게터 세터 윌셋 딛셋</summary>
<div markdown="1" style="font-size:large;">



</div>
</details>
 






## 3.ARC (Automatic Reference Counting)
<details>
<summary style="font-size:x-large;font-weight:bold">ARC</summary>
<div markdown="1" style="font-size:large;">



</div>
</details>


