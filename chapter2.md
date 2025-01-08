# 2.4.1 **Input**
**Finger exercise**: Write code that asks the user to enter their birthday in the form mm/dd/yyyy, and then prints a string of the  form ‘You were born in the year yyyy.’

#Answer <br>
bday = input('Enter your birthday (dd/mm/yyyy): ') <br>
birth_year = bday[-4:] <br>
print(f'Your were born in the year of {birth_year}.'}
