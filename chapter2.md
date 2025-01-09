# 2.4.1 **Input**
**Finger exercise**: Write code that asks the user to enter their birthday in the form mm/dd/yyyy, and then prints a string of the  form ‘You were born in the year yyyy.’

#Answer <br>
```python
bday = input('Enter your birthday (dd/mm/yyyy): ')
birth_year = bday[-4:] # Take the last 4 characters from bday
print(f'Your were born in the year of {birth_year}.'}
```
# 2.5 **While Loops** 1

**Finger exercise** Replace the comment in the following code with a while loop.<br> 
```python
num_x = int(input('How many times should I print the letter X? '))
to_print = ''
#concatenate X to to_print num_x times
print(to_print) 
```
#Answer <br>
```python
num_x = int(input('How many time should I print the letter X? '))
to_print = ''

# A while look to concatenate 'X' to 'to_print' num_x times
count = 0 
while count < num_x: 
    to_print = 'X'
    count += 1
print(to_print)
```
# 2.5 **While Loops** 2 

**Finger exercise** Write a program that asks the user to input 10 integers, and then prints the largest odd number that was entered. If no odd number was entered, it should print a message to that effect.

#Answer
```python
count = 0
largest_odd = None
# Use a while loop to get 10 inputs
while count < 10:
    num = int(input(f'({count + 1}) Please enter 10 integers : '))
    if num % 2 != 0: # Check if the number is odd
        largest_odd = num if largest_odd is None else max(largest_odd, num)
    count += 1
# Output
if largest_odd is not None:
    print(f'The largest odd number entered is {largest_odd}.')
else:
    print('No odd number was entered.')
```

# Bonus: Converting the '*while loops 2*' to a for loop
```python
largest_odd = None
count = 0
# Use a for loop to get 10 inputs
for _ in range(10):
    count += 1
    num = int(input(f'({count}) Please enter 10 integers: '))
    if num % 2 != 0: # Check if the number is odd
        largest_odd = num if largest_odd is None else max(largest_odd, num)

if largest_odd is not None:
    print(f'The largest odd number entered is {largest_odd}.')
else:
    print('No odd number was entered.')
```

# 2.6 **For Loops and Range**

**Finger exercise** Write a program that prints the sum of the prime numbers greater than 2 and less than 1000. Hint: you probably want to use a for loop that is a primality test nested inside a for loop that iterates over the odd integers between 3 and 999.

```python
prime_sum = 0                       # Start with sum at zero
for i in range (3, 1000, 2):        # Check odd numbers
    prime_detector = True           # Assuming it's prime
    
    for p in range(2, int(i**0.5) +1): # Check divisors up to sqaure root
        if i % p == 0 :                 # If divides evenly 
            prime_detector = False     # Not prime
            break                      # Stop Checking
            
    if prime_detector:              # If nothing divided evenly
        prime_sum += i              # Add to sum

print(prime_sum)
```



