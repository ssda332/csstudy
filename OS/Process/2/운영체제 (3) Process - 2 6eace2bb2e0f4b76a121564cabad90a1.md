# 운영체제 (3). Process - 2

### Thread : CPU를 수행하는 단위

- Thread의 구성
    - program counter
    - register set
    - stack space
- Thread가 동료 thread와 공유하는 부분(=task)
    - code section
    - data section
    - OS resources
- 전통적인 개념의 heavyweight process는 하나의 thread를 가지고 있는 task로 볼 수 있다.
- 다중 스레드로 구성된 태스크 구조에서는 하나의 서버 스레드가 blocked(waiting)상태인 동안에도 동일한 태스크 내의 다른 스레드가 실행(running)되어 빠른 처리를 할 수 있다
- 스레드를 사용하면 병렬성을 높일 수 있다.

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6%20(3)%20Process%20-%202%206eace2bb2e0f4b76a121564cabad90a1/Untitled.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6%20(3)%20Process%20-%202%206eace2bb2e0f4b76a121564cabad90a1/Untitled%201.png)

### Thread의 장점

- 응답성 (Responsiveness)
    - 웹 브라우저가 쓰레드를 여러개 가지고 있으면 하나의 쓰레드가 멀리 있는 서버에서 자료(html문서, 이미지 등)요청을 할때 요청한 쓰레드만 blocked 처리가 되고 다른 쓰레드는 요청 작업을 지속할 수 있다.
- 자원의 공유 (Resource Sharing)
    - 똑같은 일을 하는 프로그램이 여러개가 있으면 → 하나의 프로세스를 만들고 여러 쓰레드로 만들게되면 code나 data, 프로세스의 자원 등을 공유할 수 있음
- 경제성 (Economy)
    - 프로세스를 하나 더 만드는것, 문맥 교환이 일어날때 → 오버헤드가 큼
    - 한 프로세스에 쓰레드를 하나 더 만드는것 → 상대적으로 오버헤드 크지 않음
- CPU가 여러개 있는 환경(MP Architectures)에서 쓰레드를 여러개 뒀을때 유용성
    - 여러개의 쓰레드가 여러개의 CPU에서 병렬적으로 수행이 가능
    

### 쓰레드의 구현 (Implementation of Threads)

- 커널 쓰레드 - 커널이 쓰레드가 여러개 있다는걸 아는것
- 유저 쓰레드 - 커널은 쓰레드가 여러개 있다는걸 모르고, 사용자 프로세스가 모든 쓰레드를 관리하는 것
- 실시간 쓰레드

---

참조

[운영체제 - 이화여자대학교 | KOCW 공개 강의](http://www.kocw.net/home/search/kemView.do?kemId=1046323)