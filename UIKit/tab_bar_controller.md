# UITabBarController

* 공식문서에서 `UITabBarController`를 아래와 같이 표현한다.
> A container view controller that manages a multiselection interface, where the selection determines which child view controller to display.

이것에 대해 설명해보자면, 
1. container view controller라는 것은 다른 view controller들을 포함하는 view controller라는 것이다. (네비게이션 컨트롤러랑 동일)
2. multiselection interface는 여러개의 view controller들 중에 display할 view controller를 선택할 수 있다는 뜻이다. (네비게이션 컨트롤러는 수직적 구조이기 때문에 이런 선택이 불가능하다.)

<img width="682" alt="Screenshot 2023-08-15 at 7 48 51 PM" src="https://github.com/chaeondev/TIL/assets/80023607/392dd8cc-4d98-4497-a689-371489aada11">

* multiselection interface 특징 때문에 `UITabBarController`는 수평적인 화면 구조를 가지고 있음

* 화면전환: `UITabBarController`는 `UINavigationController`와 달리 화면전환을 위한 메서드를 제공하지 않는다.



##### Reference
- [UITabBarController](https://developer.apple.com/documentation/uikit/uitabbarcontroller)