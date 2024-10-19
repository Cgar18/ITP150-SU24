### MIDTERM

### Problem 1: Sum of Prime Numbers (10 points)

#### Problem:
Write a Python program to find the sum of all prime numbers less than a given number `n`.

#### Rubric:
- Correctly identifying prime numbers (4 points)
- Proper use of for/while loop (3 points)
- Correct calculation and return of the sum (3 points)

#### Sample Input:
```
Enter a number: 10
```

#### Sample Output:
```
Sum of primes less than 10 is: 17
```


def is_prime(num):
    """Check if a number is prime."""
    if num <= 1:
        return False
    for i in range(2, int(num**0.5) + 1):
        if num % i == 0:
            return False
    return True

def sum_of_primes(n):
    """Calculate the sum of all prime numbers less than n."""
    total = 0
    for i in range(2, n):
        if is_prime(i):
            total += i
    return total

# Input from the user
try:
    n = int(input("Enter a number: "))
    if n <= 1:
        print("Please enter a number greater than 1.")
    else:
        result = sum_of_primes(n)
        print(f"Sum of primes less than {n} is: {result}")
except ValueError:
    print("Invalid input! Please enter a valid integer.")







### Problem 2: Palindrome Checker (10 points)

#### Problem:
Write a Python program to check if a given string is a palindrome (reads the same forwards and backwards).

#### Rubric:
- Correctly identifying a palindrome using string slicing (4 points)
- Proper use of if-elif-else condition (3 points)
- Correct input and output handling (3 points)

#### Sample Input:
```
Enter a string: racecar
```

#### Sample Output:
```
racecar is a palindrome.
```

#### Another Sample Input:
```
Enter a string: hello
```

#### Sample Output:
```
hello is not a palindrome.
```

def is_palindrome(s):
    """Check if the string is a palindrome using slicing."""
    return s == s[::-1]

# Input from the user
input_string = input("Enter a string: ").strip()

# Check for palindrome
if is_palindrome(input_string):
    print(f"{input_string} is a palindrome.")
else:
    print(f"{input_string} is not a palindrome.")



### Problem 3: FizzBuzz with String Output (10 points)

#### Problem:
Write a Python program that prints the numbers from 1 to 100. But for multiples of three, print "Fizz" instead of the number and for the multiples of five, print "Buzz". For numbers which are multiples of both three and five, print "FizzBuzz".

#### Rubric:
- Correctly implementing FizzBuzz logic (4 points)
- Proper use of for loop (3 points)
- Correct output formatting (3 points)

#### Sample Input:
```
(Program runs without user input, printing numbers from 1 to 100 with "Fizz", "Buzz", and "FizzBuzz" replacements)
```

#### Sample Output (First few lines):
```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
...
```

# FizzBuzz Program
for i in range(1, 101):
    if i % 3 == 0 and i % 5 == 0:
        print("FizzBuzz")
    elif i % 3 == 0:
        print("Fizz")
    elif i % 5 == 0:
        print("Buzz")
    else:
        print(i)



### Problem 4: String Compression (15 points)

#### Problem:
Write a Python program to compress a string using the counts of repeated characters. For example, the string "aabcccccaaa" should become "a2b1c5a3". If the compressed string is not smaller than the original string, return the original string.

#### Rubric:
- Correctly counting consecutive characters (4 points)
- Proper use of for loop and if-elif-else condition (3 points)
- Correct return of compressed or original string (3 points)

#### Sample Input:
```
Enter a string: aabcccccaaa
```

#### Sample Output:
```
Compressed string: a2b1c5a3
```

#### Another Sample Input:
```
Enter a string: abc
```

#### Sample Output:
```
Compressed string: abc
```
def compress_string(s):
    """Compress the string using counts of repeated characters."""
    if not s:  # Handle empty string
        return s
    
    compressed = []
    count = 1

    for i in range(1, len(s)):
        if s[i] == s[i - 1]:
            count += 1
        else:
            compressed.append(s[i - 1] + str(count))
            count = 1
    
    # Add the last character and its count
    compressed.append(s[-1] + str(count))
    
    compressed_string = ''.join(compressed)

    # Return the original string if compressed is not smaller
    return compressed_string if len(compressed_string) < len(s) else s

# Input from the user
input_string = input("Enter a string: ")
result = compress_string(input_string)
print(f"Compressed string: {result}")


### Problem 5: Evaluate a Mathematical Expression (15 points)

#### Problem:
Write a Python program to evaluate a given mathematical expression provided as a string. The program should handle addition, subtraction, multiplication, and division.

#### Rubric:
- Correctly parsing and evaluating the expression (4 points)
- Proper use of arithmetic and logical operators (3 points)
- Correct handling of input and output (3 points)

#### Sample Input:
```
Enter a mathematical expression: 3 + 5 * 2 - 8 / 4
```

#### Sample Output:
```
Result: 10.0
```

#### Another Sample Input:
```
Enter a mathematical expression: (2 + 3) * (7 - 5)
```

#### Sample Output:
```
Result: 10
```

def evaluate_expression(expr):
    """Evaluate a mathematical expression."""
    try:
        result = eval(expr)
        return result
    except Exception as e:
        return str(e)

# Input from the user
input_expr = input("Enter a mathematical expression: ")
result = evaluate_expression(input_expr)
print(f"Result: {result}")






### Bonus Problem: Matrix Transpose (10 points)

### Problem:
Write a Python program to find the transpose of a matrix. The matrix is given as a list of lists.

### Rubric:
- Correctly transposing the matrix (4 points)
- Proper use of for loops (3 points)
- Correct input and output handling (3 points)

#### Sample Input:
```
(Program uses a predefined matrix)
```

#### Sample Output:
```
Original matrix:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]

Transposed matrix:
[1, 4, 7]
[2, 5, 8]
[3, 6, 9]
```

def transpose_matrix(matrix):
    """Transpose the given matrix."""
    # Create a new matrix for the transposed result
    transposed = []
    
    # Use a for loop to iterate through the columns of the original matrix
    for i in range(len(matrix[0])):
        # Create a new row for the transposed matrix
        new_row = []
        for row in matrix:
            new_row.append(row[i])
        transposed.append(new_row)
    
    return transposed

# Predefined matrix
original_matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Transpose the matrix
transposed_matrix = transpose_matrix(original_matrix)

# Display the original and transposed matrices
print("Original matrix:")
for row in original_matrix:
    print(row)

print("\nTransposed matrix:")
for row in transposed_matrix:
    print(row)




