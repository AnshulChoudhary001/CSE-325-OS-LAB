
## Lab Exercise: Operation on Processes using System Calls

This lab exercise involves writing C programs using system calls for operations on processes. The programs aim to simulate the creation of multiple processes, process hierarchies, and scenarios like orphan and zombie processes.

### Exercise 1: Simulating (2n – 1) Child Processes

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int n = 3; // Change n as needed
    int i, pid;

    for (i = 1; i <= n; i++) {
        pid = fork();
        if (pid == 0) {
            printf("Child process id: %d and its parent id: %d\n", getpid(), getppid());
            break;
        }
    }

    return 0;
}
```

This program uses system calls to simulate that n fork calls create (2n – 1) child processes. It prints the child process ID and its parent ID.

### Exercise 2: Creating a Process Hierarchy P1 → P2 → P3

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int pid1, pid2;

    printf("P1: %d\n", getpid());

    pid1 = fork();

    if (pid1 == 0) {
        printf("P2: %d, Parent: %d\n", getpid(), getppid());

        pid2 = fork();

        if (pid2 == 0) {
            printf("P3: %d, Parent: %d\n", getpid(), getppid());
        }
    }

    return 0;
}
```

This program creates a hierarchy of processes P1 → P2 → P3. It prints the process ID and parent ID for each process.

### Exercise 3: Creating a Hierarchy with Orphan and Zombie Processes

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int pid1, pid2, pid3, pid4, pid5;

    pid1 = fork();

    if (pid1 == 0) {
        printf("P2: %d, Parent: %d\n", getpid(), getppid());
        pid2 = fork();

        if (pid2 == 0) {
            printf("P4: %d, Parent: %d (Orphan)\n", getpid(), getppid());
            sleep(10);
        }
    } else {
        pid3 = fork();

        if (pid3 == 0) {
            printf("P3: %d, Parent: %d\n", getpid(), getppid());
            pid5 = fork();

            if (pid5 == 0) {
                printf("P5: %d, Parent: %d (Zombie)\n", getpid(), getppid());
                exit(0);
            }
        }
    }

    return 0;
}
```

This program creates a hierarchy of processes as shown in Figure 1, simulating P4 as an orphan process and P5 as a zombie process.

### Exercise 4: Creating a Hierarchy with Orphan and Zombie Processes (Figure 2)

```c
#include<stdio.h>
#include<sys/types.h>
#include<stdlib.h>

int main() {
    int pid1, pid2, pid3, pid4, pid5, pid6, pid7;

    pid1 = fork();

    if (pid1 == 0) {
        printf("P2: %d, Parent: %d\n", getpid(), getppid());
        pid5 = fork();

        if (pid5 == 0) {
            printf("P5: %d, Parent: %d\n", getpid(), getppid());
        }

        pid6 = fork();

        if (pid6 == 0) {
            printf("P6: %d, Parent: %d\n", getpid(), getppid());
        }
    } else {
        pid3 = fork();

        if (pid3 == 0) {
            printf("P3: %d, Parent: %d\n", getpid(), getppid());
            pid4 = fork();

            if (pid4 == 0) {
                printf("P4: %d, Parent: %d (Orphan)\n", getpid(), getppid());
                sleep(10);
            }

            pid7 = fork();

            if (pid7 == 0) {
                printf("P7: %d, Parent: %d (Zombie)\n", getpid(), getppid());
                exit(0);
            }
        }
    }

    return 0;
}
```

This program creates a hierarchy of processes as shown in Figure 2, simulating P4 as an orphan process and P7 as a zombie process.

### Explanation

- The programs utilize `fork()` for creating child processes.
- Orphan processes are simulated by having a child process outlive its parent.
- Zombie processes are simulated by making a child process exit while the parent is still running.

These programs provide hands-on experience in process management and system calls in a Unix-like environment. Students can observe the behavior of processes in different scenarios, enhancing their understanding of process operations.
