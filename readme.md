# Learn programming by Python

## WSL
Windows Subsystem for Linux([WSL](https://docs.microsoft.com/en-us/windows/wsl/about)) is an environment in Windows 10 for running unmodified Linux binaries.

### How to enable
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
> [!IMPORTANT]
> This command require administrative priviledge

### How install Ubuntu 
Download one of these and install it:
- [Ubuntu 16.04 LTS](https://www.microsoft.com/en-us/p/ubuntu-1604/9pjn388hp8c9)
- [Ubuntu 18.04 LTS](https://www.microsoft.com/en-us/p/ubuntu-1804/9n9tngvndl3q)
- [Ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6)

## How install python

### From store
```bash
sudo apt install python3.7
```

### From Source
```bash
sudo -i
apt update -y
apt install -y \
    wget \
    build-essential \
    libffi-dev \
    libgdbm-dev \
    libc6-dev \
    libssl-dev \
    zlib1g-dev \
    libbz2-dev \
    libreadline-dev \
    libsqlite3-dev \
    libncurses5-dev \
    libncursesw5-dev \
    xz-utils \
    tk-dev

cd /usr/src
PYTHON_VERSION=3.8.1
wget http://python.org/ftp/python/$PYTHON_VERSION/Python-$PYTHON_VERSION.tar.xz
tar xf Python-$PYTHON_VERSION.tar.xz
cd Python-$PYTHON_VERSION
./configure --enable-optimizations
make altinstall
exit
```
> [!IMPORTANT]
> make altinstall causes it to not replace the built in python executable.

### Upgrade pip
```bash
pip3.8 install --upgrade pip
```

## Select Text Editor or IDE
Having a well configured text editor can make the programming experience much more enjoyable. Much like a carpenter, having sharp tools leads to a more productive creative experience.

### Terminal based editors
- [Vim](https://www.vim.org/)
- [Emacs](https://www.gnu.org/software/emacs/)
- [Nano](https://www.nano-editor.org/)

### GUI Based Editors
- [Atom](https://atom.io/)
- [VS Code](https://code.visualstudio.com/)

    Suggested extensions(VS Code offer extensions as you keep using it):
    - [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)

        > [!IMPORTANT]
        > This extension is required in order to work with `WSL`
    - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
    - [GitLens — Git supercharged](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
    - [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
- [SublimeText](https://www.sublimetext.com/)
- [Notepad++](https://notepad-plus-plus.org/)
- [PyCharm](https://www.jetbrains.com/pycharm/)

## REPL

### What is REPL?
REPL stands for: **R**ead, **E**valuate, **P**rint, **L**oop

Each line is read and evaluated. The return value is then printed to the screen, and then the process repeats.

Python ships with a REPL, accessible by running python3.8 from a terminal.

### Using REPL
The `>>>` indicates a line to type in, like a command prompt for Python. Later on we'll see a ..., which means that we are currently sitting in a scoped area. The only way out is to enter a blank line (no spaces) before the interpreter will evaluate the entire code block.

The simplest use of this would be to do some math:
```python
>>> 1 + 1
2
>>>
```

2 is the return value of the expression and it is then printed to the screen. If something doesn't have a return value, then nothing will be printed to the screen and we'll just land back at a `>>>` prompt. We'll cover this later, but an example would be `None`:
```python
>>> None
>>>
```

To exit the REPL, we can either type `exit()` (the parentheses are important) or hit `Ctrl+d` on your keyboard.

## Git

### What is Git?
Git is a Distributed Version Control Systems(DVCS) to records changes to a file or set of files over time so that you can recall specific versions later.

### Usefull commands
[git clone](https://git-scm.com/docs/git-clone): Clone a git repository to local file system.

[git pull](https://git-scm.com/docs/git-pull): Get changes from the server and merge them with your local copy.

[git status](https://git-scm.com/docs/git-status): Show the working tree status.

[git checkout](https://git-scm.com/docs/git-checkout): Switch branches or restore working tree files.

[git add](https://git-scm.com/docs/git-add): This command updates the index using the current content found in the working tree, to prepare the content staged for the next commit.

[git commit](https://git-scm.com/docs/git-commit): Commit your changes to local git repository.

[git push](https://git-scm.com/docs/git-push): Update remote refs along with associated objects.

## Basics of programming
Writing a program is the art of breaking the problem into small blocks of tasks that work in cooperation with each other to achieve a bigger task and provide a useful service.

### Using comments
Writing a simple program is easy enough, but writing a good program that provide a service for a long time require some skill and to comply with some rule.

Writing a program for an actual useful problem, require many services. And over time many of this services will change. New services will added to the list of required service, some old services will be removed and some of them will be changed.

It is not always the same person that work on a piece of code, so we should write codes in a way that someone else may understand them at a later time. One of the easiest and most efficient ways to express our intention of writing a code is comment, one or two lines of code that describe our intention.

Comments in python start with `#` and continue till the end of the line.
```python
# This is a full line comment
print("Hello user!")    # Great user of the program
```

### Python basic types
#### Strings
Strings are a sequence of characters. In python they will be called [str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-strl).
They may be quoted with `'` or `"`. There is no difference in using each one of these but internally python will use `'` to represent strings.
```python
>>> 'single quoted string'
'single quoted string'
>>> "double quoted string"
'double quoted string'
>>> print('"double quote" in single quoted string')
"double quote" in single quoted string
>>> print("'single quote' in double quoted string")
'single quote' in double quoted string
```

In order to write long strings that span multiple lines you may use triple quote, either `'''` or `"""`
```python
>>>'''This is line 1 of the string
... This is line 2
... And line3'''
'This is line of the string\nThis is line 2\nAnd line3'
```

In order to write special characters in middle of an string literal we use an escape character. In python this special character is backslash: `\`. Any time that python see `\\` in middle of an string literal it will lookup next character(s) to identify the single character that you wanted to use.
In order to write `\` in a middle of an string you must use `\\`.
```python
>>> print('single quote(\') in middle of single quoted(\') string')
single quote ' in middle of single quoted(') string
>>> print("double quote(\") in middle of double quoted(\") string") 
double quote " in middle of double quoted(") string
>>> print("New\nLine")
New
Line
>>> print('Tab\tdelimited')
Tab    delimited
>>> print('Backslash\\ In middle of an string literal')
Backslash\ In middle of an string literal
```

There are a bunch of operations that you can do with strings
```python
>>> 'Hello ' + 'World!'
'Hello World!'
>>> 3 * '!'
'!!!'
>>> '!' * 3
'!!!'
>>> 'Hello ' + 'World' + 3 * '!'
'Hello World!!!'
```

String also have many useful methods:
```python
>>> # Methods to change case of the letters
...
>>> 'test'.upper() # TEST
'TEST'
>>> 'TesT'.upper() # TEST
'TEST'
>>> 'Test'.lower() # test
'test'
>>> 'test'.capitalize() # Test
'Test'
>>> # Methods to search for substrings
...
>>> 'test'.find('e')
1
>>> 'test'.find('st')
2
>>> 'test'.find('T')
-1
```
> [!IMPORTANT]
> In python string literals are **immutable** and you can't change them.

#### Numbers
There are to main types of numbers we'll use in Python: [`int` and `float`](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex). For the most part, we won't be calling methods on number types — instead, we will use a variety of operators.
```python
>>> 2 + 2 # Addition
4
>>> 10 - 4 # Subtraction
6
>>> 3 * 9 # Multiplication
27
>>> 5 / 3 # Division
1.66666666666667
>>> 5 // 3 # Floor division, always returns a number without a remainder
1
>>> 8 % 3 # Modulo division, returns the remainder
2
>>> 2 ** 3 # Exponent
8
```

If either of the numbers in a mathematical operation in Python is a `float`, then the other will be converted before carrying out the operation and the result will always be a `float`.
```python
>>> 2 + 3.0
5.0
>>> 2 * 3.0
6.0
```

##### Converting Strings and Numbers
It's not uncommon for us to need to convert from one type to another when writing a script. Python provides built-in functions for doing that with the built-in types. For strings and numbers, we can use the `str`, `int`, and `float` functions to convert from one type to another (within reason).
```python
>>> str(1.1)
'1.1'
>>> int("10")
10
>>> int(5.99999)
5
>>> float("5.6")
5.6
>>> float(5)
5.0
```

You'll run into issues trying to convert strings to other types if they aren't present in the string.
```python
>>> float("1.1 things")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: could not convert string to float: '1.1 things'
```

#### Boolean and None
Python way of representing truthiness and nothingness is [`bool` and `None`](https://docs.python.org/3/library/stdtypes.html#truth-value-testing).

##### Boolean
`bool` represent **truthiness** and Python has two boolean constants: `True` and `False`.

Notice that these both start with capital letters. Later we will learn about comparisons operations, and those will often return either `True` or `False`.

##### Representing Nothingness with `None`
Most programming languages have a type that represents the lack of a value, and Python is no different. The constant used to represent nothingness in Python is `None`. `None` is a **falsy**, and we'll often use it to represent when a variable has no value yet.

An interesting thing to note about `None` is that if you type `None` into your REPL there will be nothing printed to the screen. That's because `None` actually evaluates into nothing.

#### Working with variables
Almost any script we write will need to have a way for us to hold on to information for use later on. That's where variables come into play.

We can assign a value to a variable by using a single `=` and we don't need to (nor can we) specify the type of the variable.
```python
>>> my_var = "This is a simple string"
```
Now we can print the value of that string by using *my_var* later on:
```python
>>> print(my_var)
This is a simple string
>>> print(my_var + '.')
This is a simple string.
```

Before, we talked about how we can't change a string because it's immutable. This is easier to see now that we have variables.
```python
>>> my_var += " testing"
>>> my_var
'This is a simple string testing'
```

That didn't change the string — it reassigned the variable. The original string of `"This is a simple string"` was unchanged.

An important thing to realize is that the contents of a variable can be changed, and we don't need to maintain the same type.
```python
>>> my_str = 'test'
>>> my_str = 1
>>> print(my_str)
1
```
Ideally, we wouldn't change the contents of a variable called `my_str` to be an `int`, but it is something that Python would let us do.

One last thing to remember about variables is that they are just a name for an object. If you create a new variable and assign it to an old variable, then both of them are the names of the same object and we can use both names to reach to same object.
If we reassign any of the variables to another object, we just use this name for another object and old variable will remain the name of the old object.
```python
>>> my_str = 1
>>> my_int = my_str
>>> my_str = "testing"
>>> print(my_int)
1
>>> print(my_str)
testing
```
But if you use any function that modify the object itself, then you can see the change but any of the name
```python
>>> name1 = [1, 2, 3]
>>> name2 = name1
>>> id(name1) # This will be different in each execution of the script. but it will remain constant while it name the same object.
140168663471048
>>> id(name2) # This will also be a different value in each execution but have the same value as id(name1) because both of them name the same object for now
140168663471048
>>> name2
[1, 2, 3]
>>> name1.pop()
3
>>> name2
[1, 2]
>>> name1 += [3, 4]
>>> id(name1) # Note that object is not changed
140168663471048
>>> name2
[1, 2, 3, 4]
>>> name1 = [4, 5]
>>> id(name1)
140168663473224
>>> name2
[1, 2]
```
In case of immutable objects, even when we think we have changed the object, actually python have created another object for us and replaced the original object with it.
```python
>>> my_str = "This"
>>> id(my_str)
140168663441848
>>> my_str += ' is'
>>> id(my_str)    # Note that id is changed, so name `my_str` now point to a different object.
140168663441960
```

One last thing to remember is that if we assign a variable with another variable it will be assigned to the result of the variable and not whatever that varible points to later.
```python
>>> my_str = 1
>>> my_int = my_str
>>> my_str = "testing"
>>> print(my_int)
1
>>> print(my_str)
testing
```

#### Lists
In Python, there are a few different [sequence](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range) types that we're going to work with, the most common of which being the [list](https://docs.python.org/3/library/stdtypes.html#list) type.
A list is created in Python by using the square brackets ([, and ]) and separating the values by commas. Here's an example list:
```python
>>> my_list = [1, 2, 3, 4, 5]
```
There's really not a limit to how long our list can be (there is, but it's very unlikely that we'll hit it while scripting)

##### Reading from Lists
To access an individual element of a `list` you can use the index and Python uses a zero based index system.
```python
>>> my_list[0]
1
>>> my_list[2]
3
```
If we try to access an index that is too high (or too low) then we'll receive an error:
```python
>>> my_list[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```
To make sure that we're not trying to get an index that is out of range, we can test the length using the `len` function (and then subtract 1)
```python
>>> len(my_list)
5
```
Additionally, we can access subsections of a list by **"slicing"** it. We provide the starting index and the ending index (the object at that index won't be included).
```python
>>> my_list[0:2]
[1, 2]
>>> my_list[1:]
[2, 3, 4, 5]
>>> my_list[:3]
[1, 2, 3]
>>> my_list[0::1]
[1, 2, 3, 4, 5]
>>> my_list[0::2]
[1, 3, 5]
```

##### Modifying a List
Unlike strings which can't be modified (you can't change a character in a string), you can change a value in a `list` using the subscript equals operation:
```python
>>> my_list[0] = "a"
>>> my_list
['a', 2, 3, 4, 5]
```
If we want to add to a list we can use the `.append` method. This is an example of a method that modifies the object that is calling the method:
```python
>>> my_list.append(6)
>>> my_list.append(7)
>>> my_list
['a', 2, 3, 4, 5, 6, 7]
```
Lists can be added together (concatenated):
```python
>>> my_list + [8, 9, 10]
['a', 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> my_list += [8, 9, 10]
>>> my_list
['a', 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
Items in lists can be set using slices also:
```python
>>> my_list[1:3] = ['b', 'c']
>>> my_list
['a', 'b', 'c', 4, 5, 6, 7, 8, 9, 10]
# Replacing 2 sized slice with length 3 list inserts new element
>>> my_list[3:5] = ['d', 'e', 'f']
>>> print(my_list)
['a', 'b', 'c', 'd', 'e', 'f', 6, 7, 8, 9, 10]
>>> len(my_list)
11
```
We can remove a section of a `list` by assigning an empty `list` to the slice:
```python
>>> my_list = ['a', 'b', 'c', 'd', 5, 6, 7]
>>> my_list[4:] = []
>>> my_list
['a', 'b', 'c', 'd']
```
Removing items from a `list` based on value can be done using the `.remove` method:
```python
>>> my_list.remove('b')
>>> my_list
['a', 'c', 'd']
```
Attempting to remove and item that isn't in the `list` will result in an error:
```python
>>> my_list.remove('f')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list
```
Items can also be removed from the end of a list using the `pop` method:
```python
>>> my_list = ['a', 'c', 'd']
>>> my_list.pop()
'd'
>>> my_list
['a', 'c']
```
We can also use the `pop` method to remove items at a specific index:
```python
>>> my_list.pop(0)
'a'
>>> my_list
['c']
>>> my_list.pop(1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: pop index out of range
>>> [].pop()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: pop from empty list
```

#### Tuples and Ranges
The most common immutable [sequence type](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range) that we're going to work with is going to be the [tuple](https://docs.python.org/3/library/stdtypes.html#tuple). We'll also look at the [range](https://docs.python.org/3/library/stdtypes.html#range) type as an alternative to a sequential [list](https://docs.python.org/3/library/stdtypes.html#list).

##### Tuples
Tuples are a fixed-width, immutable sequence type. We create tuples using parenthesis (`(`, `)`) and at least one comma (,):
```python
>>> point = (2.0, 3.0)
```
Since tuples are immutable, we don't have access to the same methods that we do on a list. We can use tuples in some operations like concatenation, but we can't change the original tuple that we created.
```python
>>> point_3d = point + (4.0,)
>>> point_3d
(2.0, 3.0, 4.0)
```
One interesting characteristic of tuples is that we can unpack them into multiple variables at the same time:
```python
>>> x, y, z = point_3d
>>> x
2.0
>>> y
3.0
>>> z
4.0
```
The time we're most likely to see tuples will be when looking at a format string that's compatible with Python 2:
```python
>>> print("My name is: %s %s" % ("Mohammad Mahdi", "Roozitalab"))
My name is: Mohammad Mahdi Roozitalab
```

##### Ranges
Ranges are an immutable sequence type that defines a start, a stop, and a step value, and then the values within are calculated as it is interacted with. This allows for ranges to be used in place of sequential lists and while taking less memory and including more items.
```python
>>> my_range = range(10)
>>> my_range
range(0, 10)
>>> list(my_range)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> list(range(1, 14, 2))
[1, 3, 5, 7, 9, 11, 13]
```
Notice that the "stop" value is not included in the range, the values are all up-until the stop.

#### Dictionaries
We will use [dict](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) type to hold onto key/value information in Python.

[dict](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) is the main mapping type that we'll use in Python. This object is comparable to a Hash or "associative array" in other languages.
We will use it to hold onto key/value information in Python.

We create dictionary literals by using curly braces (`{` and `}`), separating keys from values using colons (`:`), and separating key/value pairs using commas (`,`). Here's an example dictionary:
```python
>>> ages = { 'kevin': 59, 'alex': 29, 'bob': 40 }
>>> ages
{'kevin': 59, 'alex': 29, 'bob': 40}
```
We can read a value from a dictionary by subscripting using the key:
```python
>>> ages['kevin']
59
>>> ages['billy']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'billy'
```
Keys can be added and their value may be changed using subscripting and assignment:
```python
>>> ages['kayla'] = 21
>>> ages
{'kevin': 59, 'alex': 29, 'bob': 40, 'kayla': 21}
```
Items can be removed from a dictionary using the `del` statement or by using the `pop` method:
```python
>>> del ages['kevin']
>>> ages
{'alex': 29, 'bob': 40, 'kayla': 21}
>>> del ages
>>> ages
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'ages' is not defined
>>> ages = { 'kevin': 59, 'alex': 29, 'bob': 40 }
>>> ages.pop('alex')
29
>>> ages
{'kevin': 59, 'bob': 40}
>>> {}.pop('billy')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'billy'
```
Since this is our second time running into a `KeyError` it's worth looking at a way to avoid these when we're attempting to read data from a dictionary. For that, we can use the get method:
```python
>>> ages.get('kevin')
59
>>> ages.get('billy')
>>>
```
Now we're receiving `None` instead of raising an error when we try to get the value for a key that doesn't exist.

It's not uncommon to want to know what keys or values we have without caring about the pairings. For that situation we have the `values` and `keys` methods:
```python
>>> ages = {'kevin': 59, 'bob': 40}
>>> ages.keys()
dict_keys(['kevin', 'bob'])
>>> list(ages.keys())
['kevin', 'bob']
>>> ages.values()
dict_values([59, 40])
>>> list(ages.values())
[59, 40]
```

##### Alternative ways to create a `dict` using Keyword Arguments
There are a few other ways to create dictionaries that we might see, those being using the `dict` constructor with key/value arguments and a list of tuples:
```python
>>> weights = dict(kevin=160, bob=240, kayla=135)
>>> weights
{'kevin': 160, 'bob': 240, 'kayla': 135}
>>> colors = dict([('kevin', 'blue'), ('bob', 'green'), ('kayla', 'red')])
>>> colors
{'kevin': 'blue', 'bob': 'green', 'kayla': 'red'}
```

##### Things to note about dictionaries:
- Unlike Python 2 dictionaries, as of Python 3.6 keys are ordered in dictionaries. Will need `OrderedDict` if you want this to work on another version of Python.
- You can set the key to any **IMMUTABLE** type (so no `list`)
- Avoid using things other than simple objects as keys.
- Each key can only have one value (so don't have duplicates when creating a `dict`)

### Control flow
#### Conditionals and Comparisons
Scripts become most interesting when they do the right thing based on the inputs that we provide. To start building robust scripts, we need to understand how to make [comparisons](https://docs.python.org/3/library/stdtypes.html#comparisons) and use [conditional blocks](https://docs.python.org/3/tutorial/controlflow.html#if-statements).

##### Comparisons
There are some standard comparison operators that we'll use that match pretty closely to those used in mathematical equations. Let's take a look at them:
```python
>>> 1 < 2
True
>>> 0 > 2
False
>>> 2 == 1
False
>>> 2 != 1
True
>>> 3.0 >= 3.0
True
>>> 3.1 <= 3.0
False
```
If we try to make comparisons of types that don't match up, we will run into errors:
```python
>>> 3.1 <= "this"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: '<=' not supported between instances of 'float' and 'str'
>>> 3 <= 3.1
True
>>> 1.1 == "1.1"
False
>>> 1.1 == float("1.1")
True
```
We can compare more than just numbers. Here's what it looks like when we compare strings:
```python
>>> "this" == "this"
True
>>> "this" == "This"
False
>>> "b" > "a"
True
>>> "abc" < "b"
True
```
Notice that the string 'b' is considered greater than the strings 'a' and 'abc'. The characters are compared one at a time alphabetically to determine which is greater. This concept is used to sort strings alphabetically.

##### The `in` Check
We often get lists of information that we need to ensure contains (or doesn't contain) a specific item. To make this check in Python, we'll use the `in` and `not in` operations.
```python
>>> 2 in [1, 2, 3]
True
>>> 4 in [1, 2, 3]
False
>>> 2 not in [1, 2, 3]
False
>>> 4 not in [1, 2, 3]
True
```

##### Conditional blocks: if/elif/else
With a grasp on comparisons, we can now look at how we can run different pieces of logic based on the values that we're working with using conditionals. The keywords for conditionals in Python are `if`, `elif`, and `else`. Conditionals are the first language feature that we're using that requires us to utilize whitespace to separate our code blocks. In this document we will always use indentation of 4 spaces. The basic shape of an `if` statement is this:
```python
if CONDITION:
    pass
```
The *CONDITION* portion can be anything that evaluates to `True` or `False`, and if the value isn't explicitly a boolean then it will be converted to determine how to carry out proceed past the conditional (basically using the `bool` constructor).
```python
>>> if True:
...     print("Was True")
...
Was True
>>> if False:
...     print("Was True")
...
>>>
```
To add an alternative code path, we'll use the `else` keyword, followed by a colon (:), and indenting the code underneath:
```python
>>> if False:
...     print("Was True")
... else:
...     print("Was False")
...
Was False
```
In the even that we want to check multiple potential conditions we can use the `elif CONDITION:` statement. Here's a more robust example:
```python
>>> name = "Kevin"
>>> if len(name) >= 6:
...     print("name is long")
... elif len(name) == 5:
...     print("name is 5 characters")
... elif len(name) >= 4:
...     print("name is 4 or more")
... else:
...     print("name is short")
...
name is 5 characters
```
Notice that we fell into the first `elif` statement's block and then the second `elif` block was never executed even though it was true. We can only exercise one branch in an if statement.

#### Logic Operations
Up to this point, we've learned how to make simple comparisons, and now it's time to make compound comparisons using logic/boolean operators.

##### [Boolean Operators](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not)
###### The `not` Operation
Sometimes we want to know the opposite boolean value for something. This might not sound intuitive, but sometimes we want to execute an `if` statement when a value is `False`, but that's not how the `if` statement works. Here's an example of how we can use not to make this work:
```python
>>> name = ""
>>> not name
True
>>> if not name:
...     print("No name given")
...
No name given
>>>
```
We know that an empty string is a "falsy" value, so `not ""` will always return `True`. `not` will return the opposite boolean value for whatever it's operating on.

###### The `or` Operation
Occasionally, we want to carry out a branch in our logic if one condition *OR* the other condition is `True`. Here is where we'll use the `or` operation. Let's see `or` in action with an `if` statement:
```python
>>> first = ""
>>> last = "Thompson"
>>> if first or last:
...     print("The user has a first or last name")
...
The user has a first or last name
>>>
```
If both first and last were "falsy" then the print would never happen:
```python
>>> first = ""
>>> last = ""
>>> if first or last:
...     print("The user has a first or last name")
...
>>>
```
Another feature of `or` that we should know is that we can use it to set default values for variables:
```python
>>> last = ""
>>> last_name = last or "Doe"
>>> last_name
'Doe'
>>>
```
The `or` operation will return the first value that is "truthy" or the last value in the chain:
```python
>>> 0 or 1
1
>>> 1 or 2
1
```
###### The `and` Operation
The opposite of `or` is the `and` operation, which requires both conditions to be `True`. Continuing with our first and last name example, let's conditionally print based on what we know:
```python
>>> first = "Keith"
>>> last = ""
>>> if first and last:
...     print(f"Full name: {first} {last}")
... elif first:
...     print(f"First name: {first}")
... elif last:
...     print(f"Last name: {last}")
...
First name: Keith
>>>
```
Now let's try the same thing with both first and last:
```python
>>> first = "Keith"
>>> last = "Thompson"
>>> if first and last:
...     print(f"Full name: {first} {last}")
... elif first:
...     print(f"First name: {first}")
... elif last:
...     print(f"Last name: {last}")
...
Full name: Keith Thompson
>>>
```
The and operation will return the first value that is "falsy" or the last value in the chain:
```python
>>> 0 and 1
0
>>> 1 and 2
2
>>> (1 == 1) and print("Something")
Something
>>> (1 == 2) and print("Something")
False
```

#### Loops
It's incredibly common to need to repeat something a set number of times or to iterate over content. Here is where looping and iteration come into play.

##### [The `while` loop](https://docs.python.org/3/tutorial/introduction.html#first-steps-towards-programming)
The most basic type of loop that we have at our disposal is the `while` loop. This type of loop repeats itself based on a condition that we pass to it. Here's the general structure of a `while` loop:
```python
while CONDITION:
    pass
```
The *CONDITION* in this statement works the same way that it does for an `if` statement. When we demonstrated the `if` statement we first tried it by simply passing in `True` as the condition. Let's see when we try that same condition with a while loop:
```python
>>> while True:
...     print("looping")
...
looping
looping
looping
looping
```
That loop will continue forever, we've created an infinite loop. To stop the loop, press *Ctrl-C*. Infinite loops are one of the potential problems with `while` loops if we don't use a condition that we can change from within the loop then it will continue forever if initially true. Here's how we'll normally approach using a `while` loop where we modify something about the condition on each iteration:
```python
>>> count = 1
>>> while count <= 4:
...     print("looping")
...     count += 1
...
looping
looping
looping
looping
>>>
```
We can use other loops or conditions inside of our loops; we need only remember to indent four more spaces for each context. If in a nested context we want to continue to the next iteration or stop the loop entirely we also have access to the `continue` and `break` keywords:
```python
>>> count = 0
>>> while count < 10:
...     if count % 2 == 0:
...         count += 1
...         continue
...     print(f"We're counting odd numbers: {count}")
...     count += 1
...
We're counting odd numbers: 1
We're counting odd numbers: 3
We're counting odd numbers: 5
We're counting odd numbers: 7
We're counting odd numbers: 9
>>>
```
In that example, we also show off how to "string interpolation" in Python 3 by prefixing a string literal with an `f` and then using curly braces to substitute in variables or expressions (in this case the *count* value).

Here's an example using the `break` statement:
```python
>>> count = 1
>>> while count < 10:
...     if count % 2 == 0:
...         break
...     print(f"We're counting odd numbers: {count}")
...     count += 1
...
We're counting odd numbers: 1
```

##### [The `for` Loop](https://docs.python.org/3/tutorial/controlflow.html#for-statements)
The most common use we have for looping is when we want to execute some code for each item in a sequence. For this type of looping or iteration, we'll use the `for` loop. The general structure for a `for` loop is:
```python
for TEMP_VAR in ITERABLE:
    pass
```
The *TEMP_VAR* will be populated with each item as we iterate through the *ITERABLE* and it will be available to us in the context of the loop. After the loop finishes one iteration, then the *TEMP_VAR* will be populated with the next item in the *ITERABLE*, and the loop's body will execute again. This process continues until we either hit a `break` statement or we've iterated over every item in the *ITERABLE*. Here's an example looping over a list of colors:
```python
>>> colors = ['blue', 'green', 'red', 'purple']
>>> for color in colors:
...     print(color)
...
blue
green
red
purple
>>> color
'purple'
```
If we wanted not to print out certain colors we could utilize the `continue` or `break` statements again. Let's say we want to skip the string 'blue' and terminate the loop if we see the string 'red':
```python
>>> colors = ['blue', 'green', 'red', 'purple']
>>> for color in colors:
...     if color == 'blue':
...         continue
...     elif color == 'red':
...         break
...     print(color)
...
green
>>>
```

###### Other Iterable Types
Lists will be the most common type that we iterate over using a `for` loop, but we can also iterate over other iterable types. Of the types we already know, we can iterate over strings, dictionaries, and tuples.

Here's a tuple example:
```python
>>> point = (2.1, 3.2, 7.6)
>>> for value in point:
...     print(value)
...
2.1
3.2
7.6
>>>
```
A dictionary example:
```python
>>> ages = {'kevin': 59, 'bob': 40, 'kayla': 21}
>>> for key in ages:
...     print(key)
...
kevin
bob
kayla
```
A string example:
```python
>>> for letter in "my_string":
...     print(letter)
...
m
y
_
s
t
r
i
n
g
>>>
```

###### Unpacking Multiple Items in a for Loop
We discussed in the tuples section how you could separate a `tuple` into multiple variables by "unpacking" the values. Unpacking works in the context of a loop definition, and you'll need to know this to most effectively iterate over dictionaries because you'll usually want the *key* and the *value*. Let's iterate of a `list` of "points" to test this out:
```python
>>> list_of_points = [(1, 2), (2, 3), (3, 4)]
>>> for x, y in list_of_points:
...     print(f"x: {x}, y: {y}")
...
x: 1, y: 2
x: 2, y: 3
x: 3, y: 4
```
Seeing how this unpacking works, let's use the `items` method on our ages dictionary to list out the names and ages:
```python
>>> for name, age in ages.items():
...     print(f"Person Named: {name}")
...     print(f"Age of: {age}")
...
Person Named: kevin
Age of: 59
Person Named: bob
Age of: 40
Person Named: kayla
Age of: 21
```

### Functions
Being able to write code that we can call multiple times without repeating ourselves is one of the most powerful things that we can do when programming. In python a block of code that can executed multiple times is called a function.

#### [Defining functions](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
We can create functions in Python using the following:

- The `def` keyword
- The function name - starting with a letter or underscore `_` and continue with a letter, a digit or underscore `_`
- Left parenthesis `(`
- 0 or more argument names
- Right parenthesis `)`
- A colon `:`
- An indented function body
```python
>>> def say_hello():
...     print('Hello from function')
...
>>> say_hello()
Hello from function
```
If we want to have an argument for function, we just name that argument using a variable.
```python
>>> def say_hello(name):
...     print(f'Hello {name!r}')
...
>>> say_hello('Mehdi')
Hello 'Mehdi'
```
Functions also return a result, so we can assign the result of function execution to a variable.
```python
>>> def say_hello(name):
...     print(f'Hello {name!r}')
...
>>> result = say_hello('Mehdi')
>>> result
>>>
```
Since we didn't explicitly returned any value from the function, result of the function is `None`. We can return a result from the function using `return` keyword.
```python
>>> def say_hello(name):
...     return f'Hello {name!r}'
...
>>> result = say_hello('Mehdi')
>>> print(result)
Hello 'Mehdi'
```

#### Working with Multiple Arguments
In a function we can have as many argument as required.
```python
>>> def add(num1, num2):
...     return num1 + num2
...
>>> print(add(100, 200))
300
>>> print(add('Add ', 'strings'))
Add strings
```
Sometimes you may want to have an unlimited number of arguments, this is also possible in python.
```python
>>> def add(*args):
...     result = None
...     for arg in args:
...         if result is None:
...             result = arg
...         else:
...             result += arg
...     return result
...
>>> print(add(100, 200, 300, 400))
1000
>>> print(add('Add ', 'multiple ', 'strings'))
Add multiple strings
```

#### Using Keyword Arguments
Every function call we've made up to this point has used what are known as positional arguments, but if we know the name of the arguments and not necessarily the positions we can call them all using keyword arguments like so:
```python
>>> def contact_card(name, age, car_model):
...     return f"{name} is {age} and drives a {car_model}"
...
>>> contact_card("Keith", 29, "Honda Civic")
'Keith is 29 and drives a Honda Civic'
>>> contact_card(age=29, car_model="Civic", name="Keith")
'Keith is 29 and drives a Civic'
>>> contact_card("Keith", car_model="Civic", age="29")
'Keith is 29 and drives a Civic'
>>> contact_card(age="29", "Keith", car_model="Civic")
  File "<stdin>", line 1
SyntaxError: positional argument follows keyword argument
```
When we're using position and keyword arguments, every argument after the first keyword argument must also be a keyword argument. It's sometimes useful to mix them, but often times we'll use either all positional or all keyword.

Somethimes you don't want a variable to accidentally assigned a value(or simply can't), for example in our *contact_card* function we may want to have a *format* argument that user can only pass it by name.
```python
>>> def contact_card(name, age, car_model, *, format):
...     if format == 'simple':
...         return f"{name} is {age} and drives a {car_model}"
...     else:
...         return(
...             f"name: {name}\n"
...             f"age: {age}\n"
...             f"car model: {car_model}" )
...
>>> print(contact_card("Keith", 29, "Honda Civic", 'advanced'))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: contact_card() takes 3 positional arguments but 4 were given
>>> print(contact_card("Keith", 29, "Honda Civic", format='simple'))
Keith is 29 and drives a Honda Civic
>>> print(contact_card("Keith", 29, "Honda Civic", format='advanced'))
name: Keith
age: 29
car model: Honda Civic
```
As we could handle infinite amount of positional arguments we may also handle unknown keyword arguments.
```python
>>> def contact_card(name, age, car_model, *, **kwargs):
...     result = f"name: {name}\nage: {age}\ncar model: {car_model}"
...     for key, value in kwargs:
...         result += f"{key}: {value}" )
...     return result
...
>>> print(contact_card("Keith", 29, "Honda Civic", job='Developer', phone=12345678, married=False))
name: Keith
age: 29
car model: Honda Civic
job: Developer
phone: 12345678
married: False
```

#### Defining Default Arguments
Along with being able to use keyword arguments when we're calling a function, we're able to define default values for arguments to make them optional when the information is commonly known and the same. To do this, we use the assignment operator (=) when we're defining the argument.
```python
>>> def contact_card(name, age, car_model = None, *, format='simple'):
...     if format == 'simple':
...         if car_model is None:
...             return f"{name} is {age} and does not have a car"
...         return f"{name} is {age} and drives a {car_model}"
...     else:
...         result = f"name: {name}\nage: {age}\n"
...         if car_model is not None:
...             result += f"car model: {car_model}"
...         return result
...
>>> print(contact_card("Keith", 29))
Keith is 29 and does not have a car
>>> print(contact_card("Keith", 29, "Honda Civic"))
Keith is 29 and drives a Honda Civic
>>> print(contact_card("Keith", 29, format='advanced'))
name: Keith
age: 29
>>> print(contact_card("Keith", 29, "Honda Civic", format='advanced'))
name: Keith
age: 29
car model: Honda Civic
```
Not that we can still use a value for the argument if we want to, but it will use a default value if we omit that variable.

In **python 3.8** we have another option in writing a function, we can force an argument to be only available as positional argument.
```python
>>> def get_length(obj, /): return len(obj)
...
>>> get_length([1, 2, 3])
3
>>> get_length(obj=[1, 2, 3])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: get_length() got some positional-only arguments passed as keyword arguments: 'obj'
```
