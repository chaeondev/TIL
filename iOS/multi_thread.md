# iOS의 Multh Thread

- [iOS의 Multh Thread](#ios의-multh-thread)
  - [Thread란?](#thread란)
  - [Multi Thread](#multi-thread)
  - [iOS에서의 Multi Thread](#ios에서의-multi-thread)
    - [Main Thread와 Background Thread](#main-thread와-background-thread)
    - [GCD(Grand Central Dispatch)](#gcdgrand-central-dispatch)

<div>

## Thread란?

Thread에 대해서 알려면 Program, Process, Thread에 대해 구분이 필요할 것 같음.

* Program: 작업을 실행할 수 있는 파일
  - 설치는 되어있으나 실행되지 않은 상태
  - 메모리에 올라가지 않은 상태

* Process: 메모리에 올라가서 실행되고 있는 프로그램
  - 독립적인 메모리 공간을 가지고 있기 때문에, 다른 프로세스의 메모리(변수나 자료구조)에 접근할 수 없음
  - 최소 하나 이상의 Thread를 가지고 있음

* Thread: 프로세스 내에서 실행되는 하나의 작업 단위
  - 프로세스 내의 주소 공간이나 자원들을 같은 프로세스 내에 스레드끼리 공유하면서 실행됨
  - 자체적으로 스택을 보유하고 동적 메모리 할당을 위해 힙을 공유함으로써 메모리와 상호작용함.

## Multi Thread

원래 하나의 프로세스 내에 한명의 알바생만 일했는데, 그 업무를 다른 알바생한테도 나누어 주는 거임.

즉, 하나의 프로세스 내에서 여러개의 Thread가 동시에 작업을 수행하는 것을 말함.

동시에 여러 작업을 수행하기에 빠르게 작업을 수행할 수 있지만, 어떤 작업이 먼저 끝나는지, 어떤 순서로 작업이 수행되는지 알 수 없음.

## iOS에서의 Multi Thread

### Main Thread와 Background Thread

* Main Thread
  
    - iOS에서는 하나의 프로세스 내에 하나의 Main Thread가 존재함.
    - UI를 업데이트하거나 사용자의 이벤트를 처리하는 등의 작업을 수행함.

* Background Thread

    - Main Thread를 제외한 나머지 Thread들을 말함.
    - Main Thread에서 처리하기에는 너무 많은 작업을 수행해야 할 때, Background Thread에서 처리함.
    - Background Thread에서 처리한 작업의 결과를 Main Thread에서 UI를 업데이트함.

### GCD(Grand Central Dispatch)

* GCD란?

    - iOS에서는 멀티 스레드를 쉽게 사용할 수 있도록 Apple에서 개발한 기술.
    - GCD는 애플리케이션 내의 작업을 여러개의 큐(Queue)로 관리함.
    - 큐(Queue)란, 먼저 집어 넣은 데이터가 먼저 나오는 FIFO(First In First Out)구조로 되어있는 자료구조를 말함.
    - 큐(Queue)에 작업을 넣으면, GCD가 알아서 적절한 스레드를 생성하고 관리함.

* DispatchQueue

    - GCD에서는 작업을 수행하는 스레드를 DispatchQueue라는 클래스로 관리함.
    - DispatchQueue는 Serial Queue와 Concurrent Queue로 구분됨.
    - Serial Queue는 작업을 순차적으로 처리하는 큐로, 하나의 스레드에서 작업을 처리함.
    - Concurrent Queue는 작업을 동시에 처리하는 큐로, 여러개의 스레드에서 작업을 처리함.