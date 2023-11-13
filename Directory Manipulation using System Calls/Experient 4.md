## Experiment 4: Directory Manipulation using System Calls

### Aim
The aim of this laboratory is to explore the working of directory system calls, focusing on the commands `mkdir` and `ls`. These commands utilize system calls like `mkdir`, `opendir`, `readdir`, and `rmdir`. The objective is to gain insights into the operations performed by these commands in the Linux shell.

### Learning Objectives
Students will be able to:
- Understand the working of directory system calls.
- Gain practical knowledge behind commonly used Linux shell commands (`mkdir` and `ls`).
- Learn about key directory system calls, including `mkdir`, `opendir`, `readdir`, and `rmdir`.

### Theory

#### System Calls Used:
- **mkdir:** Used to create directories with a specified permission mode.
- **opendir:** Opens a directory stream, returning a pointer to the directory stream.
- **readdir:** Returns a pointer to the next directory entry.
- **rmdir:** Removes a directory (only if empty).

#### Syntax for Directory System Calls:
**mkdir System Call:**
```c
int mkdir("pathname/dirname", mode_t mode);
int return = mkdir("directory name", 0666);
```

**opendir System Call:**
```c
DIR *opendir("dir name");
```

**readdir System Call:**
```c
struct dirent *readdir(DIR *dirname);
```

**rmdir System Call:**
```c
int rmdir("pathname/dirname");
```

**Dirent Structure:**
```c
struct dirent {
    ino_t d_ino;            // inode number
    off_t d_off;            // offset to the next dirent
    unsigned short d_reclen;// length of this record
    unsigned char d_type;   // type of file (not supported by all file system types)
    char d_name[256];       // filename
};
```

### Program: Print Contents of a Directory

```c
#include<stdio.h>
#include<dirent.h>

int main() {
    DIR *dp;
    struct dirent *dptr;
    int b = mkdir("Dir1", 0777);
    dp = opendir("Dir1");

    while (NULL != (dptr = readdir(dp))) {
        printf("%s \n", dptr->d_name);
        printf("%d \n", dptr->d_type);
    }

    return 0;
}
```

### Explanation

This program uses directory system calls to create a directory named "Dir1" using `mkdir` and then opens it using `opendir`. It reads and prints the contents of the directory using `readdir`. The program displays the names of the entries and their corresponding types. This example provides practical insights into the working of directory system calls.
