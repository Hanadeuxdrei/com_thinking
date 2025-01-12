# 4.1.1 Function Definitions
**Finger exercise 1**: Use the find_root function in Figure 4-3 to print the sum of approximations to the square root of 25, the cube root of -8, and the fourth root of 16. Use 0.001 as epsilon.

```python
# Figure 4-3
def find_root(x, power, epsilon):
    # Find interval containing answer
    if x < 0 and power % 2 == 0:
        return None #negative number has no even-powered roots
    low = min(-1, x)
    high = max(1, x)
    # Use bisection search
    ans = (high + low)  / 2
    while abs(ans ** power - x) >= epsilon:
        if ans ** power < x:
            low = ans
        else:
            high = ans
        ans = (high + low) / 2
    return ans
# Sqaure root of 25, cube root of -8, fourth root of 16
square_root_25 = find_root(25, 2, 0.001) 
cube_root_8 = find_root(-8, 3, 0.001) 
fourth_root_16 = find_root(16, 4, 0.001)

# The sum of approximations
sum_appx = square_root_25 + cube_root_8 + fourth_root_16
print(sum_appx)
```

**Finger exercise 2**: Write a function is_in that accepts two strings as arguments and returns True if either string occurs anywhere in the other, and False otherwise. Hint: you might want to use the built-in str operator in.

```python
def is_in(x, y):    
   return x in y or y in x
    
is_in('hello', 'hello world')
is_in('opencourseware', 'tupperware')
is_in('fingerexercise', 'exercise')
```

**Finger exercise 3**: Write a function to test is_in.

```python
def test_is_in(first_set, second_set):
    for first in first_set:
        for second in second_set:
            result = is_in(first, second)
            print(f'Checking if "{first}" matches with "{second}": {result}')

word_set1 = ('play', 'sea', 'bird', 'rain', 'heart')
word_set2 = ('playground', 'seashore', 'blackbird', 'rainbow', 'sweetheart')

test_is_in(word_set1, word_set2)
```