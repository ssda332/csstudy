# 운영체제(5). CPU Scheduling

### CPU and I/O Bursts in Program Execution

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(5)%20CPU%20Scheduling%204667bc91a59f4dc5971c39b1bff4bd83/Untitled.png)

- 프로그램이 실행될때 CPU 수행단계 - CPU Burst
- I/O 수행단계 - I/o Burst
- 프로그램의 특징에 따라 빈도나 길이가 달라질 수 있음.

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(5)%20CPU%20Scheduling%204667bc91a59f4dc5971c39b1bff4bd83/Untitled%201.png)

- I/O bound job은 CPU를 짧게 쓰기 때문에 그래프상 빈도수가 많이 나옴. 실질적으로 CPU를 오래 쓰는것은 CPU bound job임
- **I/O bound job**같은 Interactive job에 실행 우선순위가 주어지는게 **효율성** 면에서 좋음
- I/O bound process
    - CPU를 잡고 계산하는 시간보다 I/O에 많은 시간이 필요한 job
- CPU bound process
    - 계산 위주의 job

### CPU Scheduler & Dispatcher

- CPU Scheduler
    - Ready 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고른다
    - 운영체제 안에 CPU 스케줄링을 하는 코드가 있는데 그것을 CPU 스케줄러라고 부름
- Dispatcher
    - CPU의 제어권을 CPU 스케줄러에 의해 선택된 프로세스에게 넘긴다.
    - 이 과정을 context switch(문맥 교환)라고 한다.
    

![Untitled](%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%8E%E1%85%A6%E1%84%8C%E1%85%A6(5)%20CPU%20Scheduling%204667bc91a59f4dc5971c39b1bff4bd83/Untitled%202.png)

- Preemptive(선점형), Nonpreemptive(비선점형)
- 현대적인 cpu 스케줄링은 선점형 스케줄링을 거의 대부분 쓰고있음