# Hello World
```python
$ python
Python 3.10.4 (main, Apr  3 2023, 22:35:52) [GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello, World!")
Hello, World!
>>> 
```
# The Zen of Python
```
>>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
>>> this.__file__
'/usr/local/python/3.10.4/lib/python3.10/this.py'
>>> 
```
# Keyword
```
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
>>> 
```
# Comment
## Single line comment
* comment in **calendar.py**
```python
# Constants for months referenced later
January = 1
February = 2

# Number of days per month (except for February in leap years)
mdays = [0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
```

## block or doc comment
* after class or def, ''' ''' or """ """, e.g. Line 282 in os.py, which is part of doc.
```python
def walk(top, topdown=True, onerror=None, followlinks=False):
    """Directory tree generator.

    For each directory in the directory tree rooted at top (including top
    itself, but excluding '.' and '..'), yields a 3-tuple

        dirpath, dirnames, filenames

    dirpath is a string, the path to the directory.  dirnames is ...
```
* check ```help(os.walk)``` on ipython
```python
>>> help(os.walk)
Help on function walk in module os:

walk(top, topdown=True, onerror=None, followlinks=False)
    Directory tree generator.

    For each directory in the directory tree rooted at top (including top
    itself, but excluding '.' and '..'), yields a 3-tuple

        dirpath, dirnames, filenames

    dirpath is a string, the path to the directory. 
```
# Data type && Variable
## int
```Python
>>> a, b, c = range(3, 6)
>>> print(f"a, b, c = {a, b, c}")
a, b, c = (3, 4, 5)
>>> a, b, c = c, a, b
>>> print(f"a, b, c = {a, b, c}")
a, b, c = (5, 3, 4)
>>> print(f"{a*a} == {b*b} + {c*c}? {a*a == b*b + c*c}")
25 == 9 + 16? True
>>> sum([i for i in range(101) if not i%2]), sum([i for i in range(101) if i%2])
(2550, 2500)
```
## float
```Python
>>> import math
>>> print(math.pi, math.e, sep='\n')
3.141592653589793
2.718281828459045
```
## string
```python
>>> import os
>>> print(os.name, type(os.name), sep='-')
posix-<class 'str'>
>>> import math
>>> print(eval("math.sqrt(3*3 + 4*4)"))
5.0

>>> s = "Hello你好"
>>> s.encode("UTF-8")
b'Hello\xe4\xbd\xa0\xe5\xa5\xbd'
>>> s.encode("GB2312")
b'Hello\xc4\xe3\xba\xc3'
>>> s.encode("GBK")
b'Hello\xc4\xe3\xba\xc3'
>>> b'Hello\xc4\xe3\xba\xc3'.decode("GBK")
'Hello你好'
```
## bool
* ```True```
* ```False```
```python
>>> print("0.3 == 0.1 + 0.2?", 0.3==0.1+0.2)
0.3 == 0.1 + 0.2? False
```
```python
>>> import keyword
>>> var = "True"
>>> is_keyword = keyword.iskeyword(var)
>>> if is_keyword:
...     print(f'{var} is a key word? {is_keyword}', type(is_keyword), sep=' - ')
...     print(f'{keyword.kwlist[keyword.kwlist.index(var)]} = keyword.kwlist[{keyword.kwlist.index(var)}]')
... 
True is a key word? True - <class 'bool'>
True = keyword.kwlist[2]
>>> print(F"true in keyword.kwlist? {'true' in keyword.kwlist}", type("true" in keyword.kwlist), sep=' - ')
true in keyword.kwlist? False - <class 'bool'>
```
## list
```python
>>> fib = [1, 1, 2, 3, 5]
>>> a, b, _, _, _ = fib
>>> a, b
(1, 1)
>>> [ x for x in range(10) if not x%2 ]
[0, 2, 4, 6, 8]
>>> import keyword
>>> keyword.kwlist[:5]
['False', 'None', 'True', 'and', 'as']
>>> import calendar
>>> calendar.mdays
[0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]

>>> for i, v in enumerate(range(5)):
...     print(f'{i} -> {v}')
... 
0 -> 0
1 -> 1
2 -> 2
3 -> 3
4 -> 4
```
## tuple
```python
>>> import sys
>>> print(sys._git, type(sys._git), sep=' - ')
('CPython', '', '') - <class 'tuple'>
```
* ```def _use_posix_spawn``` in os.py
```python
        # parse 'glibc 2.28' as ('glibc', (2, 28))
        parts = ver.split(maxsplit=1)
        if len(parts) != 2:
            # reject unknown format
            raise ValueError
        libc = parts[0]
        version = tuple(map(int, parts[1].split('.')))

        if sys.platform == 'linux' and libc == 'glibc' and version >= (2, 24):
            # glibc 2.24 has a new Linux posix_spawn implementation using vfork
            # which properly reports errors to the parent process.
            return True
```
## dict
```python
>>> d = dict(a=3, b=4, c=5)
>>> d
{'a': 3, 'b': 4, 'c': 5}
>>> type(d)
<class 'dict'>
>>> d['s'] = 3 * 4 / 2
>>> d
{'a': 3, 'b': 4, 'c': 5, 's': 6.0}
>>> d.pop('s')
6.0

>>> d = {"name": "John Doe", "age": 42}
>>> d.update({'foot': d.pop('age')})
>>> d
{'name': 'John Doe', 'foot': 42}

>>> {i: i*i for i in range(5)}
{0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
>>> 
```
## set
```
```
# assignment && copy && deepcopy
```python
>>> a = [1, 2, 3]
>>> b = a
>>> id(a) == id(b)
True
>>> c = a.copy()
>>> id(a) == id(c)
False
>>> a[0] = 0
>>> a
[0, 2, 3]
>>> b
[0, 2, 3]
>>> c
[1, 2, 3]

>>> a = [0, [0,1]]
>>> b = a
>>> a
[0, [0, 1]]
>>> b
[0, [0, 1]]
>>> id(a) == id(b)
True
>>> c = a.copy()
>>> c
[0, [0, 1]]
>>> id(a)
139982403815488
>>> id(c)
139982403796608
>>> a[1][0] = 1
>>> a
[0, [1, 1]]
>>> c
[0, [1, 1]]

>>> import copy
>>> d = copy.deepcopy(a)
>>> d
[0, [1, 1]]
>>> a[1][0] = 0
>>> a
[0, [0, 1]]
>>> d
[0, [1, 1]]
```

# Control Flow
## Contional
```python
num = input("Please input an integer and then I will tell you it is even or odd: ")

if int(num) % 2 == 0:
    print(f"{num} is even!")
else:
    print(f"{num} is odd!")
```
## Loop
### `while-else`
```python
>>> total = 0
>>> n = 1
>>> while n <= 100:
...     total += n
...     n += 1
... else:
...     print(total)
... 
5050
```
### `for`
```python
>>> sum = 0
>>> for i in range(1, 101):
...     sum += i
... else:
...     print(f"sum from 0 to 100: {sum}")
... 
sum from 0 to 100: 5050

>>> import calendar
>>> for month, days in enumerate(calendar.mdays[1:4], start=1):
...     print(month, days)
... 
1 31
2 28
3 31
```
### `for-if-elif-else`
```python
>>> for i in range(-1, 5):
...     if i<0:
...             print(f"{i:2d} less than 0")
...     elif i%2:
...             print(f"{i:2d} odd")
...     else:
...             print(f"{i:2d} even")
... 
-1 less than 0
 0 even
 1 odd
 2 even
 3 odd
 4 even
```
### `for-for`
```python
>>> for i in range(1, 10):
...     for j in range(1, i+1):
...             print(f"{j} * {i} = {i*j:-2d}", end="  ")
...     print()
... 
1 * 1 =  1  
1 * 2 =  2  2 * 2 =  4  
1 * 3 =  3  2 * 3 =  6  3 * 3 =  9  
1 * 4 =  4  2 * 4 =  8  3 * 4 = 12  4 * 4 = 16  
1 * 5 =  5  2 * 5 = 10  3 * 5 = 15  4 * 5 = 20  5 * 5 = 25  
1 * 6 =  6  2 * 6 = 12  3 * 6 = 18  4 * 6 = 24  5 * 6 = 30  6 * 6 = 36  
1 * 7 =  7  2 * 7 = 14  3 * 7 = 21  4 * 7 = 28  5 * 7 = 35  6 * 7 = 42  7 * 7 = 49  
1 * 8 =  8  2 * 8 = 16  3 * 8 = 24  4 * 8 = 32  5 * 8 = 40  6 * 8 = 48  7 * 8 = 56  8 * 8 = 64  
1 * 9 =  9  2 * 9 = 18  3 * 9 = 27  4 * 9 = 36  5 * 9 = 45  6 * 9 = 54  7 * 9 = 63  8 * 9 = 72  9 * 9 = 81
```
# Exception
```python
>>> print a
  File "<stdin>", line 1
    print a
    ^^^^^^^
SyntaxError: Missing parentheses in call to 'print'. Did you mean print(...)?
>>> print(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'a' is not defined
>>> int('a')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'a'
```
# function
```python
# function isleap in module calendar
def isleap(year):
    """Return True for leap years, False for non-leap years."""
    return year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)
```
---
```python
def is_leap(year):
    '''
        check if year is a leap year or not.
        @param: year in YYYY
        @return： True | False
    '''
    if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:
        return True
    return False
```
# lambda
# recursion
```python
>>> def countdown(n):
...     if n == 0:
...             print("Start!")
...     else:
...             print(n)
...             countdown(n-1)
... 
>>> countdown(9)
9
8
7
6
5
4
3
2
1
Start!

>>> def fact(n):
...     if n in [0, 1]: 
...             return 1
...     else:
...             return n * fact(n-1)
... 
>>> fact(5)
120
```
# with
```python
with open('/') as fh_root:
    pass
```
# Context Management
```python
class CM(object):
    
    def __enter__(self):
        pass

    def __exit__(self):
        pass
```
# OOP
## `class/self/prop/method`
```python
class Cls:
    cls_prop

    @classmethod
    def cls_method():
        pass

    @staticmethod
    def static_method():
        pass

    def __init__(self, ...):
        self.__pri_prop = 'some private prop'
        pass

    @property
    def prop(self):
        pass

    @prop.setter
    def set_prop(self):
        pass

    def __str__(self):
        pass
```
## `__<prop/method>`
## `@classmethod`
## `@staticmethod`
## `@property` && `@<prop>.setter`
```

```
## override
```

```
```python
class Python:
    author = 'Guido'

    @classmethod
    def zen(cls):
        
```
# module
```python
>>> import math
>>> type(math)
<class 'module'>
>>> math.pi, math.e
(3.141592653589793, 2.718281828459045)
>>> type(math.__dict__)
<class 'dict'>
>>> __name__, math.__name__
('__main__', 'math')
>>> math.__file__
'/usr/local/python/3.10.4/lib/python3.10/lib-dynload/math.cpython-310-x86_64-linux-gnu.so'

# the module os -> os.py
>>> import os
>>> os.name
'posix'
>>> os.__file__
'/usr/local/python/3.10.4/lib/python3.10/os.py'
```
* best practise in a module(.py)
```python
    import <module>

    if __name__ == '__main__':
        pass
```
# package
* a folder with `__init__.py`
* expose `class`/`function ` with `__all__`
```shell
$ tree collections/
collections/
├── __init__.py
├── __pycache__
│   ├── __init__.cpython-310.opt-1.pyc
│   ├── __init__.cpython-310.opt-2.pyc
│   ├── __init__.cpython-310.pyc
│   ├── abc.cpython-310.opt-1.pyc
│   ├── abc.cpython-310.opt-2.pyc
│   └── abc.cpython-310.pyc
└── abc.py
```
```py
__all__ = [
    'ChainMap',
    'Counter',
    'OrderedDict',
    'UserDict',
    'UserList',
    'UserString',
    'defaultdict',
    'deque',
    'namedtuple',
]
```
```python
>>> import collections
>>> collections.__file__
'/usr/local/python/3.10.4/lib/python3.10/collections/__init__.py'
```
## 
# Regular Expression - re
```
```