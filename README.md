![Logo DIT](./img/Logo.png)
#  EXCEPTIONS 


## Main Concepts
### Python
#### Origin
#### Market Shares
![Python is third most used langage](./img/Market_Share.png "Most used programming languages among developers worldwide as of 2022")
#### Mostly use cases

### Errors and Exceptions
Error and exception handling is something you should consider in all your programs. It is obvious for a developer to encounter some errors when writing code. However, there are mainly two types of errors, built-in and user-caused.
Until now error messages haven’t been more than mentioned, but if you have tried out the examples you have probably seen some. There are (at least) two distinguishable kinds of errors: _syntax errors_ and _exceptions_

#### Syntax Errors
Syntax errors, also known as parsing errors, are perhaps the most common kind of complaint you get while you are still learning Python:
``` python
while True print('Hello Word')
File "<stdin>", line 1
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
``` 
The parser repeats the offending line and displays a little ‘arrow’ pointing at the earliest point in the line where the error was detected. The error is caused by (or at least detected at) the token preceding the arrow: in the example, the error is detected at the function print(), since a colon (':') is missing before it. File name and line number are printed so you know where to look in case the input came from a script.
### Exceptions : 
An exception is an event, **which occurs during the execution of a program, that disrupts the normal flow of the program's instructions**.
In fact, Python's exception and error handling helps developers to deal with these exceptional situations by controlling the behavior of your code even in case of errors.
Exceptions occur when exceptional situations arise in your program. For example, opening a file that doesn't exist, or stopping a running program and sometimes even a user will want to have fun by typing anything. Such situations are handled with the help of exceptions.
Even if a statement or expression is syntactically correct, it may cause an error when an attempt is made to execute it. Errors detected during execution are called exceptions and are not unconditionally fatal: you will soon learn how to handle them in Python programs. Most exceptions are not handled by programs, however, and result in error messages as shown here:
``` python
25 * 10/0
```

#### Type of exceptions
There are many type of exceptions (*[see here](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)*). The most current are 
- [*ZeroDivisionError*](https://docs.python.org/3/library/exceptions.html#ZeroDivisionError) : when you try to divide a number by zero
- [*NameError*](https://docs.python.org/3/library/exceptions.html#NameError) : when a local or global name cannot be found
- [*TypeError*](https://docs.python.org/3/library/exceptions.html#TypeError)

#### Syntax and Handling 
##### Try....except
The most basic instruction in exception and error handling Python uses the **try** and **except** keywords to handle exceptions. Both keywords are followed by indented code blocks.
``` python
# we tell Python to try to execute a code
# but, in case of an exception, it will have to execute another code
try:
    # try this bloc of code
except:
    # to execute on error in the try block
```
The try/except statement has another option, which is the use of the **else**. The else statement will only work if no error is generated.
``` python
try:
	val = dic["a"]
except KeyError:
	print("This key doesn't exist!")
else:
	print("It is okay!")
```
The result is :

##### Raise statement
The [raise](https://docs.python.org/3/reference/simple_stmts.html#raise) statement allows the programmer to force a specified exception to occur. For example:
``` python
raise NameError('HiThere')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: HiThere
```
The sole argument to raise indicates the exception to be raised. This must be either an exception instance or an exception class (a class that derives from BaseException, such as Exception or one of its subclasses). If an exception class is passed, it will be implicitly instantiated by calling its constructor with no arguments:
``` python
raise ValueError  # shorthand for 'raise ValueError()'
```
If you need to determine whether an exception was raised but don’t intend to handle it, a simpler form of the raise statement allows you to re-raise the exception:
``` python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    raise

An exception flew by!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
NameError: HiThere
```
##### Finally


#### Custom exceptions 
When an exception is created in order to be raised, it is usually initialized with information that describes the error that has occurred. There are cases where it is useful to add information after the exception was caught. For this purpose, exceptions have a method add_note(note) that accepts a string and adds it to the exception’s notes list. The standard traceback rendering includes all notes, in the order they were added, after the exception.
``` python
try:
    raise TypeError('bad type')
except Exception as e:
    e.add_note('Add some information')
    e.add_note('Add some more information')
    raise

Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
TypeError: bad type
Add some information
Add some more information
```
For example, when collecting exceptions into an exception group, we may want to add context information for the individual errors. In the following each exception in the group has a note indicating when this error has occurred.
``` python
def f():
    raise OSError('operation failed')
excs = []
for i in range(3):
    try:
        f()
    except Exception as e:
        e.add_note(f'Happened in Iteration {i+1}')
        excs.append(e)

raise ExceptionGroup('We have some problems', excs)
  + Exception Group Traceback (most recent call last):
  |   File "<stdin>", line 1, in <module>
  | ExceptionGroup: We have some problems (3 sub-exceptions)
  +-+---------------- 1 ----------------
    | Traceback (most recent call last):
    |   File "<stdin>", line 3, in <module>
    |   File "<stdin>", line 2, in f
    | OSError: operation failed
    | Happened in Iteration 1
    +---------------- 2 ----------------
    | Traceback (most recent call last):
    |   File "<stdin>", line 3, in <module>
    |   File "<stdin>", line 2, in f
    | OSError: operation failed
    | Happened in Iteration 2
    +---------------- 3 ----------------
    | Traceback (most recent call last):
    |   File "<stdin>", line 3, in <module>
    |   File "<stdin>", line 2, in f
    | OSError: operation failed
    | Happened in Iteration 3
    +------------------------------------
```
 
Exemple pratique :

Potentielles alternatives : 
 
Cas d’utilisation concrets en rapport avec l’analyse de données :
