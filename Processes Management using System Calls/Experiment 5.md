## Experiment 5: Processes Management using System Calls

### Aim
The aim of this experiment is to introduce the concept of creating a new child process, performing operations on processes, and working with orphan and zombie processes.

### Learning Objectives
Students will be able to learn the following:
- Creation of a process using the `fork()` call.
- Process operations using `wait()` and `exec()` system calls.
- Understanding orphan and zombie processes.

### Programs

#### 1. Program to create a child process using fork

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int pid;
    pid = getpid();
    printf("Current process pid is %d\n", pid);
    printf("Forking a child process \n");
    pid = fork();
    
    if (pid == 0) {
        printf("Child process id: %d and its parent id: %d\n", getpid(), getppid());
    }
    
    printf("Parent process id %d\n", getpid());
    return 0;
}
```

This program demonstrates the creation of a child process using `fork()`. It prints the current process ID, forks a child process, and then prints the child and parent process IDs.

#### 2. Program to create an orphan process

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int pid;
    pid = getpid();
    printf("Current process pid is %d\n", pid);
    printf("Forking a child process \n");
    pid = fork();
    
    if (pid == 0) {
        printf("Child process is sleeping\n");
        sleep(10);
        printf("Orphan child parent id: %d\n", getppid());
    } else {
        printf("Parent process completed\n");
    }
    
    return 0;
}
```

This program creates an orphan process by forking a child and making it sleep. The parent process completes before the child, leaving the child as an orphan.

#### 3. Program to create a zombie process

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    pid_t a;
    a = fork();
    
    if (a > 0) {
        sleep(20);
        printf("PID of Parent %d\n", getpid());
    } else {
        printf("PID of CHILD %d\n", getpid());
        exit(0);
    }
    
    return 0;
}
```

This program creates a zombie process by forking a child and making the parent sleep for 20 seconds. The child process exits, and its entry remains in the process table as a zombie until the parent finishes execution.

### Explanation

- **fork()**: Creates a new process by duplicating the calling process.
- **wait()**: Causes the parent to wait for the child process to finish.
- **exec()**: Replaces the current process image with a new process image.
- **Orphan Process**: A child process whose parent process has finished.
- **Zombie Process**: A process that has finished execution but still has an entry in the process table.

These programs illustrate these concepts and provide a hands-on understanding of process management using system calls in C.
