# 3.1   Exhausitve Enumeration
**Finger exercise 1** Finger exercise: Change the code in Figure 3-2 so that it returns the largest rather than the smallest divisor. <br> Hint: if y*z = x and y is the smallest divisor of x, z is the largest divisor of x.

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

**Finger exercise 2** Finger exercise: Write a program that asks the user to enter an integer and prints two integers, root and pwr, <br> such that 1 < pwr < 6 and root**pwr is equal to the integer entered by the user. If no such pair of integers exists, it should print a message to that effect.

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
