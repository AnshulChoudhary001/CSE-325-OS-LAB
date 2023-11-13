**Viva Questions and Answers**

### 1. What is the difference between orphan and zombie processes?

**Answer:**
- **Orphan Process:** An orphan process is a child process whose parent process has terminated. Orphan processes continue to execute in the system, and they are adopted by the init process (process ID 1).
  
- **Zombie Process:** A zombie process is a child process that has completed its execution but still has an entry in the process table. The process entry remains until the parent acknowledges the child's termination using the `wait()` system call.

### 2. How many child processes will be created if three consecutive fork statements are used in a main function?

**Answer:**
If three consecutive `fork()` statements are used, the total number of child processes created will be 2^3 - 1 = 7. This is because each `fork()` call creates a new process, and with three calls, it results in 2^n - 1 child processes.

### 3. In case of `p = fork()`, which process will be executed if `p > 0`?

**Answer:**
If `p = fork()` and `p > 0`, the parent process will be executed. The value returned by `fork()` to the parent process is the process ID (PID) of the child, and since `p > 0`, it means the process is the parent.

### 4. In case of `p = fork()`, which process will be executed if `p < 0`?

**Answer:**
If `p = fork()` and `p < 0`, it indicates an error in process creation. The parent process will continue its execution, and no child process will be created.

### 5. Which system call causes the parent process to stop until the child completes the execution?

**Answer:**
The `wait()` system call causes the parent process to stop its execution until the child process completes its execution. It allows the parent to wait for the termination of a specific child process or any child process.

### 6. What is the function of an `execl` system call?

**Answer:**
The `execl` system call is used to replace the current process image with a new one. It loads and executes a new program, effectively ending the current process and starting a new one. The new program is specified by providing its path and arguments to `execl`.

### Additional Viva Questions:

### 7. What is the purpose of the `sleep()` function in the context of processes?

**Answer:**
The `sleep()` function is used to introduce a delay in the execution of a program. In the context of processes, it can be employed to simulate timing scenarios, control the sequence of process execution, and demonstrate behaviors like orphan and zombie processes.

### 8. How does a child process become an orphan process?

**Answer:**
A child process becomes an orphan process when its parent process terminates before the child completes its execution. Orphan processes are then adopted by the init process.

### 9. Explain the role of the `exit()` function in a process.

**Answer:**
The `exit()` function is used to terminate a process. When a process calls `exit()`, it immediately stops execution, and the exit status is returned to the operating system. In the context of zombie processes, calling `exit()` in the child process allows the entry in the process table to be cleared.

### 10. How can a parent process wait for a specific child process to complete using the `waitpid()` system call?

**Answer:**
The `waitpid()` system call is used to wait for the termination of a specific child process. By specifying the process ID (PID) of the child and additional options, the parent can control which child it waits for and retrieve information about the terminated child.

### Conclusion:

These viva questions cover various aspects of processes management using system calls, providing a comprehensive understanding of process creation, termination, and control in a Unix-like environment.
