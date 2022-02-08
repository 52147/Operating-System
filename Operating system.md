# Operating system (OS)


- research project due 5/3 ; orginality 10% below
- powerpoint 10-15;  word 1500 ; 2 picutres
- topic: 
- CPU scheduling algorithms and mechanisms, process synchronization & deadlocks and its algorithms, paging and page tables mechanisms, disks scheduling algorithms, filesystems (NFS, ZFS, NTFS), Linux filesystems, fIlesystems interface/implementation/internals, OS security and protection mechanisms/algorithms. Note that ALL algorithms must be OS kernel algorithms.

- punched card:
  -  also known as Hokkerith card or IBM cards,
  -  are paper cards where holes may be punched by hand or machine to represent computer data and instuctions.
  -  They were a widely-used means of inputting data into early computer.

- one card is one line of the program
![image](https://user-images.githubusercontent.com/79159894/151080054-72847f0b-c37f-47f5-a348-4ef6fb28b01e.png)




- altair 8800:
  - The Altair is widely recognized as the spark that ignited the microcomputer revolution 
  - as the first commercially successful personal computer. 
  -  first commercially successful personal computer.
  -  The Altair 8800 is a microcomputer designed in 1974 by MITS and based on the Intel 8080 CPU.
![image](https://user-images.githubusercontent.com/79159894/151079890-75d1410e-cc83-44c8-8a50-1706775d245b.png)


OS video:
- how is everything with you?
- grow my experience
- how good i fun?

## Chapter 1 
### Introduction
- A operating system is software that manages a computer's hardware.
- It also provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.
- It is important first to understand the organization and architecture of computer hardware.
- This inculuds 
- 1. the CPU
- 2. memory
- 3. I/O divices
- 4. storage.
- A fundamental responsibility of an operatong system is to allocate these resources to programs.
- we cover several topics to help set the stage for reminder of the text:
  - 1. data structures used in operating systems
  - 2. computing environments
  - 3. open-source 
  - 4. free operating systems. 
   
### Operating systems role in the overall computer system
  - A computer system can be divided roughly into four components:
    - 1. hardware :
       - the central processing unit (CPU), 
       - the memory
       - and the input/output(I/O) devices
       - provides the basic computing resources for the system. 
    - 2. the operating system :
       -  controls the hardware and coordinates its use among the various application programs for the various users.
    - 3. the application programs :
       - such as word processors, spreadsheets, complier, and web browsers
       - defined the ways in which these resources are used to solve user's computing problems. 
       - it's provides an enviroment within other programs can do useful work.
    - 4. a user
    
- We next explore operating systems from 2 viewpoints:
-  that of the user and that of the system.
#### User view
- The user's view of the computer varies according to the interface being used.
- Many computer users sit with a laptop or in front of a PC consisting of a monitor, keyboard, and mouse.
- Such a system is designed for user to monopolize its resources.
- The goal is to maximize the work that the user is performing.
- In this case, the operating system is designed mostly for easy of use, with some attention  paid to performance and security 
- and none paid to resource utilization -- how various hardware and software resources are shared.

#### moblie computer
- The user interfaces for mobile computers generally features a touch screen, where the user interacts with the system by pressing and swiping fingers across the screen rather than using a physical keyboard and mouse.
- Many mobile devices also allow users to interact through a voice recognition interface, such as Apple's Siri.

#### Computers with no user view
- for example, embedded computers in home devices and automobiles may have numeric keypads
- and may turn indicator lights on or off to show status,
- but they and they operating systems and applications are designed primarily to run without user intervention.

#### System view
- From the computer's point of view,
- the operating system is the progtam ,ost intimately invilved with the hardware.
- we can view an operating system as a resource allocator
- A computer ststem has many resources that may be required to solve a problem:
 - 1. CPU time
 - 2. memory space
 - 3. storage space
 - 4. I/O devices, and so on.

#### operating system is a resource allocator
- The operating system acts as the manager of these resources.
- Facing numerous and possibly conflicying requests for resources,
- the operating system must decide how to allcoate then to specific programs and users 
- so that it can operate the computer system efficiently and fairly.

#### operating system is a control program
 - A slightly different view of an operating system emphasized the need to control the various I/O devices and user programs.
 - A operating system is a control program.
 - A control program manages the execution of user programs to prevent errors and improper use of the computer.
 - It is especially concerned with the operation and control of I/O devices.
    
#### 1980 operating system were born : Moore's Law
- In 1960s, Moore's Law predicted that the number of transistors on an integrated circuit would double every 18 months, and the prediction has held true.
- Computer gained in functionality and shrank in size, 
- leading to a vast number of uses and a vast number and variety of operating systems.

#### system kernal
- We have no universally accepted definition of what is part of the operating system.
- A more common definition , and the one that we usually follow, is the ath operating system is the one program running at all times on the computer
- -- usually called the kernel.
- Along with the kernal, there are 2 other types of programs:
  - 1. system programs:
    - which are associtaed with the operating system but are not necessarily part of the kernal,
  - 2. application programs:
    - which include all programs not associated with the operation of the system

#### Mobile operating systems : middleware
- mobile operating systems often include not only a core kernal but also middleware
- -- a set of software framwork that provide additional services to application developers.
  - For example:
    - each of the two most prominent mobile operating systems
    - -- Apple's iOs and Google's Android
    - -- features a core kernal along with middleware that supports databases, multimediam and graphics.



- In summary, the operating system includes 
  - 1. the always running kernal,
  - 2. middleware framworks :
    - that ease application development and provide features 
  - 3. system programs :
    - that aid in managing the system while it is running. 

### 1.2 Computer-System Organization

#### Device controller
- A modern gernal-purpose computer system consists of one or more CPUs and a number of device controllers connected through a common bus that provides access between components and shared memory. 
- Each device controller is in charge of a specific type of device 
- (for example, a disk drive,audio device, or graphics display). 
- Depending on the controller, more than one device may be attached. 
  - For instance, one system USB port can connect to a USB hub, to which several devices can connect. 

- A device controller maintains some local buffer storage and a set of special-purpose registers. 
- The device controller is responsible for moving the data between the peripheral devices that it controls and its local buffer storage.
- Typically, operating systems have a device driver for each device controller. This device driver understands the device controller and provides the rest of the operating system with a uniform interface to the device. 
- The CPU and the device controllers can execute in parallel, competing for memory cycles. To
ensure orderly access to the shared memory, a memory controller synchronizes access to the memory.
- In the following subsections, we describe some basics of how such a system operates, focusing on three key aspects of the system. We start with interrupts,
-  which alert the CPU to events that require attention. We then discuss storage structure and I/O structure.

#### 1.2.1 Interrupts: device controller : operation finished -> device driver 
- Consider a typical computer operation: a program performing I/O. 

- To start an I/O operation, the device driver loads the appropriate registers in the device controller. 
- The device controller, in turn, examines the contents of these registers to determine what action to take
- (such as “read a character from the keyboard”).

- The controller starts the transfer of data from the device to its local buffer. 
- Once the transfer of data is complete, the device controller informs the device driver that it has finished its operation.
- The device driver then gives control to other parts of the operating system, possibly returning the data or a pointer to the data if the operation was a read. 
- For other operations, the device driver returns status information such as “write completed successfully” or “device busy”.
  
- But how does the controller inform the device driver that it has finished its operation? 
- This is accomplished via an interrupt.


## Chapter 2 Operating system structure

- We can view an operating system from several vantage points.
- 1. One view focuses on the services that the system provides;
- 2. on the interface that it makes available to uses and programmers.
- 3. on its components and their interconnections.


### 2.1 Operating system services
- 1. User interface:
     - Almost all operating systems have a user interface(UI).
     - This interface can take several forms.
     - 1. GUI (graphical user interface)
          - Most commonly, a **graphical user interface (GUI)** is used.
          - the interface is a window system with a mouse that serves as a pointing device to direct I/O,
          - choose from menues, and make selections and a keyboard to enter text.
     - 2. touch-screen interface
          - Mobile systems such as phones and tablets provide a touch-screen interface,
          - enabling users to slide their fingers across teh screen or press buttons on the screen to select choices.
     - 3. CLI (command-line interface)
          - which uses text comaands and a method for entering them
          - (a keyboard for typing in commands in a specific format with specific options).     
- 2. Program execution:
- 3. I/O operations
- 4. File-system manipulation :
     - programs need to read and wrire files and directories.
     - They also need to create and delete them by name, search for give file, and list file information.
     - some operating systems include permissins management to allow or deny access to files or directories base on file ownership.
     - Many operating systems provides a variety of file systems,
     - sometimes to allow personal choice and sometimes to provide specific features or performance characteristics. 
- 5. Communications:
     - There are many circumstances in which one process needs to exchange information with another process.
     - Such communication may occur between processes that are executing on the same computer or between process that are executing on different computer systems tied together by a network.
     - 1. shared memory:
       - Communications may be implemented via shared memory,
       - in which 2 or more processes read and write to a shared section of memory,
     - 2. message passing:
       - in which packets of information in predefined formats are moved between processes by the operating system. 
- 6. Error detection:
- 7. Resource allocation
- 8. Logginh
- 9. Protection and security

### 2.3 System calls
- Systems calls provide an interface to the services made available by an operating system.
- These calls are generally available as functions written in C and C++, although certain low-level tasks
- (for example, tasks where hardware must be accessed directly)
- may have to be written using assembly-language instructions.

#### how system calls are used:
- Before we discuss how an operating system makes system calls available,
- let's first use an example to illustrate how system calls are used:
  - writing a simple program to read data from one file and copy them to another file.
  
  - The first input that the program need is the names of the 2 files:
     - the input file and the output file.
     - These names can be specified in many ways, depending ob the operating-system design.
     - 1. command
       - One approach is to pass the names of the two files as part of teh command
       - --for example, the UNIX cp command:
         - cp in.txt out.txt
         - This command copies the input file in.txt to the output file out.txt.
     - 2. system calls
         - A second approach is for the program to ask the user for the names.
         - In an interactive system, this approach will require a sequence of system calls,
         - first to write a prompting message on the screen and then to read form the keyboard the characters that define the two files.
         - On mouse-based and icon-baseed systems,
         - a menu of file names is usually displayed in a window.
         - The user can then use the mouse to select the source name, 
         - and a window can be opended for the destination name to be specified.
         - This sequence requires mant I/O system calls.
    
  - Once the two file names have been obtained, the program must open the input file and create and open the output file.
  - Each of these operations requires another system call.
  - Possible error conditions for each system call must be handled.
    - For example, when the program tries to open the input file, it may find that there is no file of that name or that the file is protected against access.
    - In these case, the program should output an error message 
    - (another sequence of system calls)
    - and then terminate abnormally(another system call).
    - If the input file exists, then we must create a new output file.
    - We may find that there is already an output file with the same name,
    - This situation may cause the program to abort(a system call),
    - or we may delete the existing file(a system call)
    - and create a new one(yet another system call).
    - Another option, in an interactives system, is to ask the user(via a sequence of system calls to output the prompting message and to read the response from the terminal)
    - whether to replace the existing file or to abort the program.
    - When both files are set up, we enter a loop that reads from the input file(a system call)
    - and writes to the output file(another system call).
    - Each read and write must return status information regarding various possible error coditions.
    - On input, the program may find that the end of the file has been reached or that there was a hardware failure in the read(such as a parity error).
    - The write operation may encounter various errors, depending on the output device (for example, no more available disk space).
    - Finally, after the entire file is copied, the program may close both files(2 system calls),
    - write a message to the console or window(more system calls),
    - and finally terminate normally(the final system call).

### 2.3.2 API (Application programming interface)
- As you can see, even simple programs may make heavy use of the operating system.
- Frequently, systems execute thousands of system calls per second.

- Application developers design programms according to an application programming interface(API).
- The API specifies a set of functions that are available to an application programmer,
- including the parameters that are passed to each function and the return values the programmer can expect.
- Three of the most common APIs available to application programmers are 
- 1. the Windoes API for Windows systems, 
- 2. the POSIX API for POSIX-based systems(which include virtually all versions of UNIX, LINUX,and macOS)
- 3. JAVA API for programmers that run on the java virtual machine

- A programmer accesses an API via library of code provided by the operating sysytem.
- In the case of UNIX and Linux for programs written in the C language, the library is called libc.
- Note that-- each operating system has its own name for each system call.

- The functions that make up an API typically invoke the actual system calls on behalf of the application programmer.
  - for example,
  - the Windows function CreateProcess()
  - (which, unsurprisingly, is used to create a new process)
  - actually invokes the NTCreateProcess() system call in the Window kernel.

#### use API to invoke system call
- Why would an application programmer prefer programming according to an API rather than invoking actual system calls?
    
### 2.3.3 Types of System calls
- System calls can be grouped roughly into six major categories:
- 1. process control
- 2. file management
- 3. device management
- 4. information maintenance
- 5. communications
- 6. protection
- These types of system calls normally provided by an operating system.

## 2.3.3.1 Process Control

### Stacks



## Part two Process Management
- A process is a program in executin.
- A process will need certain resources -- such as CPU time, memory, files, and I/O devices -- to accomplish its task.
- These rsources are typically allocated to the process while it is executing.
- A process is the unit of work in most systems.
- operating- system processes execute system code,
- and user processes execute user code.

- Modern OS support processes having multiple threads of control.
- On systems with multiple hardware processing cores, these threads can run in pareallel.

- One of the most aspects of an OS is how it schedules threads onto available processing cores.
- Several choices for designing CPU schedulers are available to programmers. 

** Chapter 3 Processes
- A system consists of a collection of processes,
- some executing user code, others executing opreating system code.
- All these processed can execute concurrently, with the CPU multiplexed among them.

### 3.1 Process concept

### 3.1.1 The process
- Informally, a process is a program in execution.
- The status of the current activity of process is represented by the value of the program counter
- and the contents of the processor's registers
- The memory layout of a process is divided into multiple sections.
- These sections include:
#### The memory layout of a process
- Text section: the executable code
 
- Data section: global variables

- Heap section: memory that is dynamically allocated during program run time

- Stack section: 
  - temporary data storage when invoking functions
  - (such as function parameters, return addressed, and local variable)

- 
