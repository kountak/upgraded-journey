![Logo DIT](./img/Logo.png)
#  EXCEPTIONS


### Python
Python is the most popular programming languages [(see classification here)](https://99firms.com/blog/most-popular-programming-languages/#gref). 
As in any programming language, there are situations where certain errors occur that must be managed.



### Errors and Exceptions
Error and exception handling is something you should consider in all your programs. It is obvious for a developer to encounter some errors when writing code. However, there are mainly two types of errors, built-in and user-caused.
Until now error messages haven’t been more than mentioned, but if you have tried out the examples you have probably seen some. There are (at least) two distinguishable kinds of errors: _syntax errors_ and _exceptions_

## 1. Syntax Errors
Syntax errors, also known as parsing errors, are perhaps the most common kind of complaint you get while you are still learning Python:  
**Program 1**  
``` python
while True print('Hello Word')
File "<stdin>", line 1
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
``` 
The parser repeats the offending line and displays a little ‘arrow’ pointing at the earliest point in the line where the error was detected. The error is caused by (or at least detected at) the token preceding the arrow: in the example, the error is detected at the function print(), since a colon (':') is missing before it. File name and line number are printed so you know where to look in case the input came from a script.
## 2. Exceptions : 
An exception is an event, **which occurs during the execution of a program, that disrupts the normal flow of the program's instructions**.  
In fact, Python's exception and error handling helps developers to deal with these exceptional situations by controlling the behavior of your code even in case of errors.  
Exceptions occur when exceptional situations arise in your program. For example, opening a file that doesn't exist, or stopping a running program and sometimes even a user will want to have fun by typing anything. Such situations are handled with the help of exceptions.  
Even if a statement or expression is syntactically correct, it may cause an error when an attempt is made to execute it. Errors detected during execution are called exceptions and are not unconditionally fatal: you will soon learn how to handle them in Python programs. Most exceptions are not handled by programs, however, and result in error messages as shown here:  
**Program 2**  
``` python
25 * 10/0
PS D:\Python> & C:/Users/CYRILLE/AppData/Local/Programs/Python/Python311/python.exe d:/Python/Untitled-1.py
Traceback (most recent call last):
  File "d:\Python\Untitled-1.py", line 1, in <module>
    25 *10/0
    ~~~~~~^~
ZeroDivisionError: division by zero
```

#### 2.1. Type of exceptions
There are many type of exceptions (*[see here](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)*). The most current are:

**Table 1.1  Built-in exceptions in Python**
|N°| Exceptions | Explanation |
|-| --- | ------ |
|1.|SyntaxError |It is raised when there is an error in the syntax of the Python code.|
|2.|ValueError|It is raised when a built-in method or operation receives an argument that has the right data type but mismatched or inappropriate values.|
|3.|IOError|It is raised when the file specified in a program statement cannot be opened.|
|4.|KeyboardInterrupt|It is raised when the user accidentally hits the Delete or Esc key while executing a program due to which the normal flow of the program is interrupted.|
|5.|ImportError|It is raised when the requested module definition is not found.|
|6.|EOFError |It is raised when the end of file condition is reached without reading any data by input().|
|7.| ZeroDivisionError | It is raised when the denominator in a division operation is zero. |
|8.| IndexError | It is raised when the index or subscript in a sequence is out of range. |
|9.| NameError | It is raised when a local or global variable name is not defined. |
|10.|IndentationError|It is raised due to incorrect indentation in the program code.|
|11.|TypeError|It is raised when an operator is supplied with a value of incorrect data type.|
|12.|OverFlowError|It is raised when the result of a calculation exceeds the maximum limit for numeric data type.|

#### 2.2. Syntax and Handling 
##### 2.2.1. Try....except
The most basic instruction in exception and error handling Python uses the **try** and **except** keywords to handle exceptions. Both keywords are followed by indented code blocks.  
**Program 3**  
``` python
# we tell Python to try to execute a code
# but, in case of an exception, it will have to execute another code
try:
    # try this bloc of code
except:
    # to execute on error in the try block
```
The try/except statement has another option, which is the use of the **else**. The else statement will only work if no error is generated.  
**Program 4**
``` python
dic = {"a":1, "b":2, "c":3}
try:
	val = dic["a"]
except KeyError:
	print("This key doesn't exist!")
else:
	print("It is okay!")
```
The result is :
> It is okay!


##### 2.2.2. Raise statement
The [raise](https://docs.python.org/3/reference/simple_stmts.html#raise) statement allows the programmer to force a specified exception to occur. The raise statement can be used to throw an exception. The syntax of raise statement is:   
    _raise exception-name[(optional argument)]_  
The argument is generally a string that is displayed when the exception is raised.
For example:  
**Program 5**
``` python
raise NameError('HiThere')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: HiThere
```
The sole argument to raise indicates the exception to be raised. This must be either an exception instance or an exception class (a class that derives from BaseException, such as Exception or one of its subclasses). If an exception class is passed, it will be implicitly instantiated by calling its constructor with no arguments:  
**Program 6**
``` python
raise ValueError  # shorthand for 'raise ValueError()'
```
If you need to determine whether an exception was raised but don’t intend to handle it, a simpler form of the raise statement allows you to re-raise the exception:  
**Program 7**
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
##### 2.2.3. Finally
The try statement in Python can also have an optional **_finally_** clause. The statements inside the finally block are always executed regardless of whether an exception has occurred in the try block or not. It is a common practice to use finally clause while working with files to ensure that the file object is closed. If used, finally should always be placed at the end of try clause, after all except blocks and the else block.  
**Program 8**  
``` python
print ("Handling exception using try...except...else...finally")
try:
 numerator=50
 denom=int(input("Enter the denominator: "))
 quotient=(numerator/denom)
 print ("Division performed successfully")
except ZeroDivisionError:
 print ("Denominator as ZERO is not allowed")
except ValueError:
 print ("Only INTEGERS should be entered")
else:
 print ("The result of division operation is ", quotient)
finally:
 print ("OVER AND OUT")
```
In the above program, the message “OVER AND OUT” will be displayed irrespective of whether an exception is raised or not.  

If an error has been detected in the try block and the exception has been thrown, the appropriate except block will be executed to handle the error. But if the exception is not handled by any of the except clauses, then it is re-raised after the execution of the finally block. In fact if the program contains only the except block for ZeroDivisionError so any other type of error occurs for which there is no handler code (except clause) defined, then also the finally clause will be executed first. Consider the code given in Program 9 to understand these concepts.  
**Program 9**  
``` python
print (" Practicing for try block")
try:
 numerator=50
 denom=int(input("Enter the denominator"))
 quotient=(numerator/denom)
 print ("Division performed successfully")
except ZeroDivisionError:
 print ("Denominator as ZERO is not allowed")
else:
 print ("The result of division operation is ", quotient)
finally:
 print ("OVER AND OUT")
```
While executing the above code, if we enter a non-numeric data as input, the finally block will be executed. So, the message “OVER AND OUT” will be displayed. Thereafter the exception for which handler is not present will be re-raised. The output of Program 9 is shown in the next Figure.  


![Finally1](D:/Python/upgraded-journey/img/Finally1.png)  


After execution of finally block, Python transfers the control to a previously entered try or to the next higher level default exception handler. In such a case, the statements following the finally block is executed. That is, unlike except, execution of the finally clause does not terminate the exception. Rather, the exception continues to be raised after execution of finally. To summarise, we put a piece of code where there are possibilities of errors or exceptions to occur inside a try block. Inside each except clause we define handler codes to handle the matching exception raised in the try block. The optional else clause contains codes to be executed if no exception occurs. The optional finally block contains codes to be executed irrespective of whether an exception occurs or not.

#### 2.3. Raising and Handling Multiple Unrelated Exceptions
There are situations where it is necessary to report several exceptions that have occurred. This is often the case in concurrency frameworks, when several tasks may have failed in parallel, but there are also other use cases where it is desirable to continue execution and collect multiple errors rather than raise the first exception.  

The builtin ExceptionGroup wraps a list of exception instances so that they can be raised together. It is an exception itself, so it can be caught like any other exception.  
**Program 10**
``` python
def f():
    excs = [OSError('error 1'), SystemError('error 2')]
    raise ExceptionGroup('there were problems', excs)
f()
  + Exception Group Traceback (most recent call last):
  |   File "<stdin>", line 1, in <module>
  |   File "<stdin>", line 3, in f
  | ExceptionGroup: there were problems
  +-+---------------- 1 ----------------
    | OSError: error 1
    +---------------- 2 ----------------
    | SystemError: error 2
    +------------------------------------
try:
    f()
except Exception as e:
    print(f'caught {type(e)}: e')

caught <class 'ExceptionGroup'>: e
```
By using except* _instead of except_, we can selectively handle only the exceptions in the group that match a certain type. In the following example, which shows a nested exception group, each except* clause extracts from the group exceptions of a certain type while letting all other exceptions propagate to other clauses and eventually to be reraised.  
**Program 11**  
``` python
def f():
    raise ExceptionGroup("group1",
                         [OSError(1),
                          SystemError(2),
                          ExceptionGroup("group2",
                                         [OSError(3), RecursionError(4)])])

try:
    f()
except* OSError as e:
    print("There were OSErrors")
except* SystemError as e:
    print("There were SystemErrors")

There were OSErrors
There were SystemErrors
  + Exception Group Traceback (most recent call last):
  |   File "<stdin>", line 2, in <module>
  |   File "<stdin>", line 2, in f
  | ExceptionGroup: group1
  +-+---------------- 1 ----------------
    | ExceptionGroup: group2
    +-+---------------- 1 ----------------
      | RecursionError: 4
      +------------------------------------
```

#### 2.4. Custom exceptions 
When an exception is created in order to be raised, it is usually initialized with information that describes the error that has occurred. There are cases where it is useful to add information after the exception was caught. For this purpose, exceptions have a method add_note(note) that accepts a string and adds it to the exception’s notes list. The standard traceback rendering includes all notes, in the order they were added, after the exception.  
**Program 12**  
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
**Program 13**
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
## Alternatives : 
 One alternative is using of **if** statement for handling errors.  

 
 
## Cases related to data analysis :
Error management is essential and even crucial in data analysis. The data analyst is faced with these problems in the daily management of databases. Indeed, whether more or less strict controls are made on the different entries, the databases contain many missing values, outliers or values whose type is different from the type of other values. This creates errors and exceptions that must be managed in order to have a more or less clean database to be used for analysis or training of deep learning models.  

> ## Summary
> - Syntax errors or parsing errors are detected when we have not followed the rules of the particular programming language while writing a program.
> - When syntax error is encountered, Python displays the name of the error and a small description about the error.
> - The execution of the program will start only after the syntax error is rectified.
> - An exception is a Python object that represents an error.
> - Syntax errors are also handled as exceptions.
> - The exception needs to be handled by the programmer so that the program does not
terminate abruptly.
> - When an exception occurs during execution of a program and there is a built-in exception defined for that, the error message written in that exception is displayed. The programmer then has to take appropriate action and handle it. 
> - Some of the commonly occurring built-in exceptions are **_SyntaxError, ValueError, IOError, KeyboardInterrupt, ImportError, EOFError, ZeroDivisionError, IndexError, NameError, IndentationError, TypeError,and OverFlowerror_**.
> - When an error is encountered in a program, Python interpreter raises or throws an exception.
> - Exception Handlers are the codes that are designed to execute when a specific exception is raised.
> - Raising an exception involves interrupting the normal flow of the program execution and jumping to the exception handler.
> - Raise and assert statements are used to raise exceptions. The process of exception handling involves writing additional code to give proper messages or instructions to the user. This prevents the program from crashing abruptly. The additional code is known as an exception handler.
> - An exception is said to be caught when a code that is designed to handle a particular exception is executed.
> - An exception is caught in the try block and handles in except block.
> - The statements inside the finally block are always executed regardless of whether an exception occurred in the try block or not.  

 


## Related articles
[Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
[ZeroDivisionError](https://docs.python.org/3/library/exceptions.html#ZeroDivisionError)   
[Finally clause](https://docs.python.org/3/reference/compound_stmts.html#finally)  
[Errors and exceptions management in Python Python-Mostly use cases courants](https://pythonforge.com/gestion-des-erreurs-et-des-exceptions-python/)  
[NameError](https://docs.python.org/3/library/exceptions.html#NameError)  
[TypeError](https://docs.python.org/3/library/exceptions.html#TypeError)  
[Python | Catching the ball game](https://www.geeksforgeeks.org/python-catching-and-creating-exceptions/?ref=rp)  







