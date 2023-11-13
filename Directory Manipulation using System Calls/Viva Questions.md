**Viva Questions and Answers: Directory Manipulation using System Calls**

1. **What is the purpose of the `mkdir` system call?**

   **Answer:** The `mkdir` system call is used to create directories. It takes a pathname and a permission mode as arguments and creates a new directory with the specified name and permissions.

2. **How do you open a directory stream in C using system calls?**

   **Answer:** The `opendir` system call is used to open a directory stream. It takes the directory name as an argument and returns a pointer to the directory stream (type: `DIR*`).

3. **Explain the use of the `readdir` system call.**

   **Answer:** The `readdir` system call is used to read the next entry from a directory stream. It takes a pointer to a directory stream (`DIR*`) as an argument and returns a pointer to a structure of type `struct dirent`, representing the next directory entry.

4. **What does the `rmdir` system call do, and under what condition can it remove a directory?**

   **Answer:** The `rmdir` system call is used to remove an empty directory. It takes the pathname of the directory as an argument. It can remove a directory only if it is empty; otherwise, an error occurs.

5. **Explain the structure of `struct dirent` used by the `readdir` system call.**

   **Answer:** The `struct dirent` structure represents a directory entry and typically has the following fields:
   - `ino_t d_ino`: Inode number.
   - `off_t d_off`: Offset to the next directory entry.
   - `unsigned short d_reclen`: Length of this record.
   - `unsigned char d_type`: Type of file (not supported by all file system types).
   - `char d_name[256]`: Filename.

6. **How can you create a directory and a file inside that directory using system calls?**

   **Answer:** You can use the `mkdir` system call to create a directory and the `creat` or `open` system call to create a file inside that directory. Ensure that you set the appropriate permissions and handle errors.

7. **Explain the steps to copy the contents of one directory to another using system calls.**

   **Answer:** To copy contents between directories, you can use a combination of directory and file manipulation system calls. Iterate through the source directory using `readdir`, create corresponding entries in the destination directory using `link` or `copy`, and handle errors appropriately.

8. **What is the significance of changing the working directory using the `chdir` system call?**

   **Answer:** The `chdir` system call changes the current working directory of the process. This is significant when working with relative paths. It allows you to navigate and perform operations in a specific directory without specifying the full path in subsequent system calls.

9. **How can you handle errors in directory and file manipulation operations?**

   **Answer:** Check the return values of system calls for errors. Most system calls return `-1` on failure, and you can use `errno` to obtain more information about the specific error. Implement proper error handling to ensure the robustness of your programs.

10. **What is the real-world relevance of directory manipulation system calls in system programming?**

    **Answer:** Directory manipulation system calls are crucial in system programming for tasks like creating, navigating, and managing directories. They are the foundation of commands like `mkdir` and `ls` and are essential for file organization and management in various applications. Understanding these calls is fundamental to system-level programming.
