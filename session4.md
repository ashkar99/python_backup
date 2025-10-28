# Coding Session 4

> The coding sessions are here to help you get started and to understand, you may also ask questions. It is, however, important to read up on and try to understand the parts in the coding session before the coding session itself. 

In this session the focus is on file I/O, that is how to read and write to files. It should be noted that it does not have to be files on a disk, but could be to and from the internet as well. We will primarily work with _text files_ and not with binary files. With this, we will also look at exception handling as that is preferred when using files. 

## Task 1
Write a Python program that just displays the current working directory. This will be the place where we load and save all the other files in this session to.

```
We are here: /home/tanmsi/gittemp/pythonexempel
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import os

path = os.getcwd()

print('We are here:', path)

  ```
</details>

## Task 2
Now write a program that creates a file called `pinkfloyd.txt` in which our Python program should place the names of a few important Pink Floyd albums.

```
No output on the screen...
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
output_file = open('pinkfloyd.txt', 'w')

output_file.write('The Dark Side of the Moon\n')
output_file.write('Wish You Were Here\n')
output_file.write('Animals\n')
output_file.write('The Wall\n')

output_file.close()

  ```
</details>

## Task 3
Obviously, we now need to read the file again and display it on screen. So, in this exercise, do that using the `read()` method to get everything into one string. As we have created the file ourselves it should not be a problem to open it, but especially Windows can sometimes have problems reading files and might need to add `encoding='utf-8'` to `open()`.

```
The Dark Side of the Moon
Wish You Were Here
Animals
The Wall
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import os.path

if os.path.isfile('pinkfloyd.txt'):
    input_file = open('pinkfloyd.txt', 'r')
    content = input_file.read()
    print(content)
    input_file.close()

  ```
</details>

## Task 4

It isn't feasible to read a large text into a string variable, and therefore it is often useful to read a file line by line instead. In this exercise, you should create a program that reads the file <a href="The_Shadow_over_Innsmouth.txt">The Shadow over Innsmouth</a> that you need to download and put in the correct path. The program should print the ten first lines and the total number of lines.


Not every line is shown:
```
The Shadow over Innsmouth

I.

During the winter of 1927–28 officials of the Federal government made a strange and secret investigation of certain conditions in the ancient Massachusetts seaport of Innsmouth. The public first learned of it in February, when a vast series of raids and arrests occurred, followed by the deliberate burning and dynamiting—under suitable precautions—of an enormous number of crumbling, worm-eaten, and supposedly empty houses along the abandoned waterfront. Uninquiring souls let this occurrence pass as one of the major clashes in a spasmodic war on liquor.

Number of lines: 263
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import os.path

if os.path.isfile('The_Shadow_over_Innsmouth.txt'):
    story = open('The_Shadow_over_Innsmouth.txt')

    count = 0

    for line in story:
        if count < 10:
            print(line)
            count += 1
        else:
            count += 1

    print('Number of lines:', count)

    story.close()

  ```
</details>

## Task 5
Back to the file about Pink Floyd! You might have noticed that it did not contain all the albums, so we are going to append a few more in this exercise (don't worry, we won't do all of them). Ask the user for more albums and stop when the user enters "stop" as the album name. Show the file when the new albums have been added.

```
Name of album: The Division Bell
Name of album: stop
The Dark Side of the Moon
Wish You Were Here
Animals
The Wall
The Division Bell
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
output_file = open('pinkfloyd.txt', 'a')

album = ''

while album != 'stop':
    album = input('Name of album: ')
    if album != 'stop':
        output_file.write(album)

output_file.close()

input_file = open('pinkfloyd.txt', 'r')

content = input_file.read()

print(content)

  ```
</details>

## Task 6
Now, let's copy a text file to another file by reading it line by line. To make it more interesting, we will in this example use `with` to say what files to open and how. The good thing about using `with` is that it will make sure that the file is closed when the program exits the scope (block). The program should ask the user for the file name of the file to copy and a new file name for the copy.

```
File to read from: pinkfloyd.txt
File to write to: pf.txt
5 rows and 79 characters copied.
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
input_file = input('File to read from: ')
output_file = input('File to write to: ')

with open(input_file, 'r') as infile, open(output_file, 'w') as outfile:
    r, c = 0, 0

    for row in infile:
        c += outfile.write(row)
        r += 1

    print(f'{r} rows and {c} characters copied.')

  ```
</details>

## Task 7
The most modern way, at the time of writing, to handle directories and file listings is to use `scandir`. In this exercise, you should write a Python program that prints out the files and directories in the current working directory in a nicely formatted way. It should state the kind of entry it is (file or directory). Lastly, you should use `with` from the example above to safely use files.

```
Directory : session4
Directory : .vscode
File      : The_Shadow_over_Innsmouth.txt
Directory : extra
File      : test.png
Directory : session1
File      : pinkfloyd.txt
Directory : session3
File      : pf.txt
Directory : session2
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import os

with os.scandir('.') as entries:
    for entry in entries:
        if entry.is_file():
            print(f'{"File":10}: {entry.name}')
        elif entry.is_dir():
            print(f'{"Directory":10}: {entry.name}')

  ```
</details>

## Task 8
Write a program that puts ten random numbers in a file called `numbers.txt` and then reads them again. The content of the file should be separated with space and when printing the values, they should be printed as integers and not text.

```
8 5 1 7 5 7 9 5 4 2 
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import random

with open('numbers.txt', 'w') as outfile, open('numbers.txt', 'r') as infile:
    for i in range(10):
        outfile.write(str(random.randint(1, 10)) + ' ')

    outfile.close()

    content = infile.read()

    numbers = [int(x) for x in content.split()]

    for number in numbers:
        print(number, end=' ')

print()

  ```
</details>

## Task 9
Now we will return to the text "The Shadow over Innsmouth" and count the number of times the word "Dagon" appears in it. For context, Dagon -- or the "Esoteric Order of Dagon" -- was a cult described in the short story.

```
The word "Dagon" was found 13 times in the text.
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
number_of_Dagon = 0

with open('The_Shadow_over_Innsmouth.txt') as infile:

    for row in infile:
        parts = row.split()

        for part in parts:
            if 'Dagon' in part:
                number_of_Dagon += 1

print('The word "Dagon" was found', number_of_Dagon, 'times in the text.')

  ```
</details>

## Task 10
As a bonus, we are going to look at a primitive (not feature-complete) way of collecting what URLs are available on a web page. To do this, we will use the `urllib` library and the method `read()` which is very similar to reading from disk. One different thing is that we need to call `decode()` to make the content a string. From there, everything is just one long string which we need to split based on `\r\n` which is the Windows way of creating a new line. Lastly, we look at each new string in the list and see if we can identify a substring which is a link. When all is done, we print the result as well as how many links we found.

The example below is truncated a bit, as there are more than 60 links.
```
The following links where found:
https://lnu.se/" /
https://lnu.se/en/" hreflang="en" /
https://lnu.se/" hreflang="sv" /
//cdnjs.cloudflare.com" /
/clientresources/stylebundle.min.css?v=1.7.8650.24462" /
/Layout/Resources/fontawesome-6.4/css/all.min.css" /
/student/

--- A lot of rows cut ---

A total of 68 links
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import urllib.request

urls = []

with urllib.request.urlopen('https://lnu.se') as url:
    # Fetch the content and convert it to a string using decode()
    string_content = url.read().decode()

    # Split on return + newline which is often the case on Windows
    string_content = string_content.split('\r\n')

    for element in string_content:
        # Links often start with href= in HTML
        if 'href=' in element:
            # We find the start and end by searching for href= and ">
            start = element.find('href=') + 6
            end = element.find('">')
            url = element[start:end]
            # Sometimes this results in an empty string, so checking
            if url != '':
                urls.append(url)

print('The following links where found:')

for link in urls:
    print(link)

print('A total of', len(urls), 'links')

  ```
</details>

## Task 11
As another bonus, here comes an exercise about `os.path.join()`. The command makes it possible concatenate paths easily and in this task you should create a program that looks at the current working directory and lists all the different paths in the directory.

```
Possible paths:
/home/tanmsi/gittemp/pythonexempel/session4
/home/tanmsi/gittemp/pythonexempel/.vscode
/home/tanmsi/gittemp/pythonexempel/extra
/home/tanmsi/gittemp/pythonexempel/session1
/home/tanmsi/gittemp/pythonexempel/session5
/home/tanmsi/gittemp/pythonexempel/session3
/home/tanmsi/gittemp/pythonexempel/session2
```

<details>
  <summary>Expand to see the solution</summary>

  ```python
import os

path = os.getcwd()

paths = []

with os.scandir(path) as entries:
    for entry in entries:
        if entry.is_dir():
            paths.append(os.path.join(path, entry))

print('Possible paths:')

for s in paths:
    print(s)

  ```
</details>
