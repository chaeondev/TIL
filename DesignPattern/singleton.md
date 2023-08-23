# Singleton Pattern

## 1. Singleton Pattern이란?

* Singleton Pattern은 디자인 패턴 중 하나로, 어떤 클래스의 인스턴스는 오직 하나임을 보장하며, 이 인스턴스에 접근할 수 있는 전역적인 접근점을 제공하는 패턴임
* 매번 인스턴스를 새로 생성하지 않고, 기존에 생성한 인스턴스를 재사용함으로써, 메모리 낭비를 방지할 수 있음
* 결론적으로 매번 초기화를 해주지 않아도 되며, 모든 View Controller에서 공통적으로 사용하는 인스턴스를 만들 때 유용함 (메모리적으로도 하나의 인스턴스 공간만 차지)

## 2. Singleton Pattern의 구현

```swift
class Singleton {
    static let shared = Singleton()
    private init() {}
}
```
* Type Property로 인스턴스를 저장해서 매번 새로 생성하는 인스턴스로 인한 메모리 낭비를 방지함
* `private init() {}`은 접근제어자로 외부에서 해당 클래스의 인스턴스를 생성하지 못하도록 함
  * 협업 시 실수로 인스턴스를 생성하는 것을 방지할 수 있음

## 3. Singleton Pattern에서 Class만 사용하는 이유

 * Struct는 Value Type이므로, 인스턴스를 전달할 때에는 값이 복사되어 전달됨
 * 반면에, Class는 Reference Type이므로, 인스턴스를 전달할 때에는 값이 복사되지 않고, 참조가 전달됨
 * Singleton Pattern에서는 인스턴스를 전역적으로 사용하기 위함이므로, 전달된 인스턴스가 동일한 인스턴스여야 함 -> reference type인 Class를 사용

## 4. Singleton Pattern의 사용 예시

* 이미 다양한 iOS Framework에서 Singleton Pattern을 사용하고 있음 

```swift
let application = UIApplication.shared
let userDefaults = UserDefaults.standard
let fileManager = FileManager.default
let notificationCenter = NotificationCenter.default
```