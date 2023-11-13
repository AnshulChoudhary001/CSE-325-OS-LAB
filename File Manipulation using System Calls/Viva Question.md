**Viva Questions and Answers**

1. **Which system call is used to reposition the pointer in the file?**

   **Answer:** The system call used to reposition the pointer in the file is `lseek()`.

2. **What is the return value of the read system call?**

   **Answer:** The return value of the `read` system call is the number of bytes read. If the return value is 0, it indicates the end of the file.

3. **What is the return value of the open system call?**

   **Answer:** The return value of the `open` system call is a file descriptor. If the call is unsuccessful, it returns -1.

4. **What is passed as the first argument of the read/write system call?**

   **Answer:** The first argument of the `read/write` system call is the file descriptor (`int fd`), which represents the opened file.

5. **If a file is to be appended, in which mode will it be opened using the open system call?**

   **Answer:** If a file is to be appended, it will be opened in append mode using the `O_APPEND` flag in the open system call.

6. **What will be used in the lseek system call if the file is to be appended?**

   **Answer:** In the `lseek` system call, the offset parameter is set to 0, and the whence parameter is set to `SEEK_END` to position the pointer at the end of the file, facilitating appending.

7. **What is the return value of the lseek system call?**

   **Answer:** The return value of the `lseek` system call is the new offset position in the file, measured in bytes from the beginning of the file.

8. **Which system call can be used to find the size of a file?**

   **Answer:** The `lseek` system call, along with `SEEK_END` and an offset of 0, can be used to find the size of a file.

9. **How can we find the size of a file using the lseek system call?**

   **Answer:** To find the size of a file using `lseek`, set the offset parameter to 0, and the whence parameter to `SEEK_END`. The return value will be the size of the file in bytes.
