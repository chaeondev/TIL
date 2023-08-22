# RTL(Right To Left) - trailing, leading 쓰는 이유

## 1. RTL이란?

* RTL은 Right To Left의 약자로, 오른쪽에서 왼쪽으로 읽는 언어를 지원하는 기능이다. 
* 아랍어와 같은 언어 대응을 위해서 직접 대응할 필요가 없다 (iOS 9 이상부터는 자동으로 지원)

## 2. Trailing, Leading을 사용하는 이유

* layout을 잡기위해 left, right 키워드가 있음에도 불구하고, trailing, leading 키워드를 사용하는 이유는 RTL을 지원하기 위해서이다.
* left, right로 layout을 잡으면, 자동적으로 RTL, LTR 전환을 지원하지 않는다.
=> 따라서 현지화에 대한 대응, 국가별로 다른 언어를 지원하기 위해서 trailing, leading을 사용하는 것!

## 3. 예시

* 아래의 예시는 아랍어를 지원하기 위한 예시이다.

```swift
// 아랍어를 지원하지 않는 경우
let label = UILabel()
label.text = "Hello World"
label.textAlignment = .right
```

```swift
// 아랍어를 지원하는 경우
let label = UILabel()
label.text = "Hello World"
label.textAlignment = .natural
```

## Reference

* [RTL-Apple Documentation](https://developer.apple.com/design/human-interface-guidelines/right-to-left)