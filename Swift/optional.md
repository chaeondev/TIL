# 옵셔널, 옵셔널 바인딩, 옵셔널 체이닝

- [옵셔널, 옵셔널 바인딩, 옵셔널 체이닝](#옵셔널-옵셔널-바인딩-옵셔널-체이닝)
  - [옵셔널이란?](#옵셔널이란)
  - [옵셔널 해제 방법](#옵셔널-해제-방법)
      - [1. 강제 언래핑 (Forced Unwrapping) : `!` 사용](#1-강제-언래핑-forced-unwrapping---사용)
      - [2. 옵셔널 바인딩 (Optional Binding)](#2-옵셔널-바인딩-optional-binding)
  - [옵셔널 체이닝](#옵셔널-체이닝)


## 옵셔널이란? 
- 값이 있을 수도 있고, 없을 수도 있음을 나타내는 표현
- 스위프트에서 새로 도입된 개념 -> 프로그래밍 언어 차원에서 안정성을 최대한 높이고자 사용
- 오류가 발생할 경우, `nil`이라는 값을 반환하도록 함으로써 오류를 최소화 할 수 있음

## 옵셔널 해제 방법

#### 1. 강제 언래핑 (Forced Unwrapping) : `!` 사용

```swift
var name: String? = "Danna"

print(name) // Optional("Danna")
print(name!) // Danna
```
  - 옵셔널 변수 뒤에 `!`를 붙여주면, 옵셔널이 해제되어 실제 값이 출력됨
  - 가장 간단히 해결할 수 있는 방법이지만, 값이 `nil`일 경우, 런타임 오류가 발생할 수 있음 (앱이 꺼짐)    
<br>

#### 2. 옵셔널 바인딩 (Optional Binding)
   
**(1) [if let]**   

```swift
var name: String? = "Danna"
if let value = name {  
print("\(value)입니다.") // Danna입니다.
}
// name이 nil이 아니라면, name을 unwrapping하여 상수 value에 할당
```
- Swift 5.7 `if let shorthand` syntax에 의해 구문을 더 간단하게 표현 가능    
  [if let shorthand](https://github.com/apple/swift-evolution/blob/main/proposals/0345-if-let-shorthand.md)

```swift
var name: String? = "Danna"
if let name {
print("\(name)입니다.") // Danna입니다.
}
// Swift 5.7 이상부터 사용 가능
```

- 옵셔널 해제한 변수는 지역변수로 사용되기 때문에, `if let` 구문 안에서만 사용 가능
- `else`문 생략 가능  
<br>

**(2) [guard let]**  


```swift
func testOptionalBinding() {

    var name: String? = "Danna"

    guard let value = name else { return }

    print("\(value)입니다.") // Danna입니다.
}
// name이 nil일 때 else 구문이 실행되고, return으로 함수를 종료시켜서 이후 코드가 실행되지 않음
```

- `if let`과 다르게 `guard let`은 `else` 구문을 반드시 포함해야 함
- `guard let`은 특정 코드블록 (함수, 메서드, 반복문 등) 내부에 있지 않으면 사용할 수 없음
- **early exit** 이라는 특징을 가지고 있음 -> 조건에 맞지 않으면 바로 종료하기 때문

<br>


## 옵셔널 체이닝
  
* nil값을 점검할 때 간결하게 표현할 수 있는 코드로, 불필요한 코드와 과정을 생략
  
```swift
// Optional Chaining
var name: String? = "Danna"
var age: Int? = 20

var myName: String? = name?.uppercased()
```
- 옵셔널 체이닝을 사용하면, 옵셔널 변수에 값이 있을 때만 해당 코드가 실행되고, 값이 없을 때는 바로 `nil`을 반환
- `?`를 사용하여 옵셔널 체이닝을 사용할 수 있음
