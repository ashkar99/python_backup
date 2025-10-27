# Coding Session 3

> The coding sessions are here to help you get started and to understand, you may also ask questions. It is, however, important to read up on and try to understand the parts in the coding session before the coding session itself. You do not need to solve any of the tasks, but have a general understanding of it.

The purpose of this session is to have a further look at how to use classes and objects that are available for you in Python. This means to call methods on objects that are available in the standard library. This session is also about _lists_ in Python. We will add, remove and search for elements in lists as well as use them with functions.

## Task 1
Create a function that takes a string and strips it of any whitespace before or after the text as well as making it all lowercase. The user should be able to input a string and see both the original and the stripped version of the string.

```
Enter sentence:   Wish You Were Here
Original sentence: [  Wish You Were Here        ]
Cleaned sentence: [wish you were here]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def stripped(s):
    s = s.strip()
    s = s.lower()

    return s


# Here starts the program
text = input('Enter sentence: ')

print('Original sentence: [' + text + ']')
text = stripped(text)
print('Cleaned sentence: [' + text + ']')

  ```
</details>

## Task 2
Another class that is available in Python is `Decimal` for handling decimal numbers using fixed sizes of the decimals. This makes it easier to calculate simple decimal numbers without getting the approximate value as with floats. Create a program that explores this by calculating 0.1 + 0.1 + 0.1 - 0.3 using both decimal and floating point numbers.

```
The floating numbers: 0.1 0.3
The decimal numbers: 0.1 0.3
Calculating 0.1 + 0.1 + 0.1 - 0.3
Using float: 5.551115123125783e-17
Using Decimal: 0.0
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
from decimal import Decimal

x = Decimal('0.1')
y = Decimal('0.3')

a = 0.1
b = 0.3

print('The floating numbers:', a, b)
print('The decimal numbers:', x, y)

print('Calculating 0.1 + 0.1 + 0.1 - 0.3')
print('Using float:', a + a + a - b)
print('Using Decimal:', x + x + x - y)

  ```
</details>

## Task 3
Lists in Python are also classes and in this task, you should create a list with three integer values that are then printed out.

```
1 2 3 
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
lst = [1, 2, 3]

for i in lst:
    print(f'{i} ', end='')

print()

  ```
</details>

## Task 4
Now create a program that has a list of five integer values that are printed on the screen. After that, the program should replace all values in the list with the power of two for each value. It should then print the content of the list again.

```
Before calculation: [1, 2, 3, 4, 5]
After calculations: [1, 4, 9, 16, 25]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
lst = [1, 2, 3, 4, 5]

print('Before calculation:', lst)

for i in range(0, len(lst)):
    lst[i] = lst[i] ** 2

print('After calculations:', lst)

  ```
</details>

## Task 5
In this task, create a program that generates ten random integer values between 1 and 100 in a list. It should then print the complete list, together with the largest and smallest values in the list as well as the sum of all values. 

```
All values: [81, 19, 84, 61, 3, 65, 34, 41, 28, 81]
Largest value: 84
Smallest value: 3
Sum of all values: 497
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

lst = []

for i in range(10):
    lst.append(random.randint(1, 100))

print('All values:', lst)
print('Largest value:', max(lst))
print('Smallest value:', min(lst))
print('Sum of all values:', sum(lst))

  ```
</details>

## Task 6
Lists also work with functions, as any data type will do. Create a function that takes a list and calculates the average of the integers it is sent. The value should be returned to the main part of the program. The program should, in the main part, create a list of ten random integers between 1 and 100 and use that as input to the function.

```
The average is 36.6
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random


def average(ls):
    sum = 0

    for e in ls:
        sum = sum + float(e)
    avg = sum / len(ls)

    return avg


# The program starts here
lst = []

for i in range(10):
    lst.append(random.randint(1, 100))

print('The average is', average(lst))

  ```
</details>

## Task 7
Now create a program that has a function that takes a sentence and a single character and returns a list of what positions in the string the character can be found. Let the user enter a sentence and a character to search for.

```
Write a sentence: May The Force be with You
What character to look for: e
The letter "e" is at: [6, 12, 15]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def in_list(text, character):
    places = []

    for i in range(len(text)):
        if text[i] == character:
            places.append(i)

    return places


# Program starts here
sentence = input('Write a sentence: ')
single = input('What character to look for: ')

print('The letter "' + single + '" is at:', in_list(sentence, single))

  ```
</details>

## Task 8
Use lists (three in total) to create a deck of cards. The program should then shuffle the cards (using the `shuffle()` method in `random`) and display the top five cards. Notice that this becomes a bit easier when we can use object orientation, but it is a start.

```
Card number 37 is Queen of Diamonds
Card number 26 is Ace of Diamonds
Card number 30 is 5 of Diamonds
Card number 1 is 2 of Spades
Card number 34 is 9 of Diamonds
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

deck = []

for x in range(0, 52):
    deck.append(x)

suits = ['Spades', 'Hearts', 'Diamonds', 'Clubs']
ranks = ['Ace', '2', '3', '4', '5', '6', '7', '8', '9', '10',
         'Jack', 'Queen', 'King']

# Means that deck value 0 is Ace of Spades, 13 is Ace of Hearts,
# 14 is 2 of Hearts and so on

random.shuffle(deck)

for i in range(5):
    suit = suits[deck[i] // 13] # Gives one of 0 to 3
    rank = ranks[deck[i] % 13] # Gives one of 0 and 12
    print('Card number', deck[i], 'is', rank, 'of', suit)

  ```
</details>

<!-- 
##Task 8
There are many methods available to strings, so create a method that takes a sentence and splits it into individual words but removes anything that isn't just words (so stripping out numbers and symbols). The result should be returned as a list of strings. It does not have to be perfect (that is for a later assignment) but a simple start.

```
Write a sentence: The question was: is it 42? Or is it another number?
The individual words are: ['The', 'question', 'was', 'is', 'it', 'Or', 'is', 'it', 'another', 'number']
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
def parser(str):
    result = []

    words = str.split()

    for s in words:
        if s.isalpha():
            result.append(s)
        else:
            tmp = ''
            for c in s:
                if c.isalpha():
                    tmp += c

            if tmp != '':
                result.append(tmp)

    return result


# Here starts the program
text = input('Write a sentence: ')

print('The individual words are:', parser(text))

  ```
</details>
-->

## Task 9
It is time to do some stuff with slicing lists. See below for examples of what to do where the next but last is another way of doing the same as above it.

```
All elements: [42, 66, 1138, 88, 1, 2001]
All except first and last: [66, 1138, 88, 1]
Every other from the first: [42, 1138, 1]
Every other from the second: [66, 88, 2001]
Going backwards: [66, 1138]
Same as: [66, 1138]
Reverse: [2001, 1, 88, 1138, 66, 42]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
lst = [42, 66, 1138, 88, 1, 2001]

print('All elements:', lst)
print('All except first and last:', lst[1:-1])
print('Every other from the first:', lst[::2])
print('Every other from the second:', lst[1::2])
print('Going backwards:', lst[1:-3])
print('Same as:', lst[1:-3 + len(lst)])
print('Reverse:', lst[::-1])

  ```
</details>

## Task 10
A list List is sent as a _reference_ which means that the contents of it can be changed even from a function. Illustrate this by creating a program that has a function that takes a list of integers and a number to multiply each element with. The function should _not_ return anything but rather make changes to the list itself.

```
The list before function call: [6, 1, 3, 5, 4, 7, 8, 7, 4]
The list after function call: [12, 2, 6, 10, 8, 14, 16, 14, 8]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random


def multiply(lst, multi):
    for i in range(0, len(lst)):
        lst[i] = lst[i] * multi


# Here starts the program
the_list = []

for e in range(1, 10):
    the_list.append(random.randint(1, 10))

print('The list before function call:', the_list)
multiply(the_list, 2)
print('The list after function call:', the_list)
  ```
</details>

## Task 11
An advanced feature of Python is _list comprehension_ which allows for an easier population of lists. In this task, create a small program that creates a list of ten random values between 1 and 100 using list comprehension.

```
Random numbers: [50, 78, 3, 32, 29, 97, 85, 25, 35, 49]
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

res = [random.randrange(1, 100) for i in range(10)]

print('Random numbers:', res)

  ```
</details>

## Task 12
Lists can also be _multi-dimensional_. There is no upper limit to how many dimensions lists can have, but for now, we will stay at two. In this exercise, make a program that creates a two-dimensional list of integers and then displays it using a nested for-iteration.

```
Only showing the values
1 2 3 
4 5 6 

Using index to address the values
1 2 3 
4 5 6 
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

print('Only showing the values')
for i in matrix:
    for j in i:
        print(j, end=' ')
    print()
print()

print('Using index to address the values')
for i in range(len(matrix)):
    for j in range(len(matrix[i])):
        print(matrix[i][j], end=' ')
    print()

  ```
</details>

## Task 13
Now write a program that asks the user for the number of rows and columns and then puts random values in the two-dimensional list (values between 1 and 100). The program should then print the two-dimensional list and sum all the integers together.

```
Enter the number of rows: 6
Enter the number of columns: 8

 55  23  25  66  97  72   2  85 
 42  51   4  64  64  48  88  37 
  2  65  54  25  75  40  82  78 
 25  45  16  31  20  59  25  76 
 11  27  66  57  38  85  82  46 
 23  16  10  23  34  81  48  51 

The sum of the integers is 2239
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

matrix = []

number_of_rows = int(input('Enter the number of rows: '))
number_of_columns = int(input('Enter the number of columns: '))

print()

for row in range(number_of_rows):
    matrix.append([])
    for column in range(number_of_columns):
        matrix[row].append(random.randint(1, 100))

sum = 0

for r in matrix:
    for c in r:
        print(f'{c:3}', end=' ')
        sum = sum + c
    print()

print()

print('The sum of the integers is', sum)

  ```
</details>
