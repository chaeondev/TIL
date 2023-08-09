# iOS의 계층구조

<img width="300" alt="Screenshot 2023-08-09 at 2 47 56 PM" src="https://github.com/chaeondev/TIL/assets/80023607/1bf5a83d-51de-4cd0-97a6-fb7ece0e1d12">

<!-- ![iOS architecture](https://github.com/chaeondev/TIL/assets/80023607/1bf5a83d-51de-4cd0-97a6-fb7ece0e1d12) -->
</br>

* **Cocoa Touch Framework** : UIKit, Foundation 등 개발자가 가장 많이 사용하는 Layer

    애플 환경에서 앱을 제작하기 위한 도구들의 모음

* **Media Layer** : 카메라, 영상, 미디어 파일

    그래픽, 미디어 등 멀티미디어 서비스 제공

* **Core Services** : GPS, 근접센서, 나침반 등

    기기 자체의 움직임이나 하드웨어 특성에 기반한 서비스 제공

* **Core OS** : iOS의 물리적인 기능 담당 ex) 배터리, wifi, 물리적인 버튼
    
    C기반 저수준 API, 하드웨어와 가까이 있는 최하위 계층 -> 개발자들이 수정하지 못하는 부분



