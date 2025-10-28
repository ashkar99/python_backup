# Coding Session 2

> The coding sessions are here to help you get started and to understand, you may also ask questions. It is, however, important to read up on and try to understand the parts in the coding session before the coding session itself. 

In this coding session, we take a deeper look into iteration and how to make things happen again and again. As this can be done in many different ways, we spend some time to explore this. In addition to this, we also look at functions and how they work. We will construct our functions and call them in different ways in different places in our code.

## Task 1
Write a program that counts from 10 to 1 using a `while` statement. The numbers should be printed on one line and be enclosed by `[]` as in the example below. 

```
[ 10 9 8 7 6 5 4 3 2 1 ]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
a = 10

print('[ ', end='')

while a > 0:
    print(f'{a} ', end='')
    a = a - 1

print(']')

  ```
</details>

## Task 2
Now write the same program again, but use a `for` statement instead. The output should be the same as in the previous task.

```
[ 10 9 8 7 6 5 4 3 2 1 ]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
print('[ ', end='')

for i in range(10, 0, -1):
    print(f'{i} ', end='')

print(']')
  ```
</details>

## Task 3
In this task, write a program that allows a user to repeatedly enter numbers until the number 0 is entered. When that happens, the program should end and the number of odd and even numbers should be printed.

```
Enter a number: 3
Enter a number: 1
Enter a number: 4
Enter a number: 6
Enter a number: 0
Number of even: 2
Number of odd: 2
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
answer = 1
odd = 0
even = 0

while answer != 0:
    answer = int(input('Enter a number: '))

    if answer == 0:
        pass
    elif answer % 2 == 0:
        even += 1
    elif answer % 2 != 0:
        odd += 1

print('Number of even:', even)
print('Number of odd:', odd)

  ```
</details>

## Task 4
Write a program that asks for a positive integer and if it is an even number that is entered, then all the even numbers up to (but not including) the number should be printed. If the number entered was odd, do the same but print only the odd numbers up to, but not including the entered number. See below for examples.

```
Up to: 8
0 2 4 6 

Up to: 11
1 3 5 7 9 
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
a = int(input('Up to: '))

if a % 2 == 0:
    start = 0
else:
    start = 1

for i in range(start, a, 2):
    print(f'{i} ', end='')

print()

  ```
</details>

## Task 5
In this task, you are going to create a program that prints out a triangle based on the number of lines given by the user. See below for an example.

```
How many lines? 5
*
**
***
****
*****
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
n = int(input('How many lines? '))

for i in range(1, n+1):
    for j in range(1, i+1):
        print('*', end='')
    print()

# Alternative solution

for i in range(1, n+1):
    print('*' * i)

  ```
</details>

## Task 6
Let's play a game! Write a program that allows the user to play a game of "Rock, Paper or Scissors" with the computer. The user should be allowed to select between rock, paper or scissor and the computer should randomly pick one of them. The game should be "best of three" and the end result should be printed when the match is over.

```
Choose Rock, Paper or Scissors: paper
Computer randomly takes: rock
Choose Rock, Paper or Scissors: scissor
Computer randomly takes: rock
Choose Rock, Paper or Scissors: rock
Computer randomly takes: scissors
Player wins!
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

ROCK = "rock"
PAPER = "paper"
SCISSORS = "scissors"

player = 0
computer = 0

while player < 2 and computer < 2:
    player_choice = input("Choose Rock, Paper or Scissors: ").lower()

    # Cheating a bit, using a list (don't tell Jonas...)
    computer_choice = random.choice([ROCK, PAPER, SCISSORS]).lower()
    print('Computer randomly takes:', computer_choice)

    if player_choice == ROCK and computer_choice == SCISSORS:
        player += 1
    elif player_choice == PAPER and computer_choice == ROCK:
        player += 1
    elif player_choice == SCISSORS and computer_choice == PAPER:
        player += 1
    else:
        computer += 1

# Print the winner of the game
if player == 2:
    print("Player wins!")
else:
    print("Computer wins!")

  ```
</details>

## Task 7
Now let's move on with functions. This first task is to create a program with a function called `maximum` that takes two variables, called `a` and `b` and returns the largest of the two. Complete this with a main part that shows how it all works by asking the user for input.

```
First number: 3
Second number: 5
The largest of the two is 5
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def maximum(a, b):
    if a > b:
        return a
    else:
        return b


# Here the main part of the program starts!
x = int(input('First number: '))
y = int(input('Second number: '))

m = maximum(x, y)

print('The largest of the two is', m)

  ```
</details>

## Task 8
Remember the calculation for the leap year from the last live coding session? Now redo this as a function instead, complete with a main part that will show how it works by letting the user enter a year. See below for two example runs of the program.

```
Enter a year: 2022
This is not a leap year.

Enter a year: 2020
This is a leap year.
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def is_leapyear(year):
    return (year % 4 == 0 and year % 100 != 0) or year % 400 == 0


# Here starts the program
y = int(input('Enter a year: '))

if (is_leapyear(y)):
    print('This is a leap year.')
else:
    print('This is not a leap year.')

  ```
</details>

## Task 9
A program can have more than one function (and most often does). Write a program with one function for calculating the circumference of a circle and one for calculating the area of a circle. Show a main part of the program that uses both of the functions and show the result using three decimals.

```
Radius of the circle: 6.1234
The circumference is 38.474
The area is 117.797
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import math


def circumference(r):
    return 2 * math.pi * r


def area(r):
    return math.pi * r**2


# Here starts the main program
radius = float(input('Radius of the circle: '))

print(f'The circumference is {circumference(radius):.3f}')
print(f'The area is {area(radius):.3f}')
  ```
</details>

## Task 10
Write a program that asks the user for a large number and then calculates the sum of different digits in that number. See below for an example run of the application.

```
Supply a large number: 1977
The sum of the numbers in 1977 is 24
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def sum_of_digits(n):
    sum = 0

    while n > 0:
        rem = n % 10
        sum = sum + rem
        n = n // 10

    return sum


# Here starts the program
number = int(input('Supply a large number: '))

print('The sum of the numbers in', number, 'is', sum_of_digits(number))

  ```
</details>

## Task 11
Python can return more than one value at a time and in this task we want you to write a program that has a method called `switch()` that takes two integers and returns them the other way around. See below for an example.

```
Give me a number: 3
Give me another: 4
x is 3
y is 4
x is 4
y is 3
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def switch(a, b):
    tmp = a
    a = b
    b = tmp
    return a, b


# Alternative solution
def switchero(a, b):
    return b, a

# Here the program starts
x = int(input('Give me a number: '))
y = int(input('Give me another: '))

print('x is', x)
print('y is', y)

x, y = switch(x, y)

print('x is', x)
print('y is', y)

  ```
</details>

## Task 12
To conclude, write a program with a function that accepts a string as well as a single character. The purpose of the function is to see if the character exists in the string and return true if so. If the character isn't found, it should return false. Below you can see two executions of the program.

```
Give me a sentence: May the Force be with you
Give me single character: u
Found it!

Give me a sentence: Dark Side of the Moon
Give me single character: ö
Was not in the sentence...
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def in_string(s, c):
    for i in s:
        if i == c:
            return True

    return False


# Here the program starts
text = input('Give me a sentence: ')
character = input('Give me single character: ')

if in_string(text, character):
    print('Found it!')
else:
    print('Was not in the sentence...')

  ```
</details>
