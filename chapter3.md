# 3.1   Exhausitve Enumeration
**Finger exercise 1**: Change the code in Figure 3-2 so that it returns the largest rather than the smallest divisor. Hint: if y*z = x and y is the smallest divisor of x, z is the largest divisor of x.

**Figure 3-2**
```python
# Test if an int > 2 is prime. If not, print smallest divisor
x = int(input('Enter an integer greater than 2: '))
smallest_divisor = None
for guess in range(2, x):
    if guess x % guess == 0:
        smallest_divisor = guess
        break
if smallest_divisor != None:
    print('Smallest divisor of', x, 'is', smallest_divisor)
else:
    print(x, 'is a prime number')
```

### Answer
```python
x = int(input('Enter an integer greater than 2: '))
largest_divisor = None

for guess in range(2, x):
    if x % guess == 0:
        largest_divisor = x // guess #Using the hint
        break
if largest_divisor != None:
    print(f'Largest divisor of {x} is {largest_divisor}')
else:
    print(f'{x} is a prime number')
```
<br>

**Finger exercise 2**: Write a program that asks the user to enter an integer and prints two integers, root and pwr, such that 1 < pwr < 6 and root**pwr is equal to the integer entered by the user. If no such pair of integers exists, it should print a message to that effect.

### Answer
```python
# Ask user for a number and convert the input to an integer
n = int(input("Enter an integer: "))

# Create a flag to track if we find a solution
found = False

# Try each power from 2 to 5 (1 < pwr < 6)
for pwr in range(2, 6):  
    # Calculate the possible root by:
    # 1. Taking n to the power of (1/pwr) - this finds the root
    # 2. Rounding to nearest integer because we need whole numbers
    root = round(n ** (1/pwr))
    
    # Check if this root and power combination gives us back our number
    # Example: if n=8, is root³=8? or if n=16, is root⁴=16?
    if root ** pwr == n:
        print("root:", root, "pwr:", pwr)
        found = True
        break

if not found:
    print("No such pair of integers exists.")
```

**Finger exercise 3**: Write a program that prints the sum of the prime numbers greater than 2 and less than 1000. Hint: you probably want to have a loop that is a primality test nested inside a loop that iterates over the odd integers between 3 and 999.
### Answer
```python
prime_sum = 0
for prime in range(3, 1000, 2):  # Check odd numbers from 3 to 999
    prime_detector = True
    # Primality tester
    for tester in range(3, int(prime**0.5) + 1, 2):  # Only test odd divisors
        if prime % tester == 0:
            prime_detector = False
            break
    # If prime, add the prime number itself
    if prime_detector:  
        prime_sum += prime

print(prime_sum)
```

# 3.2 Approximate Solutions and Bisection Search

**Finger exercise 1**: What would the code in Figure 3-5 do if x = -25?

**Figure 3-5**
```python
x = 123456789
epsilon = 0.01
num_guesses, low = 0, 0
high = max(1, x)
ans = (high + low) / 2
while abs(ans**2 - x) >= epsilon:
    print('low=', low, 'high =', high, 'ans=', ans)
    num_guesses +=1
    if ans**2 < x:
        low = ans
    else:
        high = ans
    ans = (high + low)/ 2
print('number of guesses =', num_guesses)
print(ans, 'is close to square root of', x)
```

### Answer 
It would run forever and never find an answer because abs(ans**2-x) will
always be greater than epsilon (0.01)


**Finger exercise 2** :What would have to be changed to make the code in Figure 3-5 work for finding an approximation to the cube root of both negative and positive numbers? Hint: think about changing low to ensure that the answer lies within the region being searched.

### Answer
```python
x = -25
epsilon = 0.01

# Counter to keep track of how many guesses we make
num_guesses = 0

# Set the lower bound of our search range
# For negative numbers, we need to search in negative range
# min(-1, x) ensures we go low enough for negative numbers
low = min(-1, x)

# Set the upper bound of our search range
# max(1, x) ensures we go high enough for positive numbers
high = max(1, x)

# Make first guess halfway between high and low bounds
ans = (high + low) / 2

# Keep looping until our cubed guess is within epsilon of x
# |ans³ - x| >= epsilon means "the difference between our cubed guess and x is too big"
while abs(ans**3 - x) >= epsilon:
    # Print current state for debugging/tracking
    print('low=', low, 'high =', high, 'ans=', ans)
    
    # Count this attempt
    num_guesses += 1
    
    # If our cubed guess is too small, make the low bound higher
    # If our cubed guess is too big, make the high bound lower
    if ans**3 < x:
        low = ans
    else:
        high = ans
    
    # Make new guess halfway between current bounds
    ans = (high + low) / 2

print('number of guesses =', num_guesses)
print(ans, 'is close to cube root of', x)
```

**Finger exercise 3***: The Empire State Building is 102 stories high. A man wanted to know the highest floor from which he could drop an egg without the egg breaking. He proposed to drop an egg from the top floor. If it broke, he would go down a floor, and try it again. He would do this until the egg did not break. At worst, this method requires 102 eggs. Implement a method that at worst uses seven eggs.

### Answer
```python
low = 1
high = 102
max_attempts = 7 # int(log2(102)) + 1 
floors = []

while max_attempts > 0:
    mid = (low + high) // 2
    floors.append(mid)
    max_attempts -= 1
    # After each drop:
    # if egg breaks: high = mid - 1
    # if egg survives: low = mid + 1

print(f"Drop sequence: {floors}")
```

#3.3 A few words about using floats

**Finger exercise**: Finger exercise: What is the decimal equivalent of the binary number 10011?

### Answer
Finger exercise binary numbers
Convert 10011 to decimal:
Starting from right:
1 in the ones(2^0) place = 1
1 in the twos(2^1) place = 2
0 in the fours(2^2) place = 0
0 in the eights(2^3) place = 0
1 in the sixteens(2^4) place = 16
Add them all up: 16 + 2 + 1 = 19
