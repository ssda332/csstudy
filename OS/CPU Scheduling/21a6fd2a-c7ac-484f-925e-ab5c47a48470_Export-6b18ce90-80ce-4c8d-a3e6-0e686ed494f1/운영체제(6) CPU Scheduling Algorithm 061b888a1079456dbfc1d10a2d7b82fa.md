# 운영체제(6). CPU Scheduling Algorithm

## 성능척도

- 이용률
- 처리율
- 사용자 입장에서의 성능척도
    - 소요시간, 반환시간(프로세스의 시작과 종료를 뜻하는게 아닌 프로세스가 레디큐에 들어와서 나가기까지의 시간만을 뜻함)
    - 대기시간(순수하게 줄서서 기다리는 시간)
    - 응답시간(레디큐에 들어와서 처음 cpu를 얻을때까지의 시간)

대기시간과 응답시간의 차이는 대기시간은 CPU를 넘겨주고 다시 Ready상태인 모든 시간을 합한것을 뜻하고 응답시간은 처음 들어와서 cpu를 얻을때까지의 시간을 뜻함

### FCFS(First-come First-Served)

- 먼저 온 순서대로 처리하는것
- 비선점형 구조
- 효율적이지 않다
- CPU를 길게 쓰는 프로세스가 먼저 도착하면 비효율적임(Convoy effect).

### SJF (Shortest-Job-First)

- **CPU burst time**이 가장 짧은 프로세스를 제일 먼저 스케줄
- **minnum average waiting time**을 보장
    - Nonpreemptive - 한번 CPU를 잡으면 이번 burst가 완료될 때까지 CPU를 빼앗기지 않음
    - Preemptive - 더 짧은 친구가 도착하면 뺏어서 넘겨줌 (SRTF)

- 문제점
    - CPU burst time이 엄청 긴 프로세스는 항상 후순위로 밀리는 문제가 있음(Starvation)
    - CPU 사용시간을 미리 알 수 없음(추정은 가능)

### Priority Scheduling

- 우선순위가 가장 높은 프로세스에게 CPU를 주는것
- Nonpreemptive, Preemptive로 나뉠수 있음
- Solution : aging(노화) - 오래 기다린 프로세스는 우선순위를 조금씩 높여줌

### Round Robin (RR)

- 각 프로세스는 동일한 크기의 할당 시간(time quantam)을 가짐
- 시간이 다되면 CPU를 뺏김
- 응답 시간이 짧아짐
- 기다리는 시간에 비례해서 Q TIME이 주어짐 (n-1)q time unit

### Multilevel Queue

- system processes
- interactive process
- interactive editing processes
- batch processes
- studen processes
-