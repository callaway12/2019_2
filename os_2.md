# Processes And Threads
* process 
    - address space
    - stack pointer
    - program counter
    - set of processor reg
    - set of system resources

* <img width="200" height="200" src="./os_img/os_unix_addr_space.png"></img>

* PID -> idex to - PT entry
* PT entry == Process Control BLock (PCB)

* in UNIX -> process creation -> fork()
    - fork() 하면 PCB 새로 만들어짐
    - new addr space
    - copy of the enitre contents of the addr space of the parent
    - initializes kernel resource of new process with resources of parent
    - new PCB on the ready queue
* fork()
    - parent 한테 chile 한테 system call return
    - parent -> child's PID
    - child -> return 0
    - 다른 주소공간, but No 메모리공유, 자원공유 O

    - 호출 이유:
        - 호출 이후에 자식 프로세스가 execve 부르기전에 자신의 파일 드스크립터들을 조작하여 방향을 변경할 수 있기 위함
* <img width="200" height="200" src="./os_img/os_fork_ex.png"></img>
    - ????????????????

* Fork and Exec
    - 