**README**

## Experiment 6: Creation of Multithreaded Processes using Pthread Library

### Aim
The aim of this laboratory is to introduce operations on threads using the Pthread library. This includes thread initialization, creation, join, and exit functions.

### Learning Objectives
Students will be able to:
- Understand the concept of threads.
- Gain practical knowledge of thread operations using the Pthread library.

### Theory

#### Thread Functions:
- **pthread_init():** Initializes a thread.
- **pthread_create():** Creates a thread.
- **pthread_exit():** Exits a thread function with a return value.
- **pthread_join():** Joins a thread in the main function and retrieves the value returned by the thread function.

#### Syntax for `pthread_create()`:
```c
int a = pthread_create(pthread_t *thread, pthread_attr_t *attr, void *(*start_routine), void*);
```

### Outline of Programs

#### Program 1: Create a thread with NULL attributes

```c
#include<stdio.h>
#include<pthread.h>

char *a;

void *func() {
    printf("In thread function\n");
    pthread_exit("Exit thread function\n");
}

int main() {
    pthread_t thread1;
    void *a;

    printf("In main thread\n");

    pthread_create(&thread1, NULL, func, NULL);
    pthread_join(thread1, &a);

    printf("%s\n", (char *)a);

    return 0;
}
```

#### Program 2: Pass a message from the main function to threads

```c
#include<pthread.h>
#include<stdlib.h>

void *myfunc(void *myvar);

int main(int argc, char *argv[]) {
    pthread_t thread1, thread2;
    char *msg1 = "first thread";
    char *msg2 = "second thread";
    int ret1, ret2;

    ret1 = pthread_create(&thread1, NULL, myfunc, (void *)msg1);
    ret2 = pthread_create(&thread2, NULL, myfunc, (void *)msg2);

    printf("Main function after pthread_create\n");

    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    printf("first thread ret1= %d\n", ret1);
    printf("first thread ret1= %d\n", ret1);

    return 0;
}

void *myfunc(void *myvar) {
    char *msg;
    msg = (char *)myvar;
    int i;

    for (i = 0; i < 10; i++) {
        printf("%s %d\n", msg, i);
        sleep(2);
    }

    return NULL;
}
```

#### Program 3: Return a value from the thread function to the main function

```c
#include <stdio.h>
#include <pthread.h>

int *a;

struct arg_struct {
    int arg1;
    int arg2;
    int arg3;
};

void *print_the_arguments(void *arg) {
    struct arg_struct *ar = (struct arg_struct *)arg;

    scanf("%d", &ar->arg3);
    scanf("%d", &ar->arg2);

    int c = ar->arg2 + ar->arg3;
    pthread_exit((void *)c);
}

int main() {
    pthread_t some_thread;
    struct arg_struct args;
    args.arg1 = 5;
    args.arg2 = 7;
    void *a;

    pthread_create(&some_thread, NULL, &print_the_arguments, &args);
    pthread_join(some_thread, &a);

    printf("%d\n", (int)a);

    return 0;
}
```

### Explanation

- **Program 1:** Creates a thread with NULL attributes. The main function creates a thread using `pthread_create` and waits for it to finish using `pthread_join`. The thread function prints a message and exits.

- **Program 2:** Passes messages from the main function to two threads. The threads print messages ten times with a sleep interval of 2 seconds.

- **Program 3:** Returns a value from the thread function to the main function. The main function creates a thread using `pthread_create` and retrieves the value using `pthread_join`. The thread function takes two integer inputs, adds them, and exits with the sum.
