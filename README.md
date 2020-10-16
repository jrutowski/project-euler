
**What's this about?** This is a collection of some of my solutions to the Project Euler problems available at [link]projecteuler.net[/link] (so spoiler alert). I did my best to organize them in a fashion
such that the structure would be understandable! So far there are 13 problem solutions (and hopefully many more to come).

```python
##############################################
#Project Euler Problem Solutions
##############################################
#Problem 3 -- What is the largest prime factor of the number 600851475143 
from itertools import count, islice
from math import sqrt
import time
def isprime(n):
    if n < 2:
        return False 
    for number in islice(count(2), int(sqrt(n)-1)):
        if(n%number == 0):
            return False
    return True
prime_list = []
import numpy as np
def prime_factors_rapid(n):
    array = np.arange(int(sqrt(n)-1))
    for i in np.nditer(array):
        if((n%i == 0) & (isprime(i) == True)):
            prime_list.append(i)
    return max(prime_list)

import time
start = time.time()
prime_factors_rapid(600851475143)
end = time.time()
print(end - start)

#Find the largest Palindrome Product#
import numpy as np 
from itertools import combinations
array_1 = np.arange(100,1000)
combinations_list = list(combinations(array_1, 2))
product_list = np.prod(combinations_list, axis = 1)
palindrome_list = []

def palindrome_number(number):
    rev = 0
    while(number > 0):
        digit = number%10
        rev = rev*10 + digit
        number = number//10
    return rev

def palindrome_max(list):
    for products in product_list:
        if(palindrome_number(products) == products):
            palindrome_list.append(products)
    return max(palindrome_list)
palindrome_max(combinations_list)


#2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.
#What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?
import numpy as np
from functools import reduce      
def gcd(a,b):
    while b != 0:
        a,b = b, a%b
    return a
print(reduce(lambda a,b: a*b / gcd(a,b), range(1,21))
    
#Sum Square Difference:
def nums(n):
    array = np.arange(1, n+1)
    array_sum = np.sum(array)
    array_sum_squared = (array_sum)*(array_sum)

    squared_array = [x * x for x in array]
    squared_sum = np.sum(squared_array)

    return (array_sum_squared - squared_sum)


#10001st Prime Number#
def prime_sequence(ceiling):
    prime_list = []
    prime_array = np.arange(1, ceiling)
    for integer in range(len(prime_array)):
        if(isprime(integer) == True):
            prime_list.append(integer)
    return prime_list[10000]

#Triangle Numbers -- Problem 12
def triangle_num(x):
    number = (x*(x+1))/2
    return number

def triangle_divisors(num):
    array = np.arange(1, num)
    divisors = np.arange(1,501)
    triangle_array = [triangle_num(x) for x in array]
    division_matrix = np.zeros(shape = (num, 501))
    return division_matrix

#Collatz Conjecture: Problem 14: Find the integer with the largest collatz 'chain'
import numpy as np 
def collatz_generator(n):
    yield(float(n))
    while n != 1:
        if(n%2 == 0):
            n= n/2
            yield(n)
        else:
            n = 3*n+1
            yield(n)
print(list(collatz_generator(9)))
def problem_14(ceiling):
    array = np.arange(1, ceiling+1)
    collatz_length = []
    for i in np.nditer(array):
        x = []
        x = list(collatz_generator(i))
        collatz_length.append(len(x))
    return collatz_length.index(max(collatz_length))+1 #To offset Array begininng at 1 

test = [1,2,3,4,5]
test.index(max(test))
collatz_length.index(max(collatz_length))

#Problem 9: Pythagorean Triplet#
def triplet(goal):
    a = np.arange(1, goal)
    a_sq = []
    for integer in np.nditer(a):
        squared = integer * integer
        a_sq.append(squared)
    b = a_sq 
    c = a_sq 


#Problem 16: Triangle Divisors:
from math import factorial

def digit_sum(x):
    x_str = str(x)
    sum = 0
    for i in x_str:
        sum += int(i)
    return sum
digit_sum(2**1000)
digit_sum(factorial(100))

test = 2**1000

#Problem 25: What is the index of the first term in the Fibonacci sequence to contain 1000 digits
def fibonacci_generator():
    x,y = 1,1
    index = 1
    while (len(str(x)) <= 1000):
        yield(len(str(x)), index)
        index += 1
        x,y = y, x+y
print(list(fibonacci_generator()))
print(list(collatz_generator(9)))

# Problem 12: Highly divisible triangular number
#Create a triangle number generator
import numpy as np
def triangular_numbers(ceiling):
    natural_numbers = np.arange(1,ceiling+1)
    triangle_num = 0
    for index, numbers in enumerate(natural_numbers):
        triangle_num += numbers
        yield triangle_num

print(list(triangular_numbers(10)))
#List the divisors in each triangle number
def divisors():
    divisors_count = 0
    divisors_list = np.arange(1,500000000)
    for i in range(len((divisors_list))):
        triangle_list = list(triangular_numbers(i))
        for triangle in triangle_list:
            if(triangle % i == 0):
                divisors_count += 1
                if(divisors_count >= 500):
                    return triangle
                   

#Problem 34: Digital Factorials
from math import factorial
def problem_34(ceiling):
    candidate_list = []
    array = np.arange(3, ceiling + 1)
    for integer in array:
        integer_str = str(integer)
        for i in len(integer_str):
            


```
