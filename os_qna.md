# OS 1 PROBLEMS
* Whay are the two main functions of an operating system?
    1. provideing application programmers a clean abstract set of resources indtead of the messy hardware ones
    2. managing these hardware resources
* What is multiprogramming?
    - 유저가 여러 프로그램을 동시에 사용하는것,
    - multiplexing (sharing) resources in two different ways:
        - time-sharing : response time 절감, must be fast, devide cpu time
        - mem-sharing : memory sharing
* In section 1.4, nine different types of operating systems are described. Give a list of applications for each of these systems( one per operating systems type )
    - Mainframe operating system: Claims processing in an insurance company. 
    - Server operating ystem: Speech-to-text conversion service for Siri. 
    - Multiprocessor operating system: Video -editing and rendering.
    - Personal computer operating system: Word processing application.
    - Handheld computer operating system: Context-aware recommendation system. 
    - Embedded operating system: Programming a DVD recorder for recording TV. 
    - Sensor-node operating system: Monitoring  temperature in a wilderness area. Real-time operating system: Air traffic control system.
    - Smart-card operating system: Electronic payment.
* To use cache memory, main memory is divided into cache lines, typlically 32 or 64 bytes long. An entire cache line is cached at once. What is the advantage of caching an entire line instead of a single byte or word at a time?
    - because of the locality, nearby locations next is very high!, cache hit !! increase
* What is spooling? Do you think that advanced personal computers will have spooling as a standard feature in the future?
    - job들을 mem에 쌓아두고 job 하나가 끝나면 바로 cpu가 다른 job을 실행할 수 있게 해주는것, 
    - ㄴ 왜냐하면 이게 batch system 이랑 비슷, 3장의 virtual mem 관리에서 job이 아닌 job의 한줄 한줄 계산을 하기 떄문에 ㄴ
* On early computers, every byte of data read or written was handled by the CPU. What implications does this have for multiprogramming?
    - CPU 에게 I/O interrupt 가 걸릴때 CPU 가 노니깐 그때 다른 프로세스를 쓰게 하기 위해서. 
* Why was timesharing not widespread on second-generation computers?
    - **Batch system** 이니깐 타임 쉐어링을 할 수 가 없지
* Instructions related to accessing I/O devices are typically privileged instructions, that is, they can be executed in kernel mode but not in user mode. Give a reason why these instructions are privileged.
    - 
* There are several design goals in building an operating system, for example, resource utilization, timeliness, robustness, and so on. Give an example of two design goals that my contradct on another
    - Consider fairness and real time. Fairness requires that each process be allo- cated its resources in a fair way, with no process getting more than its fair share. On the other hand, real time requires that resources be allocated based on the times when different processes must complete their execution. A real- time process may get a disproportionate share of the resources.
    - 모든 프로세스는 공평하게 돌아가야하는 real time 은 해당하는 dead-line 까지의 완수를 목적으로 하기에 상충한다.
* What is the difference between kernel and user mode? Explain how having two distinct modes aids in designing an os.
    - kernel 모드에서는 os가 직접적인 하드웨어의 관리를 도맡아 한다. user mode 에서는 제약되는 명령어들이 존재한다. 
    - PSW 라는 Program Status Word 가 어느 mode 인지 결정한다. 
    - user mode 에서는 I/O, mem access 가 제한된다.
    - Trap instruction 이 이러한 모드의 변환 명령어다
* A computer has a pipeline with four stages. Each stage takes the same time to do its word, namely, 1 nsec. How many instructions per second can this machine execute?
    - might be 4 nsec???????
    - wtf?
* 