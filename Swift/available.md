# available Keyword

## available 키워드란?

available 키워드는 특정 플랫폼에서 사용 가능한 API를 지정하는데 사용한다.

## #available vs @available

### #available

```swift
if #available(iOS 10, macOS 10.12, *) {
    // iOS 10 이상, macOS 10.12 이상에서 사용 가능한 API
} else {
    // iOS 10 미만, macOS 10.12 미만에서 사용 가능한 API
}
```
- #available은 if문 내에서 사용한다.
- *는 그 외의 모든 플랫폼에서 사용 가능한 API를 의미한다.

### @available

```swift
@available(iOS 10, macOS 10.12, *)
func foo() {
    // iOS 10 이상, macOS 10.12 이상에서 사용 가능한 API
}
```
- @available은 함수, 클래스, 프로퍼티, enum, struct, protocol 등에서 플랫폼을 제한할 수 있는 attribute이다.
- 해당 플랫폼 이하에서 실행시 에러가 발생

## Reference

- [@availble attribute - swift documentation](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/attributes/#available)
- [Availability Condition - swift documentation](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/statements/#Availability-Condition)