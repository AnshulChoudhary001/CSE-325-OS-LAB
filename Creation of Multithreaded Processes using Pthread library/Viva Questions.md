**Viva Questions and Answers**

1. **Provide two examples in which multithreaded processes provide an advantage over a single-threaded solution.**
   - **Parallel Processing:** Multithreading is beneficial in tasks that can be divided into independent subtasks. For example, in image processing, one thread can handle image loading, another can handle image processing, and a third can handle displaying the result simultaneously, improving overall efficiency.
   - **Responsive User Interface:** In applications with a graphical user interface (GUI), multithreading can be used to keep the user interface responsive while performing time-consuming tasks in the background. This ensures that the application remains interactive even during resource-intensive operations.

2. **What resources are used when a thread is created?**
   - **Thread Control Block (TCB):** Each thread has its own TCB, which contains information about the thread's state, program counter, register set, and other essential information.
   - **Stack:** Threads have their own stack space, which is used for storing local variables and function call information.
   - **Program Counter:** Indicates the address of the next instruction to be executed by the thread.
   - **Registers:** Threads have their own set of registers, including the stack pointer and instruction pointer.

3. **What is the syntax for creating a thread?**
   - The syntax for creating a thread using the Pthread library in C is as follows:
     ```c
     #include <pthread.h>
     
     int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
                         void *(*start_routine)(void *), void *arg);
     ```
     - `pthread_create`: Function to create a new thread.
     - `thread`: Pointer to a variable that will receive the thread identifier.
     - `attr`: Attributes for the thread (usually set to NULL for default attributes).
     - `start_routine`: Function pointer to the function the thread will execute.
     - `arg`: Argument to be passed to the thread function.

4. **What is the use of pthread_join()?**
   - The `pthread_join` function is used to wait for a specific thread to finish its execution before allowing the calling thread to proceed. It is a way to synchronize the execution of threads. The syntax is as follows:
     ```c
     int pthread_join(pthread_t thread, void **retval);
     ```
     - `pthread_join`: Function to wait for the specified thread to terminate.
     - `thread`: Thread identifier of the thread to be joined.
     - `retval`: Pointer to a location where the exit status of the joined thread can be stored.

5. **What is the use of pthread_exit()?**
   - The `pthread_exit` function is used to terminate the calling thread and return a value to the joining thread. It allows a thread to exit and communicate a result to the thread that joins it. The syntax is as follows:
     ```c
     void pthread_exit(void *retval);
     ```
     - `pthread_exit`: Function to terminate the calling thread.
     - `retval`: Value to be returned to the joining thread.

6. **Which pthread function passes the value from the thread function to the main function?**
   - The `pthread_exit` function is used to pass a value from the thread function to the main function or the joining thread. The value passed as an argument to `pthread_exit` can be retrieved by the joining thread using the `pthread_join` function.
