# 2.4.1 **Input**
**Finger exercise**: Write code that asks the user to enter their birthday in the form mm/dd/yyyy, and then prints a string of the  form ‘You were born in the year yyyy.’

#Answer <br>
```python
bday = input('Enter your birthday (dd/mm/yyyy): ')
birth_year = bday[-4:] # Take the last 4 characters from bday
print(f'Your were born in the year of {birth_year}.'}
```
# 2.5 **While Loops**

**Finger exercise** Replace the comment in the following code with a while loop.<br> num_x = int(input('How many times should I print the letter X? ')) <br> to_print = '' <br> #concatenate X to to_print num_x times <br> print(to_print) <br><br>

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
