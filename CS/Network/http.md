# HTTP 네트워크 통신

<br>

- [HTTP 네트워크 통신](#http-네트워크-통신)
  - [HTTP 통신의 특징](#http-통신의-특징)
    - [Connectionless: 비연결성](#connectionless-비연결성)
    - [Stateless: 무상태](#stateless-무상태)
    - [ATS: HTTP 통신의 특징으로 인한 애플의 정책](#ats-http-통신의-특징으로-인한-애플의-정책)
  - [Request](#request)
  - [API](#api)
  - [Response](#response)
    - [JSON과 XML](#json과-xml)
    - [Status Code(상태 코드)](#status-code상태-코드)
  - [iOS 네트워크 통신 라이브러리](#ios-네트워크-통신-라이브러리)

<br>
</br>

네트워크 통신의 가장 basic한 내용에 대한 이해부터 해보려고 한다. 그중에서 HTTP 통신에 대해 알아보자.

  
  ![IMG_303AC272D160-1](https://github.com/chaeondev/TIL/assets/80023607/0a7d174d-d1bf-4cbf-9903-f6e3de86f31f)

HTTP란 하나의 규약으로, 클라이언트와 서버가 데이터를 주고 받는 방식을 정의한 것이다.

* Hyper Text Transfer Protocol
* 인터넷에서 데이터를 주고 받을 수 있는 프로토콜

클라이언트(앱)가 서버에 Request를 보내면, 서버는 클라이언트에게 Response를 보내는 방식으로 통신한다.


## HTTP 통신의 특징

### Connectionless: 비연결성

* 요청이 10번 들어와도 항상 새롭게 연결을 다시 함. 연결이 유지되지 않음!
* 서버의 자원을 효율적으로 사용할 수 있으나, 항상 새로 연결하고 해제하는 과정때문에 요청에 대한 응답이 느림

### Stateless: 무상태

* 서버가 클라이언트의 상태를 보존하지 않는다. 
* 즉 서버가 클라이언트의 정보를 기억하고 있지 않아서, 클라이언트(사용자)를 식별할 수 없음
* 대응: 쿠키, 세션, 토큰 등을 사용하여 클라이언트를 식별함
  
### ATS: HTTP 통신의 특징으로 인한 애플의 정책

* ATS(App Transport Security) : 앱이 서버와 통신할 때, 보안을 강화하기 위해 iOS 9부터 도입된 기능 - 앱이 서버에 전송하는 데이터에 대한 보안 설정
* https를 사용하도록 강제하고, http 통신을 하려면 예외를 추가해야한다.
  
  

## Request

1) 요청이 있어야 응답을 한다.
    
    * `단방향 통신` : 항상 클라이언트가 먼저 요청을 보내야 서버가 응답을 보낼 수 있다.
    
      * 클라이언트가 요청을 보내지 않으면 서버는 아무것도 할 수 없다는 뜻임. 서버가 클라이언트에게 먼저 정보를 줄 수 없음.

  
2) HTTP Method : 요청의 종류를 구분하는 방법 -> GET, POST, PUT, DELETE 등이 있음
   
   * **GET** : 서버**에서** 클라이언트**로** 어떤 정보를 **가져오고** 싶을 때 사용하는 메서드 (ex. 게시글 목록 조회, 검색 결과 조회)

   * **POST** : 서버**에** 클라이언트**가** 어떤 정보를 **보내고** 싶을 때 사용하는 메서드 (ex. 게시글 작성, 번역 요청)

   * **PUT** : 서버에 클라이언트가 어떤 정보를 수정하고 싶을 때 사용하는 메서드 (ex. 게시글 수정)

   * **DELETE** : 서버에 클라이언트가 어떤 정보를 삭제하고 싶을 때 사용하는 메서드 (ex. 게시글 삭제)

3) 인증키(API Key) : 요청을 보낸 클라이언트가 누구인지 확인하는 방법, 믿을만한 사용자인지 입증해야함. 

## API

* Application Programming Interface
* API는 HTTP 통신을 할 때, 서버와 클라이언트가 어떤 메서드를 사용해서 어떤 데이터를 주고 받을지에 대한 규칙을 정의한 것이다.

## Response

### JSON과 XML

* XML(eXtensive Markup Language) -> 웹에 친화적

* JSON(Javascript Object Notation)  -> 모바일에 친화적
  
    * 키-값 쌍으로 이루어진 딕셔너리식으로 데이터를 표현함

* JSON 데이터 처리 방법
  * JSONSerialization -> 지금은 거의 안쓰임
  * SwiftyJSON -> Serialization을 기반으로 만들어짐
  * Codable -> Swift 4에서 새로 도입된 방식/ 훨씬 쉽고 자주 사용함

### Status Code(상태 코드)

* 404 에러와 같은 상태 코드를 통해 요청이 성공했는지 실패했는지 알 수 있다.


## iOS 네트워크 통신 라이브러리

1. URLSession : 애플에서 제공해주는데 쓰기 어려움
2. Alamofire / SwiftyJSON : 네트워크 통신을 쉽게 할 수 있도록 도와주는 라이브러리들

    * Alamofire가 request를, SwiftyJSON이 response를 처리함