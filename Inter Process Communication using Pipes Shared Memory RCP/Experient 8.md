# Inter Process Communication using Pipes/Shared Memory/RPC

## Aim
The aim of this laboratory is to introduce the Inter-process communication (IPC) mechanism of the operating system to allow processes to communicate with each other.

## Learning Objective
Students will learn various IPC techniques to exchange information between different processes in a system. The primary focus will be on Pipes, Shared Memory, and Remote Procedure Call (RPC).

## Description
Inter Process Communication (IPC) is a mechanism offered by the operating system to facilitate communication between cooperating processes. This communication mechanism enables processes to transfer or share data and coordinate activities. IPC is supported by all UNIX systems and can be used within a single computer system or between different systems. Examples of IPC methods include Pipes, FIFOs (named pipes), Shared memory, Message queues, and Remote Procedure Call.

### Pipes
Pipes are the oldest form of UNIX System IPC, providing half-duplex communication between processes that have a common ancestor. A pipe is created using the `pipe` function.

#### Example: Program to illustrate Pipe communication
```c
#include<stdio.h>
#include<unistd.h>
#include<sys/types.h>
#include<string.h>
#include<stdlib.h>

int main() {
    int fd[2], nb;
    pid_t cpid;
    char inf[] = "Welcome to LPU\n";
    char rbuff[50];

    pipe(fd);

    if((cpid = fork()) == -1) {
        printf("Parent failed to create the child process");
        exit(1);
    }

    if(cpid == 0) {
        close(fd[0]);
        write(fd[1], inf, (strlen(inf) + 1));
        printf("The information written in the pipe by child is: %s", inf);
        exit(0);
    } else {
        close(fd[1]);
        nb = read(fd[0], rbuff, sizeof(rbuff));
        printf("The information received by the Parent process from the pipe is: %s", rbuff);
    }

    return 0;
}
```

#### Example: Program to illustrate Two-way Pipe communication
```c
#include<stdio.h>
#include<unistd.h>
#include<sys/types.h>
#include<string.h>
#include<stdlib.h>

void main() {
    int fd1[2], fd2[2], nb;
    pid_t cpid;
    char inf1[] = "Welcome to LPU";
    char inf2[] = "Thank you";
    char buff[100];

    pipe(fd1);
    pipe(fd2);

    if((cpid = fork()) == -1) {
        printf("Parent failed to create the child process");
        exit(1);
    }

    if(cpid == 0) {
        close(fd1[0]);
        close(fd2[1]);
        write(fd1[1], inf1, strlen(inf1) + 1);
        nb = read(fd2[0], buff, sizeof(buff));
        printf("\n The information received by the Child process is:%s\n", buff);
        exit(0);
    } else {
        close(fd1[1]);
        close(fd2[0]);
        write(fd2[1], inf2, strlen(inf2) + 1);
        nb = read(fd1[0], buff, sizeof(buff));
        printf("\n The information received by the parent process is:%s\n", buff);
    }
}
```

### Shared Memory
Shared Memory is an IPC mechanism where system memory is shared between two or more processes. Communication is done through this shared memory, allowing modifications made by one process to be visible to another process. The operating system assigns a memory segment in the address space for several processes to read and write without involving the kernel during data exchange.

#### Functions of IPC Using Shared Memory
- `shmget()`: Used to create the shared memory segment.
- `shmat()`: Used to connect the shared segment with the process's address space.
- `shmdt()`: Used to detach the shared segment from a process.
- `shmctl()`: Allows a process to control the shared memory segment.

#### Example: Program for IPC using Shared Memory (Write)
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/shm.h>
#include<string.h>

int main() {
    void *shm;
    char buf[200];
    int shmid;

    shmid = shmget((key_t)123, 2048, 0666 | IPC_CREAT);

    printf("The Key value of shared memory is %d\n", shmid);
    shm = shmat(shmid, NULL, 0);

    printf("Process attached to the address of %p\n", shm);
    printf("Write the data to shared memory\n");
    read(0, buf, 100);
    strcpy(shm, buf);
    printf("The stored data in shared memory is: %s\n", (char *)shm);

    return 0;
}
```

#### Example: Program for IPC using Shared Memory (Read)
```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/shm.h>
#include<string.h>

int main() {
    void *shm;
    char buf[200];
    int shmid;

    shmid = shmget((key_t)123, 2048, 0666);
    printf("The Key value of shared memory is %d\n", shmid);

    shm = shmat(shmid, NULL, 0);
    printf("Process attached to the address of %p\n", shm);

    printf("The retrieved data from the shared memory is: %s\n", (char *)shm);

    return 0;
}
```

### Remote Procedure Call (RPC)
RPC is an interprocess communication mechanism employed for client-server-based applications. It can be used within the same system or between different systems with a network connection. The client initiates communication with a procedure or function call, sending a request message to the server. The server executes the procedure, sends a response back to the client, and the client resumes execution.

#### Example: Remote Procedure Call (RPC)
*Example and explanation for RPC are not provided in the original text. Please add them based on your understanding of RPC.*

## Usage
- Compile each program using a C compiler (e.g., `gcc program.c -o program`).
- Run the compiled executables (e.g., `./program`).

## Notes
- Understand the concepts and implementation details of Pipes, Shared Memory, and RPC.
- Experiment with the provided examples and modify them to explore different scenarios.
- Note the impact of different IPC mechanisms on communication between processes.
