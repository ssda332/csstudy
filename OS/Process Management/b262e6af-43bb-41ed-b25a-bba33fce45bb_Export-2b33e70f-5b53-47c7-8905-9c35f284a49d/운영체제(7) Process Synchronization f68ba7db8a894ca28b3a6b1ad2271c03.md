# 운영체제(7). Process Synchronization

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(7)%20Process%20Synchronization%20f68ba7db8a894ca28b3a6b1ad2271c03/Untitled.png)

### Race Condition

- S-box를 공유하는 E-box가 여럿 있는 경우 Race Condition의 가능성이 있음
- 프로세스들간의 공유메모리를 사용하면 문제가 생길수 있음(멀티 쓰레드도 연관, 커널 데이터)

### OS에서의 race condition

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(7)%20Process%20Synchronization%20f68ba7db8a894ca28b3a6b1ad2271c03/Untitled%201.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(7)%20Process%20Synchronization%20f68ba7db8a894ca28b3a6b1ad2271c03/Untitled%202.png)

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(7)%20Process%20Synchronization%20f68ba7db8a894ca28b3a6b1ad2271c03/Untitled%203.png)

### 프로그램적 해결법의 충족 조건

- Mutual Exclusion (상호 배제)
    - 프로세스 Pi가 critical section 부분을 수행 중이면 다른 모든 프로세스들은 그들의 critical section에 들어가면 안 된다.
- Progress (진행)
    - 아무도 임계영역 안에 있지 않은 상태면 들어가게 해주어야 한다
- Bounded Waiting (유한 대기)
    - 프로세스가 임계 영역에 들어가려고 요청한 후부터 그 요청이 허용될 때까지 다른 프로세스들이 임계 영역에 들어가는 횟수에 한계가 있어야 한다.