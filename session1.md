# Coding Session 1

> This sessions are here to help you get started and to understand, you may also ask questions. It is, however, important to read up on and try to understand the parts in the live coding session before the live coding session itself. You do not need to solve any of the tasks, but have a general understanding of it.

This first coding session focuses on getting to know Python as well as the development environment to use it (usually Visual Studio Code). The idea is to get familiar with the tools and the process of developing software. 

## Task 1
Write a Python program that displays the text "May The Force be with You" as `example1.py`. Run the program using the play button at the top.

```
May the Force be with You
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
print('May The Force be with You')
  ```
</details>

## Task 2
Write a program in Python that prints the answer to life, the universe and everything (42), where the number 42 should be just that -- a number and not part of the string.

```
The meaning of life, the universe and everything: 42
```

<details>
  <summary>Expand to see solution</summary>

  ```python
print('The meaning of life, the universe and everything:', 42)  
  ```
</details>

## Task 3
The previous example starts to make us think about data types and variables. In this task, write a program that declares a variable called `answer` that holds the value 42. This should then be printed along with the text from above, so the output is the same as before.

```
The meaning of life, the universe and everything: 42
```

<details>
  <summary>Expand to see solution</summary>

  ```python
answer = 42
print('The meaning of life, the universe and everything:', answer)
  ```
</details>

## Task 4
Continue on the previous program by printing the data type of the variable just created.

```
The meaning of life, the universe and everything: 42
<class 'int'>
```

<details>
  <summary>Expand to see solution</summary>

  ```python
answer = 42
print('The meaning of life, the universe and everything:', answer)
print(type(answer))
  ```
</details>

## Task 5
Now change the program so that the variable `answer` is a _string_ instead of an _int_. Also, use _string concatenation_ to show the answer as well as the label text.

```
The meaning of life, the universe and everything: 42
```

<details>
  <summary>Expand to see solution</summary>

  ```python
answer = '42'
print('The meaning of life, the universe and everything: ' + answer)
  ```
</details>

## Task 6
Programs become much more interesting if you allow the users to input something. In this task, write a program that asks the user for a word and then prints it out again.

```
Give me a word: Java
The word was Java
```

<details>
  <summary>Expand to see solution</summary>

  ```python
text = input('Give me a word: ')
print('The word was', text)
  ```
</details>

## Task 7
The `input()` command only reads strings, but sometimes you want to read an integer or a float value. Write a program using Python that reads two integers and shows the sum of them.

```
First number: 60
Second number: 6
The sum is 66
```

<details>
  <summary>Expand to see solution</summary>

  ```python
first = int(input('First number: '))
second = int(input('Second number: '))

sum = first + second

print('The sum is ' + str(sum))
  ```
</details>

**Note 1:** To make this work, we need to _convert_ the integer to a string when printing. 
**Note 2:** For now we will assume that the user gives us the correct type, later we will work with exception handling to make sure the user can input anything and we can tell the user when it is wrong.

## Task 8
Now show that Python can work with subtraction, multiplication and division as well. Let the user enter two numbers and print the results.

```
Give me a number: 33
Give me another number: 4 
Subtraction: 29
Multiplication: 132
Division: 8.25
```

<details>
  <summary>Expand to see solution</summary>

  ```python
number1 = int(input('Give me a number: '))
number2 = int(input('Give me another number: '))

print('Subtraction:', str(number1 - number2))
print('Multiplication: ' + str(number1 * number2))
print('Division:', str(number1 / number2))
  ```
</details>

## Task 9
Two mathematical operations that need a bit more introduction are _integer division_ and _modulus_. Write a program that shows how they work.

```
First number: 23
Second number: 2
Integer division of the numbers will give you: 11
That means that 1 still remain(s)
```

<details>
  <summary>Expand to see solution</summary>

  ```python
first = int(input('First number: '))
second = int(input('Second number: '))

print('Integer division of the numbers will give you:', str(first // second))
print('That means that', str(first % second), 'still remain(s)')
  ```
</details>

## Task 10
There are several other mathematical functions available in Python, for example, `max()`, `min()` and `round()` -- show how they work with a Python program.

```
Largest of the two is 60
Smallest is 9.24
The second number can be rounded to 9
```

<details>
  <summary>Expand to see solution</summary>

  ```python
first = 60
second = 9.24

print('Largest of the two is', str(max(first, second)))
print('Smallest is', str(min(first, second)))
print('The second number can be rounded to', str(round(second)))
  ```
</details>

## Task 11
Assignment is when a variable is given the value of what is placed on the other side. Usually a normal = is used, but there are several ways of doing it. Show how `+=`, `-=` as well as multiple assignments work in Python.

```
Original value: 38
Adding two to the value: 40
Subtracting ten from the value: 30
Two values: 42 66
```

<details>
  <summary>Expand to see solution</summary>

  ```python
value = 38

print('Original value:', value)

value += 2
print('Adding two to the value:', value)

value -= 10
print('Subtracting ten from the value:', value)

value, value2 = 42, 66
print("Two values:", value, value2)
  ```
</details>

## Task 12
So-called _f-strings_ are a nice way of handling the formatting of strings, and not the least numbers in strings. Write a program that multiplies two floating numbers and presents the result using two decimals.

```
First number: 2.02
Second number: 3.522
Here you are: 7.11
```

<details>
  <summary>Expand to see solution</summary>

  ```python
first = float(input('First number: '))
second = float(input('Second number: '))

multi = first * second

print(f'Here you are: {multi:.2f}')
  ```
</details>

## Task 13
Let's do some math! Write a program that asks for two sides of a right-angled triangle and calculates the length of the third side (hypotenuse) using the Pythagorean theorem ($c² = a² + b²$). As we are supplying a and b, we need to calculate c as $c = \sqrt{a² + b²}$. Print, using f-strings, the result using two decimals.

```
First side: 7
Second side: 4
Length of the hypotenuse is: 8.06
```

<details>
  <summary>Expand to see solution</summary>

  ```python
import math

a = float(input('First side: '))
b = float(input('Second side: '))

c = math.sqrt(a**2 + b**2)

print(f'Length of the hypotenuse is: {c:.2f}')
  ```
</details>

## Task 14
In this task, we are going to use the `random` library. Create a program that rolls two dice (six-sided) and prints the result of each as well as the sum of the two.

```
Let's roll!
First die: 6
Second die: 2
The sum is 8
```

<details>
  <summary>Expand to see solution</summary>

  ```python
import random

print("Let's roll!")

d1 = random.randint(1, 6)
d2 = random.randint(1, 6)

print('First die:', d1)
print('Second die:', d2)

print('The sum is', d1 + d2)
  ```
</details>

## Task 15
Many tabletop games use dice with sides other than just six. Write a program that asks for the number of sides the die should have and that rolls one after that.

```
How many sides do you want? 20
You rolled 19
```

<details>
  <summary>Expand to see solution</summary>

  ```python
import random

sides = int(input('How many sides do you want? '))

dX = random.randint(1, sides)

print('You rolled', dX)
  ```
</details>

## Task 16
Now, let's continue with _selection_. Create a program that asks for a positive number and says 'You did it!' if the number was positive.

```
Enter a positive number: 3
You did it!
```

<details>
  <summary>Expand to see solution</summary>

  ```python
a = int(input('Enter a positive number: '))

if a > 0:
    print('You did it!')
  ```
</details>

## Task 17
Write a program that asks the user for a positive number and tells the user if it is in the range 1 -- 10, 11 -- 100, 101 -- 1000 or above. See below for _several executions_ of the program.

```
Give me a number: 1024
It is larger than 1000.

Give me a number: 64
It is in the range of 10.

Give me a number: 512
It is in the range of 100.
```

<details>
  <summary>Expand to see solution</summary>

  ```python
a = int(input('Give me a number: '))

if a >= 1000:
    print('It is larger than 1000.')
elif a >= 100:
    print('It is in the range of 100.')
elif a >= 10:
    print('It is in the range of 10.')
else:
    print('It is in the range of 1.')
  ```
</details>

## Task 18
This program should ask the user for a temperature and then print out a suitable message depending on the range of the temperature. See below for several executions of the program.

```
What is the temperature? 18
Welcome to Växjö!

What is the temperature? 22
A bit hot, isn't it...

What is the temperature? -15
Ah, just what I wanted!
```

<details>
  <summary>Expand to see solution</summary>

  ```python
temp = float(input('What is the temperature? '))

if temp < -10:
  print('Ah, just what I wanted!')  
elif temp < 0 and temp >= -10:
    print('Cold and nice!')
elif temp > 0 and temp < 20:
    print('Welcome to Växjö!')
elif temp >= 20 and temp < 30:
    print("A bit hot, isn't it...")
else:
    print('Way too hot!')
  ```
</details>

## Task 19
In this task, write a program that calculates if a given year is a leap year or not. The definition of a leap year is a year that is evenly divisible with 4 but not such years that are also divisible with 100. However, if the year is evenly divisible by 400, then it is a leap year. See below for several executions of the program.

```
Write a year: 2023
Not a leap year...

Write a year: 2020
Leap year!

Write a year: 1800
Not a leap year...
```

<details>
  <summary>Expand to see solution</summary>

  ```python
year = int(input('Write a year: '))

if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:
    print('Leap year!')
else:
    print('Not a leap year...')
  ```
</details>

## Task 20
In this task, create a program where it is possible (does not have to be user input) to decide, based on temperature and the use of an umbrella, if a person will be wet or fine. See below for a couple of examples of what it could look like when running.

```
What temperature is it? 18
Is it raining? y
Do you have an umbrella? n
Too bad, you will be wet!

What temperature is it? 22
Is it raining? n
Do you have an umbrella? n
All is well!

What temperature is it? 14
Is it raining? n
Do you have an umbrella? y
You seem to be fine.
```

<details>
  <summary>Expand to see solution</summary>

  ```python
temp = int(input('What temperature is it? '))
rain = input('Is it raining? ')

if rain == 'y':
    raining = True
else:
    raining = False

umb = input('Do you have an umbrella? ')

if umb == 'y':
    umbrella = True
else:
    umbrella = False

if temp >= 20 and not raining:
    print('All is well!')
elif temp < 20 and raining:
    if umbrella:
        print('It is raining, but you have your umbrella!')
    else:
        print('Too bad, you will be wet!')
else:
    print('You seem to be fine.')
  ```
</details>
