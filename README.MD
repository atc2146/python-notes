# Python Notes

Notes and references on Python. Taken from various sources. For educational use only.

## Table of Contents
* [Strings](#strings)
    * [String Methods](#string-methods)
    * [String Slices](#string-slices)
    * [f-Strings](#f-strings)
* [Lists](#lists)
    * [Iterating Lists](#iterating-lists)
    * [List Comprehension](#list-comprehension)
    * [List Methods](#list-methods)
    * [Creating Lists](#creating-lists)
    * [Adding Lists](#adding-lists)
    * [Comparing Lists](#comparing-lists)
* [Dictionaries](#dictionaries)
    * [Iterating](#iterating)
    * [Searching for a key](#searching-for-a-key)
    * [Sorting a dictionary](#sorting-a-dictionary)
    * [Merging dictionaries](#merging-dictionaries)
    * [The setdefault() method](#the-setdefault-method)
    * [The defaultdict collection](#the-defaultdict-collection)
* [Tuples](#tuples)
    * [Tuple Methods](#tuple-methods)
* [Sets](#sets)
* [Deletion](#deletion)
* [Regex](#regex)
    * [Regex Patterns](#regex-patterns)
* [Functions](#functions)
    * [Arguments](#arguments)
        * [*args](#args-non-keyword-argument)
        * [**kwargs](#kwargs-keyword-argument)
        * [Ordering](#ordering)
* [Lambda Functions](#lambda-functions)
    * [reduce(), filter(), map()](#reduce-filter-map)
        * [reduce()](#reduce)
        * [filter()](#filter)
        * [map()](#map)
* [Iterators, Generators, and Decorators](#iterators-generators-and-decorators)
    * [Iterators](#iterators)
    * [Generators](#generators)
    * [Decorators](#decorators)
* [Syntatic Sugar and Other](#syntatic-sugar-and-other)
    * [Math](#math)
      * [Permutations and Combinations](#permutations-and-combinations)
    * [Try Except](#try-except)
    * [Assert](#assert)
    * [Any and All](#any-and-all)
    * [Max And Min](#max-and-min)
    * [Zip](#zip)
    * [Type Hinting](#type-hinting)
    * [Walrus Operator](#walrus-operator)
    * [collections.Counter()](#collectionscounter)
* [Bitwise Operators](#bitwise-operators)
* [Sorting](#sorting)
* [Reversing](#reversing)
* [Data Structures and Types](#data-structures-and-types)
    * [Linked Lists](#linked-lists)
    * [Hash Tables](#hash-tables)
    * [Stacks](#stacks)
    * [Queues](#queues)
        * [Priority Queues](#priority-queues)
        * [Double Ended Queue](#double-ended-queue)
    * [Heaps](#heaps)
    * [Binary Search Tree](#binary-search-tree)
* [Algorithms](#algorithms)
    * [Depth First Search](#depth-first-search)
    * [Breadth First Search](#breadth-first-search)
    * [Binary Search](#binary-search)
* [Dynamic Programming](#dynamic-programming)
* [Recursion](#recursion)
* [Time Complexity](#time-complexity)
    * [Big O Notation](#big-o-notation)
    * [Time complexity of built-ins](#time-complexity-of-built-ins)
* [Space Complexity](#space-complexity)
* [Object Oriented Programming](#object-oriented-programming)
    * [Classes](#classes)
* [Pandas](#pandas)
    * [Creating DataFrames](#creating-dataframes)
    * [Selecting](#Selecting)
    * [Dates and Times](#dates-and-times)
* [NumPy](#numpy)
* [References](#References)

 
## Strings

Python strings are immutable.

A "raw" string literal is prefixed by an 'r' and passes all the characters through without special treatment of backslashes, so `r'x\nx'` evaluates to the length-4 string `'x\nx'`.

### String Methods
* `s.split('delim')`: Returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text.
  * Example: `'aaa,bbb,ccc'.split(',')` -> `['aaa', 'bbb', 'ccc']`.
  * As a convenient special case `s.split()` (with no arguments) splits on all whitespace characters.
* `s.join(list)`: Opposite of `split()`, joins the elements in the given list together using the string as the delimiter.
  * Example: `'---'.join(['aaa', 'bbb', 'ccc'])` -> `aaa---bbb---ccc`
* `string.count(substring, [start=...], [end=...])`: The `count()` method searches the substring in the given string and returns how many times the substring is present in it.
* `s.startswith()`: Returns True if a string starts with the specified prefix. If not, it returns False.
* `s.find()`: The `find()` method returns the index of first occurrence of the substring (if found). If not found, it returns -1.
* `s.index(element, start, end)`: returns the index of a substring inside the string (if found). If the substring is not found, it raises an exception.
  * start and end (optional): substring is searched within str[start:end]
* `s.isdigit()`: Checks whether the string consists of digits only.  Returns True or False.
  * There is also `isnumeric()` and `isdecimal()`
* `s.isalnum()`: The `isalnum()` method returns True if all characters in the string are alphanumeric (either alphabets or numbers). If not, it returns False.
* `s.replace(old, new [, count])`: replaces each matching occurrence of the old character/text in the string with the new character/text.
  * Takes an optional count argument which is the maximum number of times you want to replace the old substring with the new substring.
* `s.lower()` and `s.upper()`: changes to lowercase or uppercase, respectively.  There is also `s.capitalize()` which capitilizes the first character of a word.
* `s.islower()` and `s.isupper()`: returns whether or not **all** characters in a string are lowercased or uppercased, respectively.


### String Slices
The "slice" syntax is a handy way to refer to sub-parts of sequences - typically strings and lists. The slice `s[start:end]` slices the elements beginning at start and extending up to but **not** including the end.

String slices can also take a 3rd argument, the stride - `s[start:stop:stride]`.

Example:
```python
# Reverse a string
my_string = 'Hello world'

my_string[0:2] # 'He'

my_string[::-1] # 'dlrow olleH'

my_string[-2:] # 'ld'
```
### f-Strings
A convenient way to format strings with variables.

```python
name = 'Eric'
age = 74

print(f'Hello, {name}. You are {age}.') ## Hello, Eric. You are 74.
``` 

## Lists

### Iterating Lists

To iterate over a list with an index and value:  

```python
my_list = ['Team A', 'Team Bobcats', 'Team XYZ']

for ind, val in enumerate(my_list):
    print(ind, val)
    
# 0 Team A
# 1 Team Bobcats
# 2 Team XYZ
```

To iterate using `range()`:

```python
some_list = [4, 7, 8, 9, 22, 11]

for i in range(0, len(some_list), 1):
    print(some_list[i])

# Iterating backwards
for i in range(len(some_list)-1, -1, -1):
    print(some_list[i])

```
This will iterate up to but **not** including the index at the **2nd argument** in `range()`.

### List Comprehension
Use listcomps if you want to build lists.

The syntax is: *[expr for var in list {optional if expr}]*

```python
my_list = [1, 2, 3, 4]

[i*i for i in my_list if i%2==0]
```

There are also dictionary and set comprehensions.

### List Methods  

* The `insert()` method inserts an element to the list at the specified index.
* The `pop()` method removes the item at the given index from the list and returns the removed item.
    * You can also have an index at a negative value. This will count backwards from the list.
    * Pop without an index removes the last element of the list.
* The `remove()` method removes the first matching element (which is passed as an argument) from the list.
    * Returns `None`
    * If the element doesn't exist, it throws a `ValueError`.
    * If a list contains duplicate elements, the `remove()` method only removes the first matching element.
* The `count()` method returns the number of times the specified element appears in the list.
* The `index()` method returns the index of the specified element in the list.
* The `append()` method adds an item to the end of the list.
* The `extend()` method adds all the elements of an iterable (list, tuple, string etc.) to the end of the list.
* The `copy()` method copies the list. Note there are other ways of copying a list including slicing or forcing/casting the list type.
    
```python
my_list = [1,2,3,4]

my_list.insert(index, element)

popped_item = my_list.pop(index)

my_list.remove(element)

my_list.count(element)

my_list.index(element, [start], [end])

my_list[:-1]
# [1, 2, 3]

my_list[::-1]
# [4, 3, 2, 1]
```
Note: Slicing creates a shallow copy of the original list.

Also keep in mind that if you doing repeated `append()` and `pop(0)` calls, you may want to consider using a `deque`. For a `list` those calls require the entire list to be shifted in memory.

### Creating Lists
If you want to create a list.

```python
my_list = ['bob']*3 # can't be an empty list (can put None)
# ['bob', 'bob', 'bob']

[1, 2] * 2
# [1, 2, 1, 2]

[[1,2] for i in range(0, 2)]
# [[1, 2], [1, 2]]

my_list = list(range(2, 20, 3)) # last argument is stride
# [2, 5, 8, 11, 14, 17]
```

### Adding Lists
Adding lists using the plus operator in Python is **not** done element wise.  

```python
[1, 2] + [1, 1]
# [1, 2, 1, 1]
```

### Comparing Lists

[Comparing lists of lists](https://dbader.org/blog/python-min-max-and-nested-lists) with functions like `max()` will compare element wise.

```python
my_list = [[1, 2], [1, 4], [-2, 6]]

max(my_list) # [1, 4]

min(my_list) # [-2, 6]

# max() compares 1,1,-2 first, then 2,4
```

## Dictionaries

This is essentially Python's version of a Hash Table (associative array).  Dictionaries have key value pairs.  The keys in the dictionary need to be **hashable**.  For example, lists cannot be used as keys as they are not hashable.  There is no restriction on the value type.

The actual implementation is pretty interesting - read about on [Python.org](https://docs.python.org/3/faq/design.html#how-are-dictionaries-implemented-in-cpython).

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

# list keys
my_dict.keys() # dict_keys(['bob', 'james', 'mary'])

# list values
my_dict.values() # dict_values([20, 33, 18])

# delete a key
del my_dict['bob']

# clear dictionary
my_dict.clear()

```

### Iterating
To iterate over a dictionary:

```python
# creating an empty dict
some_dict = dict()
some_dict = {}

my_dict = {'bob': 20, 'james': 33, 'mary': 18}

for k, v in my_dict.items():
    print(k, v)

# bob 20
# james 33
# mary 18
```
### Searching for a key
Searching for a key:
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

if key in my_dict:
    print(str(key) + ' exists')

# bob exists
```

**Do not** iterate using `if key in my_dict.keys()`! This is `O(n)`, compared to `O(1)` above.


There is also the `get()` method.  This method returns a value for the given key. If the key is not available, then it returns default value `None`.
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

print(my_dict.get(key))

# 20

# if you want to specify a default value if key cannot be found
my_dict.get(key, 'DEFAULT_VAL')
```

If you try to access a key that does not exist, an error with be thrown:

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

my_dict['obama']
# Will throw an error

# ERROR!
# Traceback (most recent call last):
#   File "<string>", line 3, in <module>
# KeyError: 'obama'
```

### Sorting a dictionary

```python
x = {1: 2, 3: 4, 4: 3, 2: 1, 0: 0}

# Sort by dictionary value
# This will return a list of tuples
sorted_list = sorted(x.items(), key = lambda i: i[1])
#  [(0, 0), (2, 1), (1, 2), (4, 3), (3, 4)]

dict(sorted_list)
# {0: 0, 2: 1, 1: 2, 4: 3, 3: 4}

```
### Merging dictionaries

You can merge dictionaries with the unpacking operator, `**`

```python
vegetable_prices = {'pepper': 0.20, 'onion': 0.55}
fruit_prices = {'apple': 0.40, 'orange': 0.35, 'pepper': .25}

{**vegetable_prices, **fruit_prices}
# {'pepper': 0.25, 'onion': 0.55, 'apple': 0.4, 'orange': 0.35}

```

You can also use the `|` to merge dicts starting in Python 3.9.

### The setdefault() method
The `setdefault()` method returns the value of the item with the specified key. If the key does not exist, insert the key, with the specified value: `dictionary.setdefault(keyname, value)`

```python
person = {'name': 'Phill'}

# key is not in the dictionary
salary = person.setdefault('salary')
print('person = ', person)
print('salary = ', salary)

# key is not in the dictionary
# default_value is provided
age = person.setdefault('age', 22)
print('person = ', person)
print('age = ', age)

# person =  {'name': 'Phill', 'salary': None}
# salary =  None
# person =  {'name': 'Phill', 'age': 22, 'salary': None}
# age =  22
```

Also, consider this code:

```python
if key not in my_dict:
    my_dict[key] = []
my_dict[key].append(new_value)
```

Which can be replaced with the following:

```python
my_dict.setdefault(key, []).append(new_value)
```

The latter is much more efficient (everything done in a single lookup).

### The defaultdict collection

If a key is not found in the dictionary, then instead of a KeyError being thrown, a new entry is created. Read [more](https://docs.python.org/3/library/collections.html#collections.defaultdict).

```python
from collections import defaultdict

ice_cream = defaultdict(lambda: 'Vanilla')

ice_cream['Sarah'] = 'Chunky Monkey'
ice_cream['Abdul'] = 'Butter Pecan'

print(ice_cream['Sarah'])
# Chunky Monkey

print(ice_cream['Joe'])
# Vanilla
```

Similarly, with an integer type

```python
from collections import defaultdict

hm = defaultdict(int)

hm['b']
# does not throw an error

print(hm['b])
# 0

# If want 1 as the default value
hm = defaultdict(lambda: 1)
```

## Tuples
A tuple is a collection of objects which are **ordered** and **immutable**. Use tuples when the meaning of each field is given by its position in the tuple. For example, coordinates (lat. and long.).

A tuple has a fixed length.

```python
a_tuple = (1, )
another_tuple = ('a', 'b', 2)

empty_tuple = ()

valid_tuple = 3, 6, 'bob'
```

Note: You can also create a tuple without parentheses.

A tuple with one element needs a trailing comma.

Tuples are immutable, but if the element is itself a mutable data type like a list, its nested items can be changed.

Using the `+` or `*` operator on a tuple creates a **new** tuple.

```python
# Concatenation
print((1, 2, 3) + (4, 5, 6))
# Output: (1, 2, 3, 4, 5, 6)

# Repeat
print(("Repeat",) * 3)
# Output: ('Repeat', 'Repeat', 'Repeat')
```

Note: A tuple uses less memory than a list of the same length. A tuple is [more efficient](https://stackoverflow.com/questions/68630/are-tuples-more-efficient-than-lists-in-python/22140115#22140115) than lists in most ways, so use a tuple over a list, if appropiate.

### Tuple Methods

Tuples have the `count()` and `index()` method.

Methods that add items or remove items are not available with tuples.


## Sets
A set is an **unordered** collection with no duplicate elements. Basic uses include membership testing and eliminating duplicate entries. Set objects also support mathematical operations like union, intersection, difference, and symmetric difference.  

Curly braces `{}` or the `set()` function can be used to create sets.  

Note: to create an empty set you **have** to use `set()`, not `{}`.  The latter creates an empty dictionary.

```python
ages = {1, 22, 38}
empty_set = set()

a = set('abracadabra')  # {'a', 'r', 'b', 'c', 'd'}

# Can also create a set by passing it an iteratble
x = set(<iter>)

```

A set has a significantly faster `in` search than lists.  This is because sets finds the element by computing a hash from the key - whereas, in general, the whole list needs to be searched.  Both have `O(1)` time complexity, however.

Lists are faster (in general) when you are iterating over values, however.  This performance increases if you sort the list.

Set operations include 
* `.add()`
* `.remove()`
* `.discard()`
* `.pop()`
* `.clear()`
* `.update()`
* `.intersection_update()`
* `.difference_update()`
* `.symmetric_difference_update()`
* `.union()` or `|`
* `.intersection()` or `&`
* `.symmetric_difference()` or `^`
* `.isdisjoint()`
* `.issubset()`
* `.issuperset()`

A set is mutable.  However, a set cannot have mutable elements (lists, dictionaries) as its element.  A tuple may be included in a set.

## Deletion
You can use the `del` keyword to delete variables, user-defined objects, lists, items within lists, dictionaries, etc.

You cannot delete tuple elements, but you can delete an entire tuple.
```python
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

# deleting the third item
del my_list[2]

print(my_list) # [1, 2, 4, 5, 6, 7, 8, 9]

# deleting items from 2nd to 4th
del my_list[1:4]

print(my_list) # [1, 6, 7, 8, 9]

# deleting all elements
del my_list[:]

print(my_list) # []

# Removing a key-value pair from a dict
person = { 
  'name': 'Sam',
  'age': 25,
  'profession': 'Programmer',
}

del person['profession']

print(person) # {'name': 'Sam', 'age': 25}
```

## Regex
For Python regular expressions, you need to import the `re` module.  

Recall from the [strings](#strings) section, a raw string is prefixed by an `r`.

Some common regex functions are:
* `re.match(pattern, string)`: Searches the regular expression pattern and returns the first occurrence. Only searches the beginning of the string.
* `re.search(pattern, string)`: Searches the regular expression pattern and returns the first occurrence as a match object. Unlike Python `re.match()`, it will check all lines of the input string.
* `re.findall(pattern, string)`: search for all occurrences that match a given pattern. It will return a list.
* `re.sub(pattern, replacement, string, [count])`: replace the `string` with the replacement for all (or optionally number of `count`) occurances of `pattern`.

```python
import re

pattern = r'some string'
string = 'this is some string'

re.match(pattern, string) # None
re.search(pattern, string) # <re.Match object; span=(8, 19), match='some string'>
re.findall(pattern, string) # ['some string']
re.sub(pattern, 'bob' , string) # 'this is bob'
```
### Regex Patterns

Regular expression patterns include:

* `\d`: Any decimal digit (number).
* `\D`: Anything but a decimal digit (a non-digit).
* `\s`: Whitespace characters (tab, space, newline etc.). Same as `[ \t\n\r\f\v]`.
* `\S`: Anything but whitespace characters. Same as `[^ \t\n\r\f\v]`
* `\w`: Matches alphanumeric characters, including letters, numbers, and underscores.
* `\W`: Anything but alphanumeric characters.
* `.`: Matches any character except a newline.


```python
# Keep only alphanumeric characters

pattern = r'[^a-zA-Zo-9]+'
s = re.sub(pattern, '', s)

```

Modifiers include:

* `*`: Causes the resulting RE to match 0 or more repetitions of the preceding RE, as many repetitions as are possible. `ab*` will match ‘a’, ‘ab’, or ‘a’ followed by any number of ‘b’s.
* `+`: Causes the resulting RE to match 1 or more repetitions of the preceding RE. `ab+` will match ‘a’ followed by any non-zero number of ‘b’s; it will not match just ‘a’.
* `?`: Causes the resulting RE to match 0 or 1 repetitions of the preceding RE. ab? will match either ‘a’ or ‘ab’
* `*?`, `+?`, `??`: The `*`, `+`, and `?` qualifiers are all greedy; they match as much text as possible. Sometimes this behaviour isn’t desired; if the RE `<.*>` is matched against `<a> b <c>`, it will match the entire string, and not just `<a>`. Adding `?` after the qualifier makes it perform the match in non-greedy or minimal fashion; as few characters as possible will be matched. Using the RE `<.*?>` will match only `<a>`
* `{m}`: Specifies that exactly m copies of the previous RE should be matched; fewer matches cause the entire RE not to match. For example, `a{6}` will match exactly six 'a' characters, but not five.
* `[]`: Used to indicate a set of characters.


## Functions

### Arguments
There are keyword and positional arguments.  Usually denoted by `*args` and `**kwargs`. They allow you to pass an unspecified number of arguments to a function.

The asterisk is an unpacking operator.

#### *args (non-keyword argument)
`*args` is used to send a non-keyworded variable length argument list to the function.  For example, lists and tuples.

```python
def my_sum(*args):
    result = 0
    # Iterating over the Python args tuple
    for x in args:
        result += x
    return result

print(my_sum(1, 2, 3))
# 6

def myFun(*argv): 
    for arg in argv: 
        print (arg)
   
myFun('Hello', 'Welcome', 'to', 'GeeksforGeeks') 
# Hello
# Welcome
# to
# GeeksforGeeks
```

#### **kwargs (keyword argument)
`**kwargs` allows you to pass keyworded variable length of arguments to a function. You should use `**kwargs` if you want to handle named arguments in a function.  For example, dictionaries.

```python
def intro(**data):
    print("\nData type of argument:", type(data))

    for key, value in data.items():
        print("{} is {}".format(key, value))

intro(Firstname="Sita", Lastname="Sharma", Age=22, Phone=1234567890)
intro(Firstname="John", Lastname="Wood", Email="johnwood@nomail.com", Country="Wakanda", Age=25, Phone=9876543210)

# Data type of argument: <class 'dict'>
# Firstname is Sita
# Lastname is Sharma
# Age is 22
# Phone is 1234567890

# Data type of argument: <class 'dict'>
# Firstname is John
# Lastname is Wood
# Email is johnwood@nomail.com
# Country is Wakanda
# Age is 25
# Phone is 9876543210
```

#### Ordering
When defining a function, the order is as follows
1. positional arguments
2. `*args`
3. `**kwargs`

```python
def example2(arg_1, arg_2, *args, kw_1="shark", kw_2="blobfish", **kwargs):
    pass
```

## Lambda Functions
Lambda functions are also known as anonymous functions.

```python
x = lambda a : a + 10
print(x(5)) # 15
```

### reduce(), filter(), map()

Functional programming is commonly used with lambda functions. For some functions in Python 3, you need to import the `functools` module.


#### reduce()

`reduce()` implements a mathematical technique commonly known as folding or reduction. You’re doing a fold or reduction when you reduce a list of items to a single cumulative value. Python’s `reduce()` operates on any iterable. 

* Code outline: `functools.reduce(function, iterable[, initializer])`

```python
from functools import reduce

print(reduce(lambda x, y: x + y, [1, 2, 3, 4]))
# 1 + 2 + 3 + 4 = 10

print(reduce(lambda x, y: x * y, [1, 2, 3, 4]))
# 1 * 2 * 3 * 4 = 24

```

#### filter()

The `filter()` method constructs an iterator from elements of an iterable for which a function returns true.

* Code outline: `filter(function, iterable)`

```python
# list of letters
letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']

# function that filters vowels
def filter_vowels(letter):
    vowels = ['a', 'e', 'i', 'o', 'u']

    if letter in vowels:
        return True
    else:
        return False

filtered_vowels = filter(filter_vowels, letters)

print('The filtered vowels are:')
for vowel in filtered_vowels:
    print(vowel)
    
# The filtered vowels are:
# a
# e
# i
# o
```


#### map()
The `map()` function applies a given function to each item of an iterable (list, tuple etc.) and returns a list of the results.

* Code outline: `map(function, iterable)`

```python

# function that filters vowels
def calculateSquare(n):
    return n*n

numbers = (1, 2, 3, 4)
result = map(calculateSquare, numbers)

# converting map object to list
numbersSquare = list(result)
print(numbersSquare)

# <map object at 0x7f722da129e8>
# [1, 4, 9, 16]
```


## Iterators, Generators, and Decorators

### Iterators
An iterator is simply any object that you can iterate over.

Iterators implement the `__next__()` and `__iter__()` methods.

```python
# define a list
my_list = [4, 7, 0, 3]

# get an iterator using iter()
my_iter = iter(my_list)

# iterate through it using next()

# Output: 4
print(next(my_iter))

# Output: 7
print(next(my_iter))
```

Or you can use a `for` loop.

```python
for element in my_list:
    print(element)
```

### Generators
Python generators are a way of creating iterators.

A generator is a function that returns an object (iterator) which we can iterate over (one value at a time).

A generator is like a normal function, but with a `yield` statement instead of a `return` statement.

The difference is that while a `return` statement terminates a function entirely, a `yield` statement pauses the function saving all its states and later continues from there on successive calls.

```python
def rev_str(my_str):
    length = len(my_str)
    for i in range(length - 1, -1, -1):
        yield my_str[i]

# For loop to reverse the string
for char in rev_str("hello"):
    print(char)
    
# o
# l
# l
# e
# h    
```

Generators have lazy execution (producing items only when asked for). For this reason, a generator expression is much more memory efficient than an equivalent list comprehension.

```python
my_list = [2, 5, 9]

generator = (x**2 for x in my_list)
print(next(generator))
print(next(generator))

# 4
# 25
```

Why Implement Generators?
  1. Easy to implement
  2. Memory Efficient
  3. Represent Infinite Stream
  4. Pipelining Generators

```python
def fibonacci_numbers(nums):
    x, y = 0, 1
    for _ in range(nums):
        x, y = y, x+y
        yield x

def square(nums):
    for num in nums:
        yield num**2

print(sum(square(fibonacci_numbers(10))))
# 4895
```

### Decorators

A decorator takes in a function, adds some functionality and returns it.  This is also called metaprogramming because a part of the program tries to modify another part of the program at compile time.

Decorators are commonly used in areas such as authorization, logging, and test performance.


## Syntatic Sugar and Other

### Math

Integer division can be done using the `//` operator, i.e. the floor operator.

```python
22 // 7 
# 3

30 // 4
# 7

x += 1 # same as x = x + 1
x -= 1
```
Modulus operator is denoted by `%`.  This gives the remainder.

`bin()` will convert a base 10 number into its binary representation (as a string). Note, this will be prefixed with a '0b'.

```python
bin(2) # 0b10

bin(33) # 0b100001

int(bin(33)[2:]) # 100001
```

To convert a binary (base 2) number to decimal (base 10), you can do this:

```python
int('11000', 2) # 24
```

The `divmod()` method takes two numbers and returns a pair of numbers (a tuple) consisting of their quotient and remainder: `divmod(numerator, denomator)`.


```python
q, r = divmod(22, 3)
# q = 7
# r = 1
```

#### Permutations and Combinations

Order matters in permutation while it does not in a combination.

```python
from itertools import permutations
from itertools import combinations

perm = permutations([1, 2, 3], 2)
for i in list(perm):
    print(i)

# (1, 2)
# (1, 3)
# (2, 1)
# (2, 3)
# (3, 1)
# (3, 2)

comb = combinations([1, 2, 3], 2)
for i in list(comb):
    print(i)

# (1, 2)
# (1, 3)
# (2, 3)
```

### Try Except

* `try`: Try to run this code.
* `except`: Execute this code when there is an exception.
* `else`: No exceptions? Then run this code.
* `finally`: Always run this code.

```python
def divide(x, y):
    try:
        # Floor division : Gives only fractional
        # part as answer
        result = x // y
    except ZeroDivisionError:
        print("Sorry! You are dividing by zero.")
    else:
        print("Yeah! Your answer is:", result)
    finally: 
        # this block is always executed  
        # regardless of exception generation. 
        print('This is always executed.')  
 
# Look at parameters and note the working of Program
divide(3, 2)
divide(3, 0)

# Yeah! Your answer is: 1
# This is always executed.
# Sorry! You are dividing by zero.
# This is always executed.
```

You can also raise exceptions and catch specific exceptions.

### Assert

The `assert` statement enables you to verify if a certain condition is met and will throw an exception if it isn’t.

```python
x = "hello"

# if condition returns True, then nothing happens:
assert x == "hello"

# if condition returns False, AssertionError is raised:
assert x == "goodbye"

# Traceback (most recent call last):
#   File "<string>", line 7, in <module>
# AssertionError
```

### Any and All
The `any(iterable)` and `all(iterable)` are built-in functions in Python.  They are equivalent to writing a series of `or` and `and` operators respectively between each of the elements of the passed iterable.

```python
any([True, False, False, False])
# True

all([True, True, True, False])
# False
```

### Max and Min
The Python `max()` function returns the largest item in an iterable. It can also be used to find the largest item between two or more parameters.

`max(iterable, *iterables, key, default)`

* iterable: an iterable such as a list, tuple, set, dictionary, etc.
* *iterables (optional): any number of iterables; can be more than one.
* key (optional): key function where the iterables are passed and comparison is performed based on its return value.
* default (optional): default value if the given iterable is empty.

```python
square = {2: 4, -3: 9, -1: 1, -2: 4}

# the largest key
key1 = max(square)
print("The largest key:", key1) # 2

# the key whose value is the largest
key2 = max(square, key = lambda k: square[k])
key2 = max(square, key = square.get)

print("The key with the largest value:", key2) # -3

# getting the largest value
print("The largest value:", square[key2]) # 9
```

### Zip

The `zip()` function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together, etc.

```python
a = ["John", "Charles", "Mike"]
b = ["Jenny", "Christy", "Monica", "Vicky"]

x = zip(a, b)

for i in x:
    print(i) # i is of type tuple

# ('John', 'Jenny')
# ('Charles', 'Christy')
# ('Mike', 'Monica')
```

Note: If there are more pairs, the ones at the end are ignored.

### Type Hinting

Python supports [type hints](https://docs.python.org/3/library/typing.html).

For example, the function below takes and returns a string and is annotated as follows:

```python
def greeting(name: str) -> str:
    return 'Hello ' + name
```

Use spaces around the `=` sign when combining an argument annotation with a default value `(align: bool = True)`.

Note: these are just hints, and do **not** actually force any type since Python is a dynamically typed language.

### Walrus Operator

The `:=` operator gives you a new syntax for assigning variables in the middle of expressions. This operator is colloquially known as the walrus operator.

The walrus operator is only available in Python 3.8+.

### collections.Counter()

A mapping that holds an integer count for each key. Updating an existing key adds to its count.

```python
ct = collections.Counter('abracadabra')
print(ct)
# Counter({'a': 5, 'b': 2, 'r': 2, 'c': 1, 'd': 1})
```

## Bitwise Operators
In Python, bitwise operators are used to perform bitwise calculations on integers. The integers are first converted into binary and then operations are performed on bit by bit, hence the name bitwise operators. Then the result is returned in decimal format.

If you XOR the same number together, it cancels out:

```python
nums = [2,4,5,4,3,5,2]

# XORing everything together
= 2 ^ 4 ^ 5 ^ 4 ^ 3 ^ 5 ^ 2
= (2^2) ^ (4^4) ^ (5^5) ^ 3
= 0 ^ 0 ^0 ^ 3
= 3
```

Example leetcode question: [136. Single Number](https://leetcode.com/problems/single-number/).

## Sorting
A simple ascending sort is easy; just call the `sorted()` function. It returns a new sorted list.  The original list is not changed. 

```python
sorted([5, 2, 3, 1, 4]) # [1, 2, 3, 4, 5]
```

You can also use the `list.sort()` method. It modifies the list in-place (and **returns None** to avoid confusion). Usually it’s less convenient than `sorted()` - but if you don’t need the original list, it’s slightly more efficient.  Can also take the `reverse` and `key` arguments.

```python
a = [5, 2, 3, 1, 4]
a.sort()
a # [1, 2, 3, 4, 5]
```

The `sorted()` function can be customized through optional arguments. The `sorted()` optional argument `reverse=True`, e.g. `sorted(my_list, reverse=True)`, makes it sort backwards.

For more complex custom sorting, `sorted()` takes an optional `key=` specifying a "key" function that transforms each element before comparison. The key function takes in 1 value and returns 1 value, and the returned "proxy" value is used for the comparisons within the sort.  For example, you can sort elements of the list by length by passing in `key=len`.

```python
lst = [('candy', 32, '100'), ('apple', 8, '200'), ('baby', 20, '300')]
print(sorted(lst, key=lambda x: x[1]))
# [('apple', 8, '200'), ('baby', 20, '300'), ('candy', 32, '100')]

# The below two are equivalent, will sort in reverse order
print(sorted(lst, key=lambda x: -x[1]))
print(sorted(lst, key=lambda x: x[1], reverse=True))
# [('candy', 32, '100'), ('baby', 20, '300'), ('apple', 8, '200')]
```

*[Timsort](https://en.wikipedia.org/wiki/Timsort)* is the sorting algorithm used by Python.

`sorted()` on a string returns the list of characters of a string sorted. You will need to call `join()` if you want a string again.

```python
''.join(sorted('string to sort alphabetically'))
# aaabceghiilllnooprrsstttty
```

## Reversing

In Python, reversing items can be done:
* Using the slicing method: `some_var[::-1]`.
* Using `reversed(some_var)`.
* Using `some_var.reverse()` which reverses the elements of the list in place.

[Note](https://www.geeksforgeeks.org/python-reversed-vs-1-which-one-is-faster/): For a comparatively large list, under time constraints, it seems that the `reversed()` function performs faster than the slicing method. This is because `reversed()` just returns an iterator that iterates the original list in reverse order, without copying anything whereas slicing creates an entirely new list, copying every element from the original list. For a list with 106 values, the `reversed()` performs almost 20,000 better than the slicing method. If there is a need to store the reverse copy of data then slicing can be used but if one only wants to iterate the list in reverse manner, `reversed()` is definitely the better option.

## Data Structures and Types
The [official](https://docs.python.org/3/tutorial/datastructures.html) Python documentation has good notes on this. A brief summary is provided below.

### Linked Lists
A [linked list](https://en.wikipedia.org/wiki/Linked_list) is a linear collection of data elements whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which together represent a sequence.

Linked Lists can be used to implement queues or stacks as well as graphs.


### Hash tables
See [dictionary](#dictionary) section of notes.

### Stacks
A stack is a data structure that stores items in an Last-In/First-Out (LIFO) manner.

A stack in Python can be implemented with:
* `list`: However, can run into speed issues as it grows.
* `Collections.deque`: Deque is preferred over the `list` in the cases where we need quicker append and pop operations from both the ends of the container, as deque provides an `O(1)` time complexity for append and pop operations as compared to list which provides `O(n)` time complexity. 
* `queue.LifoQueue`: Usually used for thread communication operations.

```python
from Collections import deque
 
stack = deque()
stack.append('a')
stack.append('b')
stack.pop()
```

### Queues
A queue stores items in a First-In/First-Out (FIFO) manner.

#### Priority Queues
A [priority queue](https://en.wikipedia.org/wiki/Priority_queue) is an abstract data type similar to a regular queue or stack data structure in which each element additionally has a "priority" associated with it.

The items in the queue must be able to be assigned a priority.

#### Double Ended Queue

A double-ended queue, or deque, has the feature of adding and removing elements from either end. The `deque` module is a part of collections library.

### Heaps
A [heap](https://en.wikipedia.org/wiki/Heap_(data_structure)) is a specialized tree-based data structure which is essentially an almost complete tree that satisfies the heap property:
* Max heap:  for any given node C, if P is a parent node of C, then the key (the value) of P is greater than or equal to the key of C
* Min heap: the key of P is less than or equal to the key of C

The node at the "top" of the heap (with no parents) is called the root node.

The heap is one maximally efficient implementation of an abstract data type called a [priority queue](#priority-queues).

Heaps are usually implemented with an array, as follows:
 * Each element in the array represents a node of the heap, and
 * The parent / child relationship is defined implicitly by the elements' indices in the array.

 In Python, there is the `heapq` module that implements a priorty queue using a binary heap.

 ```python
import heapq

my_list = [5, 7, 9, 1, 3]

# Make list into heap (smallest has default highest priority)
heapq.heapify(my_list)

# Push element into min-heap
heapq.heappush(my_list, 9) # [1, 3, 4, 7, 5, 9]

# Pop an element (with the highest priority)
popped = heapq.heappop(my_list)
# popped is 1

 ```

 Note you can implement a [max heap](https://stackoverflow.com/questions/2501457/what-do-i-use-for-a-max-heap-implementation-in-python) in python using the negative of a list.  The heap is not necessarily sorted - but it does satisfy the heap property.

### Binary Search Tree

[Binary Search Tree](https://en.wikipedia.org/wiki/Binary_search_tree) (BST) is a node-based binary tree data structure which has the following properties:  

* The left subtree of a node contains only nodes with keys lesser than the node’s key.
* The right subtree of a node contains only nodes with keys greater than the node’s key.
* The left and right subtree each must also be a binary search tree. 
* There must be no duplicate nodes.

```python
# Definition for a binary tree node.
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

# Searching
# Worst case O(n)
def searchBST(self, root: TreeNode, val: int) -> TreeNode:
    if not root:
        return None
    if root.val == val:
        return root
    elif root.val > val:
        return self.searchBST(root.left, val)           
    else:
        return self.searchBST(root.right, val)

# can also implement an iterative approach with search

```
## Algorithms

### Depth First Search
Depth-first search (DFS) is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.

If we are performing a search of a particular element, then at each step, a comparison operation will occur with the node we are currently at.

Example: DFS of a binary tree

### Breadth First Search


### Binary Search

This is provided by the `bisect` module.

## Dynamic Programming

Dynamic Programming is mainly an optimization over plain recursion. Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming. The idea is to simply store the results of subproblems, so that we do not have to re-compute them when needed later.

## Recursion

Recursion is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem.

This can be used to solve problems such as [(509. Fibonnaci Number)](https://leetcode.com/problems/fibonacci-number/).

```python
def fib(n: int) -> int:
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
# Time complexity: O(C)^n, exponential

# Here is an iterative approach (faster).
# This actually is a form of dynamic programming.
def fib(n: int) -> int:
    a, b = 0, 1

    for i in range(n):
        result = a + b
        a, b = b, result
    
    return a
# Time complexity: O(n)
```

## Time Complexity

### Big O Notation

Given n, the size of the input to the algorithm, Big O notation represents the relationship between n and the number of steps the algorithm takes to find a solution.

We have (in increasing complexity): 
* O(1): Constant
* O(logn): Logarithmic
* O(n): Linear
* O(nlogn): Log-linear
* O(n<sup>2</sup>): Quadratic
* O(2<sup>n</sup>): Exponential
* O(n!): Factorial

### Time complexity of built-ins

The [complexity](https://stackoverflow.com/questions/13884177/complexity-of-in-operator-in-python) of `in` depends entirely on what `L` is. `e in L` will become `L.__contains__(e)`.

See this time [complexity document](https://wiki.python.org/moin/TimeComplexity) for the complexity of several built-in types.

Here is the summary for `in`:  

* list - Average: O(n)
* set/dict - Average: O(1), Worst: O(n)

The O(n) worst case for sets and dicts is very uncommon, but it can happen if `__hash__` is implemented poorly. This only happens if everything in your set has the same hash value.

* Python's built-in `sorted()` has a time complexity of O(nlogn)
* Python's built-in `.count()` on lists has a time complexity of O(n)
* Python's built-in `.reverse()` on lists has a time complexity of O(n)
* Python's built-in `.min()` and `.max()` on lists has a time complexity of O(n)
* Python's built-in `.split()` on strings has a time complexity of O(n), if splitting on whitespace.

Note Python's set is implemented as a hash table so lookup/insert/delete is `O(1)` average and `O(n)` worst.

## Space Complexity

The [space complexity](https://en.wikipedia.org/wiki/Space_complexity) of an algorithm or a computer program is the amount of memory space required to solve an instance of the computational problem as a function of characteristics of the input. It is the memory required by an algorithm to execute a program and produce output.


## Object Oriented Programming

### Classes

```python
class Person:
    # class variable
    human = True

    def __init__(self, name, age):
        # instance variables
        self.name = name
        self.age = age

    def myfunc(self):
        print("Hello my name is " + self.name)


p1 = Person("John", 36)
p1.myfunc()
print(p1.age) # 36
print(p1.human) # True
print(Person.human) # will also be True, don't need to instantiate a class to access a class variable

```
There are also [built-in](https://docs.python.org/3/library/functions.html) functions like `repr()` or `str()` that you can override in a class.

## Pandas

A library in python that is useful for displaying tabular data.

Remember to `import pandas as pd`

### Creating DataFrames
```python
# From a dict
d = {'col1': [1, 2], 'col2': [3, 4]}
df = pd.DataFrame(data=d)

# From a list
lst = [['tom', 25], ['krish', 30], 
       ['nick', 26], ['juli', 22]] 
df = pd.DataFrame(lst, columns =['Name', 'Age']) 

```

To copy a dataframe, it is recommend to do a deep copy.

```python
df_copy = df.copy(deep=True)
```

### Selecting

```python
d = {'col1': [1, 2], 'col2': [3, 4]}

# Select some columns
d[['col1', 'col2]]

```

### Dates and Times
* Datetime can be converted using `pd.to_datetime()`

## NumPy

A library (`numpy`) in Python that is useful for mathematical operations (particularly vector operations).  

The core functionality of NumPy is its "ndarray", n-dimensional array, data structure. These arrays are strided views on memory. In contrast to Python's built-in `list` data structure, these arrays are homogeneously typed: all elements of a single array must be of the same type. 

## References

* [Google for Education > Python](https://developers.google.com/edu/python)
* [Progamiz](https://www.programiz.com/)
    * [args and kwargs](https://www.programiz.com/python-programming/args-and-kwargs)
    * [del](https://www.programiz.com/python-programming/del)
* [Real Python](https://realpython.com/)
    * [Sets](https://realpython.com/python-sets/)
    * [map](https://www.programiz.com/python-programming/methods/built-in/map)
    * [Walrus Operator](https://realpython.com/python-walrus-operator/)
* [Geeks For Geeks](https://www.geeksforgeeks.org/)
    * [Try Except](https://www.geeksforgeeks.org/try-except-else-and-finally-in-python/)
* [Base N conversions](https://www.dcode.fr/base-n-convert)
* [W3Schools](https://www.w3schools.com/python)
  * [assert keyword](https://www.w3schools.com/python/ref_keyword_assert.asp)
  * [zip](https://www.w3schools.com/python/ref_func_zip.asp)
* [Wikipedia Numpy](https://en.wikipedia.org/wiki/NumPy)
* StackOverflow
  * [StackOverFlow how does collections defaultdict work](https://stackoverflow.com/questions/5900578/how-does-collections-defaultdict-work)
* [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-args-and-kwargs-in-python-3)
* [GCoder: 3 Python practice interview questions](https://gdcoder.com/interview-coding-problems-1-implement-trie-prefix-tree-2-longest-substring-with-at-most-k-distinct-characters-3-3sum/)
* [Python Gotcha's](https://docs.python-guide.org/writing/gotchas/)
* Fluent Python by Luciano Ramalho
* [Python.org tutorial](https://docs.python.org/3/tutorial/)

Materials taken from various other websites too (used only for educational purposes).