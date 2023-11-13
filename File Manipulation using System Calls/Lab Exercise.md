## Exercise 1: Copying Half the Content of a File Using System Calls

### Program (a): Copying the First Half of the File

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    int sourceFile, targetFile;
    char buffer[4096];
    ssize_t bytesRead, bytesWritten;

    sourceFile = open("source.txt", O_RDONLY);
    targetFile = open("target_first_half.txt", O_CREAT | O_WRONLY, 0666);

    lseek(sourceFile, 0, SEEK_SET); // Move file pointer to the beginning

    bytesRead = read(sourceFile, buffer, sizeof(buffer) / 2);
    bytesWritten = write(targetFile, buffer, bytesRead);

    close(sourceFile);
    close(targetFile);

    return 0;
}
```

### Program (b): Copying the Second Half of the File

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    int sourceFile, targetFile;
    char buffer[4096];
    ssize_t bytesRead, bytesWritten;

    sourceFile = open("source.txt", O_RDONLY);
    targetFile = open("target_second_half.txt", O_CREAT | O_WRONLY, 0666);

    lseek(sourceFile, sizeof(buffer) / 2, SEEK_SET); // Move file pointer to the middle

    bytesRead = read(sourceFile, buffer, sizeof(buffer) / 2);
    bytesWritten = write(targetFile, buffer, bytesRead);

    close(sourceFile);
    close(targetFile);

    return 0;
}
```

## Exercise 2: Reading from Console Until User Enters '$' and Printing to a File

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    int targetFile;
    char input;
    ssize_t bytesRead;

    targetFile = open("console_input.txt", O_CREAT | O_WRONLY, 0666);

    printf("Enter text (terminate with '$'): ");

    while (1) {
        bytesRead = read(0, &input, sizeof(char));
        if (input == '$') {
            break;
        }
        write(targetFile, &input, bytesRead);
    }

    close(targetFile);

    return 0;
}
```

## Exercise 3: Reading File Contents without Using Char Array and Displaying on the Console

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    int sourceFile;
    char character;

    sourceFile = open("file_to_read.txt", O_RDONLY);

    while (read(sourceFile, &character, sizeof(char)) > 0) {
        write(1, &character, sizeof(char)); // Display on the console
    }

    close(sourceFile);

    return 0;
}
```

### Explanation

1. **Copying Half the Content of a File:**
    - **Program (a):** Reads the first half of the source file and writes it to a new file.
    - **Program (b):** Skips the first half of the source file, reads the second half, and writes it to a new file.

2. **Reading from Console Until User Enters '$':**
    - Reads from the console until the user enters '$' and writes the input to a file named "console_input.txt".

3. **Reading File Contents without Using Char Array:**
    - Reads character by character from the source file and displays them on the console without using any char array or built-in functions like `sizeof()` and `strlen()`.

These exercises provide practical experience with file manipulation using system calls in C, including copying file content and reading from the console.
