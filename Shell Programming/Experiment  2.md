# Shell Scripting Basics 

## Introduction
Welcome to the Shell Scripting Basics laboratory! This laboratory is designed to provide a comprehensive understanding of shell scripting, enabling students to harness the power of shell commands and automate tasks efficiently. Throughout this course, students will learn the fundamental concepts of shell programming, including variables, input/output redirection, arithmetic operations, flow control structures, and loops. By the end of this laboratory, students will have gained practical skills in writing shell scripts for various tasks.

## Lab Objectives
The Shell Scripting Basics laboratory aims to achieve the following objectives:

### Shell Script Fundamentals
- **Objective:** Understand the basics of shell scripting, including the creation of shell script files, setting execute permissions, and executing scripts using `sh` or `bash` commands.

### Shell Variables
- **Objective:** Learn to use variables in shell scripts to store and manipulate data.

### Input/Output Redirection
- **Objective:** Explore standard input and output redirection techniques, enabling efficient data flow between scripts, files, and command-line utilities.

### Shell Arithmetic
- **Objective:** Perform arithmetic operations in shell scripts using `let` and `expr` commands, enabling mathematical computations within scripts.

### Flow Control Structures
- **Objective:** Master flow control structures such as `if`, `if-then-else`, `if-then-elif-then-else`, and `case` statements for decision-making in scripts.

### Loops
- **Objective:** Understand `while` and `for` loops, enabling repetitive execution of commands for specified conditions or items in a list.

## Detailed Concepts

### Shell Variables
In shell scripting, variables are placeholders for storing data. They are created using the format `variable_name=value`. For example:
```bash
day="Sunday"
```
Here, the variable `day` is assigned the value `"Sunday"`.

### Input/Output Redirection
- **Standard Input Redirection (`<`):** Redirects input from files to commands. For example:
```bash
wc < test.txt
```
- **Standard Output Redirection (`>`):** Redirects command output to files. For example:
```bash
ls > test.txt
```

### Shell Arithmetic
Arithmetic expressions in shell scripts can be evaluated using `let` or `expr` commands. For example:
```bash
x=2
y=3
let "sum = x + y"
echo "Sum is $sum"
```

### Flow Control Structures
#### `if`, `if-then`, `if-then-else`, `if-then-elif-then-else`:
```bash
if [ condition ]
then
  # commands
elif [ condition ]
then
  # commands
else
  # commands
fi
```

#### `case` Statement:
```bash
case <test-value> in
  value1)
    # commands
    ;;
  value2)
    # commands
    ;;
  *)
    # Default statements
    ;;
esac
```

### Loops
#### `while` Loop:
```bash
num=0
while [ $num -lt 10 ]
do
  echo $num
  num=`expr $num + 1`
done
```

#### `for` Loop:
```bash
list="one two three four five"
num=1
for i in $list
do
  echo $num
  num=`expr $num + 1`
done
```

## Sample Program Explanation
The following sample program demonstrates the use of the `case` statement to select a number:
```bash
num="one"
case "$num" in
  "one") echo "Number is 1." ;;
  "two") echo "Number is 2." ;;
  "three") echo "Number is 3." ;;
  *) echo "No Number." ;;
esac
```

In this program, the variable `num` is compared against various values using the `case` statement, and corresponding messages are displayed based on the match.

## Conclusion
The Shell Scripting Basics laboratory equips students with essential skills in shell scripting, enabling them to automate tasks, process data, and make decisions in a Unix/Linux environment. By understanding variables, input/output redirection, arithmetic operations, flow control structures, and loops, students are well-prepared to create efficient and robust shell scripts for a variety of applications. 


#Some Exercises:

### Exercise 1: Variable Usage

**Script (`greet.sh`):**
```bash
#!/bin/bash

echo "Enter your name: "
read name
echo "Hello, $name! Welcome to the shell scripting world."
```

**Explanation:**
This script takes user input, stores it in the `name` variable, and then prints a greeting message using the stored value.

### Exercise 2: Input/Output Redirection

**Script (`file_stats.sh`):**
```bash
#!/bin/bash

echo "Enter the filename: "
read filename

lines=$(wc -l < "$filename")
words=$(wc -w < "$filename")
chars=$(wc -c < "$filename")

echo "Number of lines: $lines"
echo "Number of words: $words"
echo "Number of characters: $chars" > file_stats.txt
```

**Explanation:**
This script takes a filename as input, counts the lines, words, and characters, and then redirects the output to a file named "file_stats.txt".

### Exercise 3: Arithmetic Operations

**Script (`rectangle_area.sh`):**
```bash
#!/bin/bash

echo "Enter length: "
read length
echo "Enter width: "
read width

area=$((length * width))

echo "Area of the rectangle is: $area"
```

**Explanation:**
This script takes user input for length and width, calculates the area, and then prints the result.

### Exercise 4: Flow Control Structures

**Script (`odd_even.sh`):**
```bash
#!/bin/bash

echo "Enter a number: "
read number

if [ $((number % 2)) -eq 0 ]; then
    echo "$number is even."
else
    echo "$number is odd."
fi
```

**Explanation:**
This script checks if the entered number is even or odd and prints the appropriate message.

### Exercise 5: Loops

**Script (`even_numbers.sh`):**
```bash
#!/bin/bash

num=2
count=1

while [ $count -le 10 ]; do
    echo $num
    num=$((num + 2))
    count=$((count + 1))
done
```

**Explanation:**
This script uses a `while` loop to print the first 10 even numbers.

### Exercise 6: Case Statement

**Script (`schedule.sh`):**
```bash
#!/bin/bash

echo "Enter the day of the week: "
read day

case "$day" in
    "Monday") echo "Math class at 9 AM, History class at 11 AM" ;;
    "Tuesday") echo "Physics class at 10 AM, Chemistry class at 1 PM" ;;
    "Wednesday") echo "English class at 9 AM, Biology class at 11 AM" ;;
    "Thursday") echo "Computer Science class at 2 PM" ;;
    "Friday") echo "No classes today, enjoy your weekend!" ;;
    *) echo "Invalid day" ;;
esac
```

**Explanation:**
This script uses a `case` statement to provide a schedule based on the user's input for the day of the week.

### Exercise 7: Combining Concepts

**Script (`multiplication_table.sh`):**
```bash
#!/bin/bash

echo "Enter a number: "
read number

count=1

while [ $count -le 10 ]; do
    result=$((number * count))
    echo "$number x $count = $result"
    count=$((count + 1))
done
```

**Explanation:**
This script takes a number as input and prints its multiplication table from 1 to 10 using a `while` loop.

### Exercise 8: Advanced Scripting

**Script (`average_calculator.sh`):**
```bash
#!/bin/bash

sum=0
count=0

while read number; do
    if [[ $number =~ ^[0-9]+$ ]]; then
        sum=$((sum + number))
        count=$((count + 1))
    fi
done < input_numbers.txt

if [ $count -eq 0 ]; then
    echo "No valid numbers found in the file."
else
    average=$((sum / count))
    echo "Average of the numbers: $average"
fi
```

**Explanation:**
This script reads numbers from a file (`input_numbers.txt`), calculates their sum and average, and then prints the average. It handles non-numeric values in the file gracefully.
