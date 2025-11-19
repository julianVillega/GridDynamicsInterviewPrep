[link to chat gpt chat](https://chatgpt.com/share/691e3871-378c-8003-87d3-28cd5433a570)

# **Data Structures:**

## **Lists**

- Ordered
- Mutable
- Allow duplicates
- **elements can be of different types, although this is not usual**
```Python
# valid list examples
lst = [1, 2, 3] lst.append(4) lst[0] = 10
lst = [1, "hello", 3.14, [1,2], {"a":1}]
```

## **Tuples**

- Ordered
- **Immutable**
- Useful for fixed collections & as dict keys
- **tuples allow for duplicate values**

```Python
t = (1, 2, 3) 
t2 = (1,1,2,2,3,3) # they accept duplicate values.
# t[0] = 10 → error tuples are immutable
```


## **Sets**

- **Unordered**
- No duplicates !!
- Fast membership checks

`s = {1, 2, 3} s.add(3)  # no effect`

## **Dictionaries**

- Key → value mapping
- Keys must be hashable (immutable)
- Cannot have duplicate keys, if so the last value overwrites the previous ones.
```Python
d = {"a": 1, "b": 2} 
d["c"] = 3
d2 = {"a": 1, "b": 2, "a":6}
d2["a"] # outputs 6 
```

Dictionary keys must be hashable and immutable.
Built in hashable keys types are:
int, float, str, tuples of hashable elements only, frozenset and None


# **Slicing and List Comprehensions:**

## Slicing:

Slicing is used to create a new list, tuple or string from a segment of another such object.
it's syntax is as follows:
```Python
# iterrable[startIndex : endIndex]
# practical example:

lst = [0,1,2,3,4,5]
lst[1:4]   # [1,2,3] # notice lst[4] is not included
lst[:3]    # [0,1,2] # when startIndex is ommited, 0 the default value
lst[::2]   # [0,2,4] # returns a list of every second element
lst[::-1]  # reverse list

```

## List comprehensions:

List comprehensions are useful for creating a lists sets and dictionaries from other iterables.
For example:

```Python
squares = [x*x for x in range(5)]
evens = [x for x in lst if x % 2 == 0] 

sq_set = {x*x for x in range(5)}
index_map = {i: v for i, v in enumerate(lst)}
```


# Functions:

## Functions Overview:

In python functions support the following types of arguments:
* Positional Arguments
* Keyword Arguments
* Default Parameters

## Positional Arguments:
The following is an example of a simple function that uses positional arguments only:

```Python
def add(a, b):
	return a + b
```


## Default Parameters

These are arguments that take default values is no value is provided when the function is called.

```Python
def f(name="john"):
	print("hello ", name)
```

## \*Args keyword

The \*Args keyword is used to specify a variable number of positional arguments. for example:

```Python
def f(*args):
	return args[0]
	
	
f(1,2,3) # works fine
f(1) # works fine
```

## \*\*Kwargs Keyword
Similar to \*args, \*\*Kwargs allow to specify a variable number of kword arguments, that is arguments that must be specified by their name when calling the function. For example:

```Python
def f(**kwargs):
	pinrt(kwargs)
	
f(name="mary", sureName="on a cross") # prints {'name':"mary", 'surename':"on a cross"}
```

## Types of Arguments and their order:

When using multiple types of arguments in a function, they must follow a specific order:

1. Positional arguments without default values.
2. \*args for a variable number of positional arguments
3. Default Parameters
4. \*\*kwargs for a variable number of keyword arguments

Example:

```Python

def f(x, *args, y=10, **kwargs):
    print(x)
    print(args)
    print(kwargs)
    
f(123, "b","c",false, greeting="it's me Mario!")
"""
outputs:
123 for x
["b","c",false] for *args
10 for y with it's default value
{'greeting':"it's me Mario"} for **kwargs
"""
```


# Object Oriented Python:

### **Class & instance**
```Python
class Animal:
    def __init__(self, name):
        self.name = name  # instance attribute
    
    def speak(self):
        print("no sound")

```


### **Inheritance**

```Python
class Dog(Animal):
    def speak(self):
        print("woof")

```

### **Method types**

|Type|Definition|Usage|
|---|---|---|
|Instance method|`def method(self)`|most methods|
|Class method|`@classmethod def m(cls)`|factory methods|
|Static method|`@staticmethod`|utility functions|

Class methods have access to class atributes, these are shared among all instances of a class.
These methods are invoked from the class itself not requiring an instance to do so. For this reason they are usually used to create factory methods.

Static methods on the other hand, are just a namespace inside a class, they are used for creating utility functions, these cannot access instance or class state.

Example:
```Python
class A:
    count = 0  # class attribute

    @classmethod
    def inc(cls):
        cls.count += 1

    @staticmethod
    def util(x):
        return x * 2


```

# Modules, Packages and Imports

In Python a module is simple a file with a .py extension from with we can import things like functions, classes or even individual variables.

Packages on the other hand are folders containing one or more modules (.py files) alongside a
`__init__.py` file. This the presence of this file tells the python interpreter to treat the files in that directory as modules.

The following example shows a package with 2 modules, main and utils where the add function from utils is imported in the main file.

```Python
project/
    utils.py
    main.py

```

*utils.py*
```Python
def add(a, b):
    return a + b

```

*main.py*
```Python
from utils import add
print(add(1, 2))
```

## Imports:
There are several ways to use imports:

## Importing a whole module:

```Python
import math # imports all the math module
```

## Importing specific names (functions, classes, variables ...)
```Python
from math import sqrt# imports only the sqrt function from the math module
```

## Importing with aliases:
```Python
import numpy as np # imports the numpy module but allows us to refer to it as np.
np.someMethod()
```
