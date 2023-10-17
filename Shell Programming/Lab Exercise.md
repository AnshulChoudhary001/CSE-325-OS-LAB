### Exercise 1: Multiplication Table

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

### Exercise 2: Small Calculator

**Script (`calculator.sh`):**
```bash
#!/bin/bash

echo "Enter first number: "
read num1
echo "Enter second number: "
read num2

echo "Select operation:"
echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"
read choice

case $choice in
    1) result=$((num1 + num2));;
    2) result=$((num1 - num2));;
    3) result=$((num1 * num2));;
    4) result=$(awk "BEGIN {print $num1 / $num2}");;
    *) echo "Invalid choice"; exit 1;;
esac

echo "Result: $result"
```

**Explanation:**
This script implements a small calculator that performs addition, subtraction, multiplication, and division based on user input and choice.

### Exercise 3: Prime Numbers up to Given Limit

**Script (`prime_numbers.sh`):**
```bash
#!/bin/bash

echo "Enter the limit: "
read limit

echo "Prime numbers up to $limit are:"

for ((num = 2; num <= limit; num++)); do
    is_prime=1
    for ((i = 2; i <= num / 2; i++)); do
        if [ $((num % i)) -eq 0 ]; then
            is_prime=0
            break
        fi
    done

    if [ $is_prime -eq 1 ]; then
        echo $num
    fi
done
```

**Explanation:**
This script takes a limit as input and prints all prime numbers up to that limit using a `for` loop and checking for divisibility. Prime numbers are numbers greater than 1 that have no positive divisors other than 1 and themselves.
