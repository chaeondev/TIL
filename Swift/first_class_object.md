# First Class Object 

- [First Class Object](#first-class-object)
  - [1. 변수 ・ 상수나 데이터 구조 내에 함수(자료형) 저장](#1-변수--상수나-데이터-구조-내에-함수자료형-저장)
  - [2. 함수의 반환값으로 함수(자료형) 사용](#2-함수의-반환값으로-함수자료형-사용)
  - [3. 함수의 인자값으로 함수(자료형) 전달](#3-함수의-인자값으로-함수자료형-전달)


First Class Object는 크게 3가지 특징을 가지고 있습니다.
1. 변수 ・ 상수나 데이터 구조 내에 자료형을 저장할 수 있다.
2. 함수의 반환값으로 자료형을 사용할 수 있다.
3. 함수의 인자값으로 자료형을 전달할 수 있다.

## 1. 변수 ・ 상수나 데이터 구조 내에 함수(자료형) 저장

```swift
func add(a: Int, b: Int) -> Int {
    return a + b
}

var function = add  // 함수 호출 연산자 없이 함수 할당 가능
                    // 함수만 대입한 것으로, 함수가 실행된 상태는 아님
```
해당되는 특성을 가지고 있다는 것은 함수 호출 형식이 확장된다는 것을 의미합니다.

-> 이는 함수 호출 연산자 () 없이 함수를 호출할 수 있다는 것을 의미하기도 합니다.

위의 코드에서 변수 `function` 은 함수 `add` 를 할당받았습니다.

`Function Type`은 `(Int, Int) -> Int` 입니다.

```swift
function(4, 2) // 6
```
이와같이 함수를 호출할 경우 변수인 function에 할당된 함수가 실행됩니다.

## 2. 함수의 반환값으로 함수(자료형) 사용

```swift
func currentAccount() -> String {
    return "계좌 있다는 얼럿 띄우기"
}
// () -> String

func noCurrentAccount() -> String { 
    return "계좌 없으니 계좌 생성 화면으로 이동"
}
// () -> String

func checkBank(bank: String) -> () -> String {
    let bankArray = ["우리", "신한", "국민"]
    return backArray.contains(bank) ? currentAccount : noCurrentAccount
}
```
위의 코드에서 `checkBank` 함수는 반환값으로 함수를 받습니다.
`currentAccount`와 `noCurrentAccount` 함수의 FunctionType은 `() -> String` 이기에 `checkBank` 함수의 반환값으로 사용할 수 있습니다.

```swift
let checkBankFunction = checkBank(bank: "우리")
checkBankFunction() // "계좌 있다는 얼럿 띄우기" 함수 호출
```

## 3. 함수의 인자값으로 함수(자료형) 전달

```swift
func oddNumber() {
    print("홀수")
}

func evenNumber() {
    print("짝수")
}

func resultNumber(number: Int, odd: () -> Void, even: () -> Void) {
    return number % 2 == 0 ? even() : odd()
}

resultNumber(number: 3, odd: oddNumber, even: evenNumber) // "홀수"
```
위의 코드에서 `resultNumber` 함수는 인자값으로 함수를 받습니다.

하지만 이 경우 의도하지 않은 같은 function type의 함수가 들어갈 위험이 있습니다. 그렇기에 사용되는 것이 클로저입니다.

```swift
resultNumber(number: 3, odd: { print("홀수") }, even: { print("짝수") }) // "홀수"
```
이름 없는 함수(익명 함수)인 클로저를 사용해서 함수를 전달할 수 있습니다. 이 또한 일급 객체의 특성에서 비롯된 것입니다. (클로저에 대한 내용은 다른 문서로 추가 예정)