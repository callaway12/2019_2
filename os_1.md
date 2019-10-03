# What is O.S
- help the programs can use hardware
- OS as an Extended Machine
    + Abstraction (Top - Down)
        - 정의하고 구현
        - 주어진 문제 해결
- 2 types of modes for OS
    + User mode
        - 제약 ㅇ
        - Routine call (applicaiton -> OS)
            + hardware controll 어려움
        - Function call (middleware -> User Interface Program)
            + gives back to User Interface
    + Kenel mode
        - 제약 ㄴ
        - all the things above the OS pass to OS
- System Call vs Function call
    + kernel 모드로 들어간다
    + 함수가 위치한 절대, 상대주소가 아닌 트립 명령은 임의의 주소로 이동불가
    - Sysytem call
        + change user mode to kernel mode
        + Trap 명령어(kernel mode로 들어가서 OS 구동하는거)
            - user mode 에서도 kernel mode 에서도 등장
            - user mode 에서 trap은 kernel mode 로 들어감
            - fault 발생시 trap 명령어 실행
            - OS 자체 예외처리 명령어 일종
- Resource Manager
    + (Down - Top)
    + Time
        - CPU Sharing
        - CPU 여러 프로그램에 나눠서 할당
        - 연산속도에 write read 속도를 못 따라가니깐 그 짬짬히 나눠서 쓰는거
        - 순서 상관 있음
    + Space (Multi programing, Multi tasking, Multiplexing)
        - Memory Sharing
        - 순서에 따라 할당 ㄴ
        - 자원의 일부를 갖는것
        - cf, Batch system
            + run only one program till its end
- Asynchronous I/O
    - 비동기 I/O device -> I/O 가 느리니 그 시간에 CPU/Mem 다른일 하는거
- Spooling
    + job들을 mem에 쌓아두고 job 하나가 끝나면 바로 cpu가 다른 job을 실행할 수 있게 해주는것
- CPU Pipelining
    + 
- PC(Program counter)
    + contains the memory address of next instruction to be fetced
- Stack pointer 
    + points top of the current stack in memory
- PSW (Program Status Word)
    + CPU의 현재 정보를 갖고 있는 reg, cpu 상태 저장
    + mode 저장하는 reg, (kernel mode, user mode)
- MMU (Memory Management Unit)
    + 추후 3장에서 업데이트 링크
- Multi processor system
    + interconnect 
        - 보통 하나의 bus 로 데이터 송수신
        - 고급은 각 processor 유기적으로 연결
    + Multithreaded and Multicore chips
        - L2 cache sharing by bus
        - each core has separate L2 cache
- I/O Devices
    + Interrupt
        + <img width="200" height="200" src="./db_img/io_devices_sequence.png"></img>
        + cpu 에서 디스크 data access 요청
        + kernel mode로 전환
        + 해당 요청을 각각의 Device Driver 에서 해당 Device로 요청
        + 디스크에서 data 준비 후
        + Interrupt controller 에서 cpu로 interrupt (I/O port space)
        + I/O Port 는 해당 I/O Device 별로 다른 register들
        + cpu 에서 준비되면 해당 data interrupt device 정보와 함께 전달
    + I/O Interrupt 는 언제든 바로바로 interrupt controller 에서 interrupt signal 보냄
    + Dispatch Routine
        + Interrupt 발생시 OS의 routine 을 불러냄
        + 각 I/O port 에 해당하는 reg에서 Interrupt handler 를 불러내야함
        + Interrupt vector를 통해 interrupt handler의 해당 주소값을 알아내서 해당 I/O 명령어 수행
        + 
    + DMA (Direct Memory Access)
        + Chip, H/W
        + data 크기, device 정보, mem addr, direction, 포함해서 
        + device controller 랑 mem 사이에서 cpu 개입 없이 진행
    + Interrupt during Interrupt
        + CPU 가 알아서 정해줌
## OPERATIONG SYSTEM ZOO
- Mainframe Operation System
    + Batch 
        + 한번에 하나만 처리
    + Transaction processing
        + handle many small tasks
    + Timesharing
        + many users run multiple jobs at once
- Server Operating System
    + 웹서버
    + linux, Solaris, Windows Server
- Multiprocessoer Operating System
    + 여러개의 cpu
- Personal Computer Operating System
    + 개인 피씨
- Handheld Computer Operating System
    + PDA
    + iOS, Android
- Embedded Operating System
    + TV, DVD, cars
- Sesor-Node Operating System
    + computers for Sensing
- Real-Time Operating System
    + Time is the key parameter
    + Hard real-time system
        - deadline 중요
        - 발전소 주요 제어 패널
        - 자동차 브레이크 
    + Soft real-time system
        - 통화 음성
## OS CONCEPT
- Processes
    - program which running
    - has its own **address space**