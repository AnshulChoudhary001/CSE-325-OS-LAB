## Experiment 3: File Manipulation using System Calls

### Aim
The objective of this laboratory is to understand the working behind the `cp` command by using system calls like `open`, `read`, `write`, and `lseek` to copy the contents of one file to another. Additionally, the experiment explores reading user input and writing it to a file.

### Learning Objectives
Students will be able to:
- Understand the working of system calls for file manipulation.
- Gain insights into the implementation of commonly used Linux shell commands.
- Learn about system calls such as `open`, `read`, `write`, `close`, and `lseek`.

### Description of File System Calls

#### System Calls Used:
- **open:** Used to create a file and open it in read/write and append mode.
- **read:** Opens a file in read mode and reads from a file or console.
- **write:** Opens a file in write mode and writes to a file or console.
- **close:** Closes a file.
- **lseek:** Sets the pointer inside the file to a specified position.

#### Syntax of System Calls:
**open System Call:**
```c
int return = open("file name", O_CREAT | O_RDONLY | O_WRONLY, 666);
```

**read/write System Call:**
```c
int return = [read/write] (int fd, char buffer, bytes);
```

**lseek System Call:**
```c
int return = lseek(int fd, int offset, whence);
```

### Sample Programs

#### 1. Program to Create and Open a File using System Calls
```c
#include<stdio.h>
#include<fcntl.h>

int main() {
    int n, m;
    n = open("new_file", O_RDONLY);
    printf("file descriptor is %d \n", n);
    m = open("new_file1", O_CREAT | O_WRONLY, 0777);
    printf("file descriptor is %d \n", m);
}
```

This program demonstrates creating and opening files using the `open` system call.

#### 2. Program to Read from Console and Write to Console
```c
#include<stdio.h>
#include<fcntl.h>

int main() {
    int n, m;
    char buffer[100];
    n = write(1, "Hello World", 11);
    printf("No of bytes written %d \n", n);
    m = read(0, buffer, 12);
    printf("No of bytes read %d \n", m);
}
```

This program reads from the console and writes to the console using the `read` and `write` system calls.

#### 3. Program to Append a File
```c
#include<stdio.h>
#include<fcntl.h>

int main() {
    int a, b, c;
    char buffer[100];
    a = open("new_file2.txt", O_WRONLY | O_APPEND, 0777);
    printf("file descriptor is %d \n", a);
    b = read(0, buffer, 10);
    c = write(a, buffer, b);
    printf("value of b:%d , c: %d", b, c);
}
```

This program appends content to a file using the `open`, `read`, and `write` system calls.

#### 4. Program to Read and Write from and to a File
```c
#include<stdio.h>
#include<fcntl.h>

int main() {
    int a, b, c;
    char buffer[100];
    a = open("new_file2", O_CREAT | O_WRONLY, 0777);
    printf("file descriptor is %d \n", a);
    b = read(0, buffer, 10);
    c = write(a, buffer, b);
    printf("the value of b: %d , c:%d \n", b, c);
    return 0;
}
```

This program reads from the console and writes to a file using the `read` and `write` system calls.

### Explanation

- **Open System Call:** Used to create and open files with specific modes.
- **Read/Write System Calls:** Used to read from/write to files or consoles.
- **Lseek System Call:** Sets the pointer inside a file to a specific position.

These programs provide practical insights into the implementation of file manipulation commands and the underlying system calls. They demonstrate the versatility of system calls in handling various file operations.
