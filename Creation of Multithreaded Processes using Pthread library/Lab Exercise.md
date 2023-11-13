**README**

## Lab Exercises: Creation of Multithreaded Processes using Pthread Library

### Exercise 1: Concatenating Strings using Pthread

```c
#include <stdio.h>
#include <pthread.h>
#include <string.h>

#define MAX_SIZE 100

// Structure to hold multiple strings
struct StringArray {
    char strings[MAX_SIZE][MAX_SIZE];
    int count;
};

// Thread function to concatenate strings
void *concatenate_strings(void *arg) {
    struct StringArray *str_array = (struct StringArray *)arg;
    char result[MAX_SIZE * MAX_SIZE];
    result[0] = '\0';

    for (int i = 0; i < str_array->count; i++) {
        strcat(result, str_array->strings[i]);
    }

    printf("Concatenated String: %s\n", result);

    pthread_exit(NULL);
}

int main() {
    pthread_t concat_thread;

    struct StringArray str_array;
    str_array.count = 3;
    strcpy(str_array.strings[0], "Hello, ");
    strcpy(str_array.strings[1], "Multithreading ");
    strcpy(str_array.strings[2], "World!");

    pthread_create(&concat_thread, NULL, concatenate_strings, (void *)&str_array);
    pthread_join(concat_thread, NULL);

    return 0;
}
```

### Exercise 2: Finding the Length of Strings using Pthread

```c
#include <stdio.h>
#include <pthread.h>
#include <string.h>

#define MAX_SIZE 100

// Structure to hold multiple strings
struct StringArray {
    char strings[MAX_SIZE][MAX_SIZE];
    int count;
};

// Thread function to find the length of strings
void *find_string_length(void *arg) {
    struct StringArray *str_array = (struct StringArray *)arg;

    for (int i = 0; i < str_array->count; i++) {
        printf("Length of \"%s\": %lu\n", str_array->strings[i], strlen(str_array->strings[i]));
    }

    pthread_exit(NULL);
}

int main() {
    pthread_t length_thread;

    struct StringArray str_array;
    str_array.count = 3;
    strcpy(str_array.strings[0], "Hello");
    strcpy(str_array.strings[1], "Multithreading");
    strcpy(str_array.strings[2], "World!");

    pthread_create(&length_thread, NULL, find_string_length, (void *)&str_array);
    pthread_join(length_thread, NULL);

    return 0;
}
```

### Exercise 3: Statistical Operations on Numbers using Pthread

```c
#include <stdio.h>
#include <pthread.h>

#define MAX_SIZE 100

// Structure to hold multiple numbers
struct NumberArray {
    int numbers[MAX_SIZE];
    int count;
    double average;
    int max;
    int min;
};

// Thread function to calculate average
void *calculate_average(void *arg) {
    struct NumberArray *num_array = (struct NumberArray *)arg;
    double sum = 0;

    for (int i = 0; i < num_array->count; i++) {
        sum += num_array->numbers[i];
    }

    num_array->average = sum / num_array->count;

    pthread_exit(NULL);
}

// Thread function to find maximum and minimum
void *find_max_min(void *arg) {
    struct NumberArray *num_array = (struct NumberArray *)arg;
    num_array->max = num_array->numbers[0];
    num_array->min = num_array->numbers[0];

    for (int i = 1; i < num_array->count; i++) {
        if (num_array->numbers[i] > num_array->max) {
            num_array->max = num_array->numbers[i];
        }

        if (num_array->numbers[i] < num_array->min) {
            num_array->min = num_array->numbers[i];
        }
    }

    pthread_exit(NULL);
}

int main() {
    pthread_t average_thread, max_min_thread;

    struct NumberArray num_array;
    num_array.count = 5;
    num_array.numbers[0] = 10;
    num_array.numbers[1] = 5;
    num_array.numbers[2] = 8;
    num_array.numbers[3] = 15;
    num_array.numbers[4] = 3;

    pthread_create(&average_thread, NULL, calculate_average, (void *)&num_array);
    pthread_create(&max_min_thread, NULL, find_max_min, (void *)&num_array);

    pthread_join(average_thread, NULL);
    pthread_join(max_min_thread, NULL);

    printf("Average: %.2f\n", num_array.average);
    printf("Maximum: %d\n", num_array.max);
    printf("Minimum: %d\n", num_array.min);

    return 0;
}
```

### Exercise 4: Sorting and Merging Arrays using Pthread

```c
#include <stdio.h>
#include <pthread.h>
#include <stdlib.h>

#define MAX_SIZE 10

// Structure to hold multiple numbers
struct NumberArray {
    int numbers[MAX_SIZE];
    int count;
};

// Thread function to sort an array
void *sort_array(void *arg) {
    struct NumberArray *num_array = (struct NumberArray *)arg;
    int n = num_array->count;

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (num_array->numbers[j] > num_array->numbers[j + 1]) {
                // swap
                int temp = num_array->numbers[j];
                num_array->numbers[j] = num_array->numbers[j + 1];
                num_array->numbers[j + 1] = temp;
            }
        }
    }

    pthread_exit(NULL);
}

// Thread function to merge two sorted arrays
void *merge_arrays(void *arg) {
    struct NumberArray *num_array = (struct NumberArray *)arg;
    int mid = num_array->count / 2;
    int i = 0, j = mid, k = 0;
    int temp[MAX_SIZE];

    while (i < mid && j < num_array->count) {
        if (num_array->numbers[i] < num_array->numbers[j]) {
            temp[k++] = num_array->numbers[i++];
        } else {
            temp[k++] = num_array->numbers[j++];
        }
    }

    while (i < mid) {
        temp[k++] = num_array->numbers[i++];
    }

    while (j < num_array->count) {
        temp[k++] = num_array->numbers[j++];
    }

    for (i = 0; i < num_array->count; i++) {
        num_array->numbers[i] = temp[i];
    }

    pthread_exit(NULL);
}

int main() {
    pthread_t sort_thread1, sort_thread2, merge_thread;

    struct NumberArray num_array;
    num_array.count = 8;
    num_array.numbers[0] = 10;
    num_array.numbers[1] = 

5;
    num_array.numbers[2] = 8;
    num_array.numbers[3] = 15;
    num_array.numbers[4] = 3;
    num_array.numbers[5] = 12;
    num_array.numbers[6] = 7;
    num_array.numbers[7] = 1;

    pthread_create(&sort_thread1, NULL, sort_array, (void *)&num_array);
    pthread_create(&sort_thread2, NULL, sort_array, (void *)&num_array);

    pthread_join(sort_thread1, NULL);
    pthread_join(sort_thread2, NULL);

    pthread_create(&merge_thread, NULL, merge_arrays, (void *)&num_array);
    pthread_join(merge_thread, NULL);

    printf("Sorted and Merged Array: ");
    for (int i = 0; i < num_array.count; i++) {
        printf("%d ", num_array.numbers[i]);
    }

    return 0;
}
```

### Explanation

- **Exercise 1:** Concatenates multiple strings passed to a thread function.

- **Exercise 2:** Finds the length of strings passed to a thread function.

- **Exercise 3:** Performs statistical operations on a set of numbers using multiple threads. Calculates the average, maximum, and minimum.

- **Exercise 4:** Sorts and merges two halves of an array using multiple threads. The final sorted array is printed by the main thread.
