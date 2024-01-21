# 운영체제(4). Process Management

### 프로세스 생성 (Process Creation)

- 부모 프로세스가 자식 프로세스를 생성한다
- 프로세스의 트리(계층 구조) 형성
- 프로세스는 자원을 필요로 함
    - 운영체제로부터 받는다
    - 부모와 공유한다
- 자원의 공유
    - 부모와 자식이 모든 자원을 공유하는 모델
    - 일부를 공유하는 모델 (Copy-on-write)
    - 전혀 공유하지 않는 모델
- 수행 (Execution)
    - 부모와 자식은 공존하며 수행되는 모델
    - 자식이 종료(terminate)될 때까지 부모가 기다리는(wait) 모델
- 주소 공간 (Address space)
    - 자식은 부모의 공간을 복사함 (binary and OS data) ex) PCB
- 유닉스의 예
    - fork () 시스템 콜이 새로운 프로세스를 생성
        - 부모를 그대로 복사 (OS data except PID + binary)
        - 주소 공간 할당
    - fork 다음에 이어지는 exec () 시스템 콜을 통해 새로운 프로그램을 메모리에 올림
    

### 프로세스 종료 (Process Termination)

- 프로세스가 마지막 명령을 수행한 후 운영체제에게 이를 알려줌(exit)
    - 자식이 부모에게 output data를 보냄 (via wait).
    - 프로세스의 각종 자원들이 운영체제에게 반납됨
- 부모 프로세스가 자식의 수행을 종료시킴 (abort)
    - 자식이 할당 자원의 한계치를 넘어섬
    - 자식에게 할당된 태스크가 더 이상 필요하지 않음
    - 부모가 종료(exit)하는 경우
        - 운영체제는 부모 프로세스가 종료하는 경우 자식이 더 이상 수행되도록 두지 않는다
        - 단계적인 종

### fork() 시스템 콜

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled.png)

- fork() 시스템 콜로 부모 프로세스가 자식 프로세스를 만들면 PCB(프로세스 정보)도 그대로 복제된다. 따라서 자식 프로세스는 fork()를 다시 수행하지 않고 부모 프로세스가 진행했던 코드 다음 코드부터 수행하게 된다.
- fork() 리턴 밸류도 부모와 자식이 다르다. 따라서 각각 다른 동작을 수행하도록 할 수 있다.

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled%201.png)

- exec()은 이전 기억은 잊어버리고 새롭게 덮어씌워줌.
- exec 이후의 코드는 실행하지 않음

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled%202.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled%203.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled%204.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(4)%20Process%20Management%2010e2c1d0467e4572b4dc72b7c3d81bb8/Untitled%205.png)

---

참조

[운영체제 - 이화여자대학교 | KOCW 공개 강의](http://www.kocw.net/home/search/kemView.do?kemId=1046323)