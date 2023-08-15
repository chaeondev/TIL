# UINavigationController

* 공식문서에 따르면 `UINavigationController`에 대해 이렇게 표기되어 있음
> A container view controller that defines a stack-based scheme for navigating hierarchical content. 

이것에 대해서 설명해보자면, 
1. container view controller라는 것은 다른 view controller들을 포함할 수 있는 view controller라는 뜻임.
2. stack-based scheme라는 것은 stack이라는 자료구조를 이용해서 view controller들을 관리한다는 뜻
3. hierarchical content라는 것은 view controller들이 계층적으로 구성되어 있다는 뜻 -> `Drill-Down interface`라고도 함.

<img width="715" alt="Screenshot 2023-08-15 at 7 29 10 PM" src="https://github.com/chaeondev/TIL/assets/80023607/baec8b2b-ba4f-411f-b332-b5ba39da9c54">

* 네비게이션 컨트롤러는 계층적 컨텐츠이기 때문에 수직적 화면 전환 형식이다 

* 네비게이션 컨트롤러는 스택을 이용해서 화면을 관리하기에 스택의 가장 아래에 있는 뷰 컨트롤러를 `Root View Controller`, 그 외의 뷰 컨트롤러를 `Child View Controller`라고 한다.
    * Root Controller : 시작 페이지, 뒤로가기 버튼이 없음.
    * Child Controller : Root Controller를 제외한 나머지 뷰 컨트롤러들

* 화면전환 : Push - Pop
    * Push : 스택에 뷰 컨트롤러를 추가하는 것, 오른쪽에서 왼쪽으로 화면이 밀림
    * Pop : 스택에서 뷰 컨트롤러를 제거하는 것, 뒤로가기 버튼을 누르는 것과 같음

##### Reference

- [UINavigationController](https://developer.apple.com/documentation/uikit/uinavigationcontroller)