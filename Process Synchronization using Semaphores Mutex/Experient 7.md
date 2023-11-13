# Process Synchronization using Semaphores/Mutex

## Aim
The objective of this laboratory is to introduce the concept of synchronization using pthread library. Students will learn the concepts of mutex and semaphores, and apply them to solve classical problems of process synchronization.

## Learning Objective
After completing this laboratory, students will be able to:
- Understand the concept of mutex and semaphores using pthread library.
- Simulate and solve classical problems of process synchronization.

## Theory
This section provides the syntax of mutex and semaphore functions. For more information, refer to the manual page or help in the Linux shell.
- **pthread_mutex_t:**
  - To initialize a mutex variable.
- **pthread_mutex_lock():**
  - To apply a lock using a mutex variable.
- **pthread_mutex_unlock():**
  - To release the lock using a mutex variable.
- **sem_t:**
  - To declare a semaphore variable.
- **sem_init():**
  - To initialize a semaphore variable, which takes three parameters:
    - Semaphore variable
    - Number of processes sharing the semaphore variable
    - Maximum value of the semaphore variable
- **sem_wait():**
  - To decrement the value of the semaphore variable by 1. It also blocks other processes.
- **sem_post():**
  - To increment the value of the semaphore variable by 1. It also sends a signal to wake up the blocked process.

## Outline of the Programs

### 1. Program to Simulate a Race Condition
```c
#include<stdio.h>
#include<pthread.h>

int shared = 5;

void *func1() {
    // Critical section
    int local = shared;
    local = local + 1;
    sleep(5); // Causes a context switch
    shared = local;
    // Critical section
    printf("shared in func1: %d \n", shared);
    pthread_exit(NULL);
}

void *func2() {
    // Critical section
    int local = shared;
    local = local - 1;
    shared = local;
    // Critical section
    printf("shared in func2: %d \n", shared);
    pthread_exit(NULL);
}

int main() {
    pthread_t t1, t2;
    pthread_create(&t1, NULL, func1, NULL);
    pthread_create(&t2, NULL, func2, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
}
```

### 2. Program to Remove Race Condition using Mutex
```c
#include<stdio.h>
#include<pthread.h>

int shared = 5;
pthread_mutex_t l; // Mutex variable l

void *func1() {
    // Critical section
    pthread_mutex_lock(&l); // Applying lock using l (initially false)
    int local = shared;
    local = local + 1;
    sleep(5); // Causes a context switch
    shared = local;
    pthread_mutex_unlock(&l); // Releasing lock using l
    // Critical section
    printf("shared in func1: %d \n", shared);
    pthread_exit(NULL);
}

void *func2() {
    // Critical section
    pthread_mutex_lock(&l); // If acquired by func1 l will return true
    int local = shared;
    local = local - 1;
    shared = local;
    pthread_mutex_unlock(&l); // Releasing lock using l
    // Critical section
    printf("shared in func2: %d \n", shared);
    pthread_exit(NULL);
}

int main() {
    pthread_t t1, t2;
    pthread_create(&t1, NULL, func1, NULL);
    pthread_create(&t2, NULL, func2, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
}
```

### 3. Program to Remove Race Condition using Semaphores
```c
#include<stdio.h>
#include<pthread.h>

int shared = 5;
sem_t s; // Semaphore variable s

void *func1() {
    // Critical section
    sem_wait(&s); // Applying lock using s (initially false)
    int local = shared;
    local = local + 1;
    sleep(5); // Causes a context switch
    shared = local;
    sem_post(&s); // Releasing lock using s
    // Critical section
    printf("shared in func1: %d \n", shared);
    pthread_exit(NULL);
}

void *func2() {
    // Critical section
    sem_wait(&s); // If acquired by func1 s will return true
    int local = shared;
    local = local - 1;
    shared = local;
    sem_post(&s); // Releasing lock using s
    // Critical section
    printf("shared in func2: %d \n", shared);
    pthread_exit(NULL);
}

int main() {
    pthread_t t1, t2;
    sem_init(&s, 0, 1); // Initializing semaphore
    pthread_create(&t1, NULL, func1, NULL);
    pthread_create(&t2, NULL, func2, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
}
```

## Usage
- Compile each program using a C compiler (e.g., `gcc -pthread program.c -o program`).
- Run the compiled executable (e.g., `./program`).

## Notes
- Each program illustrates a different approach to solving the race condition problem using either no synchronization, mutex, or semaphores.
- Pay attention to the critical sections in the code where shared resources are accessed to avoid race conditions.
- Experiment with the code and understand the impact of synchronization techniques on the outcome of the programs.
