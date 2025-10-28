# Coding Session 5

> The coding sessions are here to help you get started and to understand, you may also ask questions. It is, however, important to read up on and try to understand the parts in the coding session before the coding session itself. 

The last coding session is about _data structures_. Mainly about the ones that are built-in to the language, but we will also look a bit at implementing data structures yourself. This includes understanding a bit of data classes, which are a subset of classes from object orientation but made much simpler.

<!-- 
## Task 1
Lists and tuples are very much alike, but they differ in that tuples are _immutable_. This, in turn, means that tuples are faster and use less memory. In this exercise we are going to look at that using the `timeit` library in Python. We don't have to understand every aspect of how the library works, as we are mainly concerned with the timing. 

```
Iteration:
List: 0.985602127000675
Tuple: 0.06765401600023324
Memory usage:
List: 920
Tuple: 224
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import timeit
import sys
import random


def iteration_test(data):
    for i in data:
        pass


def memory_test(data):
    return sys.getsizeof(data)


data_list = [random.randrange(1, 100) for i in range(100)]
data_tuple = (random.randrange(1, 100) for i in range(100))

print('Iteration:')
print('List: ', end='')
print(timeit.timeit(stmt='iteration_test(data_list)',
                    globals=globals(), number=1000000))
print('Tuple: ', end='')
print(timeit.timeit(stmt='iteration_test(data_tuple)',
                    globals=globals(), number=1000000))


print('Memory usage:')
print('List:', memory_test(data_list))
print('Tuple:', memory_test(data_tuple))

  ```
</details>
-->

## Task 1
Sets are used to store elements with no order and with no duplicates. Write a program that creates to sets, one called `star_wars` and one called `star_trek` and fill them with interesting things about the two worlds (see the printout below). Test the set operations _difference_, _intersection_ and _union_ with the two sets.

```
Star Wars: {'Adventure', 'Lightsabers', 'Hyperspace', 'In a galaxy far, far away', 'Space'}
Star Trek: {'Adventure', 'Photon torpedoes', 'Our galaxy', 'Warp', 'Space'}

Difference: {'In a galaxy far, far away', 'Hyperspace', 'Lightsabers'}
Intersection: {'Adventure', 'Space'}
Union: {'Photon torpedoes', 'Our galaxy', 'Warp', 'Hyperspace', 'In a galaxy far, far away', 'Space', 'Adventure', 'Lightsabers'}
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
star_wars = {'Space', 'Lightsabers', 'In a galaxy far, far away', 'Hyperspace', 'Adventure'}
star_trek = {'Photon torpedoes', 'Space', 'Our galaxy', 'Warp', 'Adventure'}

print('Star Wars:', star_wars)
print('Star Trek:', star_trek)

print()

print('Difference:', star_wars - star_trek)
print('Intersection:', star_wars & star_trek)
print('Union:', star_wars | star_trek)

  ```
</details>

## Task 2
Let the user enter some text and use a _set_ to determine the number of unique words in the string. Do not forget to make the text lower case and also to not count the space that is in the text (if the user writes a sentence).

```
Write some text: To be or not to be
Number of unique characters: 6
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
text = input('Write some text: ')

text_set = set(text.lower())
text_set.remove(' ')
print('Number of unique characters:', len(text_set))

  ```
</details>

## Task 3
Dictionaries are used to store key-value pairs in a set (they have no order). Here we like you to create a simple program that allows for adding teachers (by name) to a dictionary where the key is nothing but an incrementing integer. See the printout below to understand how to do it.

```
1. Enter teacher
2. Show teachers
3. Quit

==> 1
New teacher ("stop" to end): Tobias
New teacher ("stop" to end): Jonas
New teacher ("stop" to end): stop

1. Enter teacher
2. Show teachers
3. Quit

==> 2
0:Tobias
1:Jonas

1. Enter teacher
2. Show teachers
3. Quit

==> 1
New teacher ("stop" to end): Hobbe
New teacher ("stop" to end): Ola
New teacher ("stop" to end): stop

1. Enter teacher
2. Show teachers
3. Quit

==> 2
0:Tobias
1:Jonas
2:Hobbe
3:Ola

1. Enter teacher
2. Show teachers
3. Quit

==> 3
Bye for now!
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
teachers = dict()

choice = ''

while choice != '3':
    print('1. Enter teacher')
    print('2. Show teachers')
    print('3. Quit')
    print()
    choice = input('==> ')

    if choice == '1':
        name = ''
        while name != 'stop':
            name = input('New teacher ("stop" to end): ')
            if name != 'stop':
                incrementor = len(teachers)
                teachers[incrementor] = name
        print()
    elif choice == '2':
        for key in teachers:
            print(str(key) + ':' + teachers[key])
        print()
    elif choice == '3':
        print('Bye for now!')
    else:
        print('Try again!')

  ```
</details>

## Task 4
Dictionaries can also be used to represent more complex structures. Use a dictionary to create a structure for ships in Star Wars with name, manufacturer, model and pilots. Yes, pilots. This should be a list in the dictionary. Create two ships, as shown below, and put them in a list. Then print the name and all the pilots. Lastly, append another ship (the B-wing) and print all ships created by Slayn & Korpil.

The two first ships:
```
ship1 = {
    'name': 'Millennium Falcon',
    'manufacturer': 'Corellian Engineering Corporation',
    'model': 'YT-1300',
    'pilots': ['Han Solo', 'Chewbacca']
}

ship2 = {
    'name': 'T-6 1974',
    'manufacturer': 'Slayn & Korpil',
    'model': 'T-6 Shuttle',
    'pilots': ['Ahsoka Tano', 'Huyang']
}
```

The output from the running program:
```
Millennium Falcon is piloted by Han Solo Chewbacca 
T-6 1974 is piloted by Ahsoka Tano Huyang 
There are now 2 ships by Slayn & Kopril.
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
ship1 = {
    'name': 'Millennium Falcon',
    'manufacturer': 'Corellian Engineering Corporation',
    'model': 'YT-1300',
    'pilots': ['Han Solo', 'Chewbacca']
}

ship2 = {
    'name': 'T-6 1974',
    'manufacturer': 'Slayn & Korpil',
    'model': 'T-6 Shuttle',
    'pilots': ['Ahsoka Tano', 'Huyang']
}

ships = [ship1, ship2]

for s in ships:
    print(s['name'], 'is piloted by ', end='')
    for p in s['pilots']:
        print(p + ' ', end='')
    print()

ships.append({
    'name': 'Generic B-wing',
    'manufacturer': 'Slayn & Korpil',
    'model': 'B-wing heavy assault starfighter',
    'pilots': []
})

count = 0

for s in ships:
    if s['manufacturer'] == 'Slayn & Korpil':
        count += 1

print('There are now', count, 'ships by Slayn & Kopril.')

  ```
</details>

## Task 5
Even though the previous example looked a lot like JSON (JavaScript Object Notation), a much better way to store data, if that is what you want to do, is to use _data classes_ instead. These are simplified classes which are easier to use. Create a data class called Ship that should hold the information for a ship as above and put that in a new file. Next create a new Python program that creates the Millennium Falcon and prints out the pilots.

```
Name of the ship: Millennium Falcon
Piloted by:
Han Solo Chewbacca 
```

<details>
  <summary>Expand to see the solution</summary>

This is the data class (should be in one file):

  ```python
from dataclasses import dataclass


@dataclass
class Ship:
    name: str
    manufacturer: str
    model: str
    pilots: list()

  ```

This is the program using it:

```python
from ship import Ship

mf = Ship('Millennium Falcon', 'Corellian Engineering Corporation', 'YT-1300',
          ['Han Solo', 'Chewbacca'])

print('Name of the ship:', mf.name)

print('Piloted by:')
for s in mf.pilots:
    print(s, end=' ')

print()

```
</details>

## Task 6
It is now time to put all our knowledge together and create a simple linked list to show and understand the concepts. Start out by creating a separate file called `node.py` that holds each element, which in this case should be a string. Next create a new file called `linked_list.py` that builds the list itself using two methods, one for adding first and one for printing the content (called `add_first()` and `show()` respectively). Lastly, create a Python program that shows that the list works by creating a list and populate it.

```
a Jedi I am 
```

<details>
  <summary>Expand to see the solution</summary>


The node class

  ```python
from dataclasses import dataclass
from typing import Any


@dataclass
class Node:
    value: str = ''
    next: Any = None

  ```

The class for the linked list:

  ```python
from dataclasses import dataclass
from node import Node


@dataclass
class LinkedList:
    head: Node = None
    size: int = 0

    def add_first(self, s):
        new = Node(s, self.head)
        self.head = new

        self.size += 1

    def show(self):
        node = self.head
        text = ''

        while node is not None:
            text += node.value + ' '
            node = node.next

        return text

  ```

Main Python program using the class:

  ```python
from linked_list import LinkedList

lst = LinkedList()

lst.add_first('I am')
lst.add_first('a Jedi')

print(lst.show())

  ```
</details>

## Task 7
As built-in functions such as `max()` and `len()` does not work for our own data structure, you should add them as `count()` and `max()`. Do this as _methods_ to the data class. Also show a program that uses these methods by creating a string and sending it backwards to the linked list (so that `show()` returns the message the correct way). Then also test the new methods.

```
M a y   t h e   F o r c e   b e   w i t h   y o u 
25
y
```

<details>
  <summary>Expand to see the solution</summary>

Updated linked list:

  ```python
from dataclasses import dataclass
from node import Node


@dataclass
class LinkedList:
    head: Node = None
    size: int = 0

    def add_first(self, s):
        new = Node(s, self.head)
        self.head = new

        self.size += 1

    def show(self):
        node = self.head
        text = ''

        while node is not None:
            text += node.value + ' '
            node = node.next

        return text

    def count(self):
        return self.size

    def max(self):
        current = ''
        node = self.head

        while node is not None:
            if current < node.value:
                current = node.value
            node = node.next

        return current

  ```

Example program using the new methods:

  ```python
from linked_list import LinkedList

lst = LinkedList()

string = 'May the Force be with you'

for i in string[::-1]:
    lst.add_first(i)

print(lst.show())
print(lst.count())
print(lst.max())

  ```
</details>

## Task 8
It is now time to remove from the linked list. Implement the methods `remove_first()` and `remove_at()` and show that they work with a main program.

```
Dark Side of the Moon 
Side of the Moon 
Dark Side of the Moon 
Dark of the Moon 
```

<details>
  <summary>Expand to see the solution</summary>

Linked list with two remove methods:

  ```python
from dataclasses import dataclass
from node import Node


@dataclass
class LinkedList:
    head: Node = None
    size: int = 0

    def add_first(self, s):
        new = Node(s, self.head)
        self.head = new

        self.size += 1

    def show(self):
        node = self.head
        text = ''

        while node is not None:
            text += node.value + ' '
            node = node.next

        return text

    def count(self):
        return self.size

    def max(self):
        current = ''
        node = self.head

        while node is not None:
            if current < node.value:
                current = node.value
            node = node.next

        return current

    def remove_first(self):
        if self.head is not None:
            self.head = self.head.next
            self.size -= 1

    def remove_at(self, pos):
        if self.head is not None:
            if pos == 0:
                self.remove_first()
            elif pos > 0 and pos < self.size:
                prev = self.head

                for i in range(pos - 1):
                    prev = prev.next

                delete = prev.next
                prev.next = delete.next
                self.size -= 1

  ```

Main program using the remove methods:

  ```python
from linked_list import LinkedList

lst = LinkedList()

lst.add_first('Moon')
lst.add_first('the')
lst.add_first('of')
lst.add_first('Side')
lst.add_first('Dark')

print(lst.show())

lst.remove_first()

print(lst.show())

lst.add_first('Dark')

print(lst.show())

lst.remove_at(1)

print(lst.show())

  ```
</details>

## Task 9
It is tedious to have everything in reverse in the list, so in this exercise you should implement a method that prints it _the correct way_. The method, called `show_right()` should be _recursive_, meaning that it must call itself. To do this, we will create a private inner method in the method we call. Also create a main program to show that it works.

```
Wish you where here 
```

<details>
  <summary>Expand to see the solution</summary>

Linked list with recursive method to print the content the correct way:

  ```python
from dataclasses import dataclass
from node import Node


@dataclass
class LinkedList:
    head: Node = None
    size: int = 0

    def add_first(self, s):
        new = Node(s, self.head)
        self.head = new

        self.size += 1

    def show(self):
        node = self.head
        text = ''

        while node is not None:
            text += node.value + ' '
            node = node.next

        return text

    def count(self):
        return self.size

    def max(self):
        current = ''
        node = self.head

        while node is not None:
            if current < node.value:
                current = node.value
            node = node.next

        return current

    def remove_first(self):
        if self.head is not None:
            self.head = self.head.next
            self.size -= 1

    def remove_at(self, pos):
        if self.head is not None:
            if pos == 0:
                self.remove_first()
            elif pos > 0 and pos < self.size:
                prev = self.head

                for i in range(pos - 1):
                    prev = prev.next

                delete = prev.next
                prev.next = delete.next
                self.size -= 1

    def show_right(self):
        def _print_list(node, string):
            if node is None:
                return string
            string = node.value + ' ' + string
            return _print_list(node.next, string)

        return _print_list(self.head, '')

  ```

Main program to show that the method works:

  ```python
from linked_list import LinkedList

lst = LinkedList()

lst.add_first('Wish')
lst.add_first('you')
lst.add_first('were')
lst.add_first('here')

print(lst.show_right())


  ```
</details>
