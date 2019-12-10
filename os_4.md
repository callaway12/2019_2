# File System
* Long-term Information Storage
    - Must store large
    - info survive the termination of thre process using it
        - persistent
    - multiple processes must be albe to access the info

    - Solution
        - store in units called file
        - info in files must be persistent
        - File System : blahblah
* File system GOAL
    - ***linear sequence of fixed-size blocks***
    - How do you find info?
    - How do you keep one user from readin another's
    - How do you know which blocks are free??
* File
    - Nothing but a sequence of bytes
    - Fixed-length records have internal structure
    - Tree
        - through KEY
    
* File Types
    - Regular file
        - ASCII : displayed and printed as is
        - binary files : 
            - Magic number : identify file types (whether executable)
            1. executable
            2. archive
    - Directories
    - Character special files
    - Block special files

    - Sequential access
        - read all bytes/records from the beginning
        - no jump / but can rewind or back up
        - good for medium (mag tape)
    - Random access
        - read any order
        - essential for data base system
        - read can be
            - move file marker (seek), then read or ...
            - read and then move file marker
* Directories
    - single level directory system
    - list of (name of file, file attributes)
    - attributes include
        - size, protection, location on disk, creation time, access time, ..
    - directory list is usually unordered (effectively random)
        - when you type "is", the "is" command sorts the results for you
* Hierarchical Directory Systems
    - Path name
        - absolute
            - cd /usr/local
        - relative
            - cd bin
* Path Name Translation
    - fd = open("/one/two/three", O_RDWR);
    - open directory “/” (well known, can always find)
    - search the directory for “one”, get location of “one”
    - open directory “one”, search for “two”, get location of “two” – open directory “two”, search for “three”, get loc. of “three” – open file “three”
    - (of course, permissions are checked at each step)
* File System Implementation
    - MBR (Master Boot Record) : 
        - for boot the computer
        - partition table
            - Starting and ending addr of each partition
            - One of the partitions is marked as active
    - Boot sequence
        - BIOS reads in & executes the MBR
        - MBR locates active partition, reads in its first block, called boot block, and execute
        - boot block -> load OS 
    - <img width="660" height="350" src="./os_img/os_file_layout_ex.png"></img>
    - Super Block
        - Key params of file system
            - Magic number to identify the file system type
            - Number of blocks,, etc..
    - Free space mgmt
        - A bitmap or list of pointer
    - I-nodes
        - Attributes and disk addr of the file's blocks
    - Root dir
    - Files and directories
* Implementing Files
    - Contiguous Allocation
        - 장점 
            - Simple to implement : one disk addr + # of blocks
            - Excellent performance in seek (only one seek)
        - 단점
            - Disk fragmentation -> external fragmentation
        - USAGE
            - CM-ROM file sys
            - File size known in advance
            - No change in size
    - Linked List Allocation
        - Use pointer to next File block
        - 장점 :
            - Yes internal fragmentation, 
            - No external fragmentation
                - All blocks can be used
        - 단점 :
            - Slow for both sequential and random access (random 이 더 느림)
            - Lost bytes for pointer
                - 왜냐면 pointer 에 사용되는 block 이랑 그게 가리키는 block 이랑 두개를 읽어야하기 떄문에
    - Linked List Allocation using Table in Mem
        - 장점 :
            - 임의 접근 용이
            - 디스크 참조 필요 ㄴ
        - 단점 :
            - 전체 테이블이 메모리에 존재
            - 용량이 크다
        - ???????????????????????
        - One Single file allocation table in mem to decribe layout of the entire disk
        - Each entry in table refers to a specific cluster within a file
            - zero says cluster not userd
            - not zero says where the next FAT entry for the file is
        - File's directory entry points to the first FAT entry for the file
    - Limits of FAT
        - FAT index is 16bits
            - 1 disk can have up to 64K clusters
        - disks get bigger, cluster size must increase
        - Big cluster yiedls internal fragmentation 
        - Minimum of one file per cluster?????????
            - limitation to 64K files
        - FAT itself is a critical resource
            - lose the FAT on disk, lost the whole disk
    - FAT
        - 장점 :
            - random access is much easier
            - chain can be followed without making any disk references
            - dir entry keeps the starting block number
        - 단점 :    
            - entire table must be in mem
* I-nodes (index-nodes)
    - List attributes and disk addr of a file
    - Last disk addr for the addr of a block containing more disk block addrs
    - 장점 :
        - 어떤 파일을 열면 해당 파일의 i-node 만 메모리에 가지고 있으면 된다.
    - 단점 :
        - 디스크 block addr 을 저장할 수 있는 공간이 유한하다.
            - 마지막 주소에 데이터를 저장하지 않고 다른 디스크 block 주소를 넣는다.
    - <img width="600" height="400" src="./os_img/os_disk_layout.png"></img>
* summary
    - what is Super block?
        - 
    - I-node is what?
        -
    - Directory?
        - 
    - Data blocks?
* Directory Internals
    - just file but has specail metadata
* Fixed Length Directory Entry
    - Window / MS-DOS (Simple directory)
        - fixed size entries
        - disk addr and attributes in **directory entry**
    - Unix (Directory with i-node)
        - fixed size entries + i-node number
        - disk addr and attributes in **i-node**
* Handling Long File Names
    - <img width="500" height="450" src="./os_img/os_handling_long_fileName.png"></img>
    - 위에서 보면 고정된 크기의 이름만 들어가는데
    - 왼 : In-line // 우 : In a heap
    - 왼쪽이 고정된 크기의 이름이고 오른쪽이 해당하는 파일에서 이름을 가리키는 포인터 heap을 가리키는 포인터가 있고 밑에 attribute들이 존재하는 형식
* Speeding up the File Name Search
    - Hash table
        - hashing file name
        - more complex administration
        - Large number of files 일때 굳
    - Caching
        - caches the results of searches
        - Small number of files 일때 굳
* Shared Files
    - 