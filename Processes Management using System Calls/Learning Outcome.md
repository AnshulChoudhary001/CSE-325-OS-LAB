Learning Outcomes (What I Have Learnt)**

## Overview

This document provides an in-depth understanding of the learning outcomes achieved through the lab exercises on processes management using system calls. The exercises focused on creating, managing, and manipulating processes in a Unix-like environment using C programming language.

### Learning Outcomes

#### 1. **Understanding Process Creation**

In the first exercise, we explored the fundamental concept of process creation using the `fork()` system call. By creating a simple program, we simulated that n fork calls create (2n – 1) child processes. This exercise enhanced our understanding of how processes are duplicated in the system.

#### 2. **Process Hierarchy Creation**

The second exercise involved creating a process hierarchy (P1 → P2 → P3). By utilizing nested `fork()` calls, we gained hands-on experience in establishing a parent-child relationship among processes. We printed the process IDs and parent IDs for each process, solidifying our comprehension of hierarchical structures.

#### 3. **Simulating Orphan and Zombie Processes**

The third and fourth exercises delved into scenarios involving orphan and zombie processes. We simulated these situations by manipulating the execution flow and termination of processes. This practical experience allowed us to witness the behavior of orphan processes (a child outliving its parent) and zombie processes (a terminated child process still having an entry in the process table).

#### 4. **System Calls Usage: fork(), wait(), exec()**

Throughout the exercises, we utilized key system calls:
- `fork()`: For creating new processes.
- `wait()`: For making the parent process wait until the child finishes execution.
- `exec()`: For replacing the current process image with a new one.

Understanding and implementing these system calls provided insight into the core mechanisms of process management.

#### 5. **Application of Sleep() for Timing Control**

In exercises involving orphan and zombie processes, we utilized the `sleep()` function to introduce delays in the execution of certain processes. This demonstrated practical control over the timing of process execution.

### Conclusion

These lab exercises have equipped us with practical knowledge and skills in processes management using system calls. The hands-on experience gained through creating, manipulating, and observing processes in various scenarios has deepened our understanding of operating system concepts. This knowledge is crucial for anyone working in fields related to system programming, operating systems, and software development.
