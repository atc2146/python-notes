# Python Notes

Notes and references on Python. Taken from various places on the internet.

## Table of Contents
* [Strings](#Strings)
    * [String Methods](#String-Methods)
    * [String Slices](#String-Slices)
    * [f-Strings](#f-Strings)
* [Data Structures](#data-structures)
* [Lists](#Lists)
    * [List Comprehension](#List-Comprehension)
    * [List Methods](#List-Comprehension)
    * [Creating Lists](#Creating-Lists)
* [Dictionaries](#Dictionaries)
    * [Iterating](#Iterating)
    * [Searching for a key](#Searching-for-a-key)
    * [The setdefault() method](#The-setdefault-method)
* [Tuples](#tuples)
* [Sets](#sets)
* [Regex](#Regex)
* [Lambda Functions](#Lambda-Functions)
    * [reduce(), filter(), map()](#reduce-filter-map)
        * [reduce()](#reduce)
        * [filter()](#filter)
        * [map()](#map)
* [Sorting](#Sorting)
* [Algorithms](#Algorithms)
    * [Hash Tables](#Hash-tables)
* [Time complexity](#Time-complexity)
    * [Time complexity of built-ins](#time-complexity-of-built-ins)
* [Space complexity](#Space-complexity)
* [Object Oriented Programming](Object-Oriented-Programming)
    * [Classes](#Classes)
* [Pandas](#Pandas)
    * [Selecting](#Selecting)
* [NumPy](#NumPy)
* [References](#References)

 
## Strings
A "raw" string literal is prefixed by an 'r' and passes all the chars through without special treatment of backslashes, so `r'x\nx'` evaluates to the length-4 string 'x\nx'.

### String Methods
* `s.split('delim')`: returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text. `'aaa,bbb,ccc'.split(',')` -> ['aaa', 'bbb', 'ccc']. As a convenient special case `s.split()` (with no arguments) splits on all whitespace chars.
* `s.join(list)`: opposite of `split()`, joins the elements in the given list together using the string as the delimiter. e.g. `'---'.join(['aaa', 'bbb', 'ccc'])` -> aaa---bbb---ccc
* `s.count()`: In simple words, `count()` method searches the substring in the given string and returns how many times the substring is present in it.  The syntax is: `string.count(substring, [start=...], [end=...])`

### String Slices
The "slice" syntax is a handy way to refer to sub-parts of sequences -- typically strings and lists. The slice `s[start:end]` is the elements beginning at start and extending up to but not including end.

You can reverse a string (or list) with the following slice:
```python
my_string = 'a string'

my_string[::-1]
```
### f-Strings
A convenient way to format strings with variables.

```python
name = 'Eric'
age = 74

print(f'Hello, {name}. You are {age}.') ## Hello, Eric. You are 74.
``` 
## Data Structures
The [official](https://docs.python.org/3/tutorial/datastructures.html) Python documentation has good notes on this. A brief summary is provided below.

## Lists
To iterate over a list with an index and value:  

```python
my_list = ['Team A', 'Team Bobcats', 'Team XYZ']

for ind, val in enumerate(my_list):
    print(ind, val)
```

### List Comprehension
The syntax is: *[expr for var in list {optional if expr}]*

```python
my_list = [1,2,3,4]

[i*i for i in my_list if i%2==0]
```

### List Methods  

* The `insert()` method inserts an element to the list at the specified index.
* The `pop()` method removes the item at the given index from the list and returns the removed item.
    * You can also have an index at a negative value. This will count backwards from the list.
    * Pop without an index removes the last element of the list.
* The `remove()` method removes the first matching element (which is passed as an argument) from the list.
    * Returns None
    * If the element doesn't exist, it throws a ValueError.
* The `count()` method returns the number of times the specified element appears in the list.
* The `index()` method returns the index of the specified element in the list.

```python
my_list = [1,2,3,4]

my_list.insert(index, element)

popped_item = my_list.pop(index)

my_list.remove(element)

my_list.count(element)

my_list.index(element, [start], [end])
```


### Creating Lists
If you want to create a list.

```python
my_list = ['bob']*3

my_list = list(range(2,20,3))
```


## Dictionaries

This is essentially Python's version of a Hash Table.  Dictionaries have key value pairs.  The keys in the dictionary need to be hashable.  For example, lists cannot be used as keys as they are not hashable.  The actual implementation is pretty interesting - read about it [here](https://docs.python.org/3/faq/design.html#how-are-dictionaries-implemented-in-cpython).

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

# delete a key
del my_dict['bob]

# clear dictionary
my_dict.clear()
```

### Iterating
To iterate over a dictionary:

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

for k, v in my_dict.items():
    print(k, v)
```
### Searching for a key
Searching for a key:
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

if key in my_dict:
    print(str(key) + ' exists')
```

There is also the `get()` method.  This method returns a value for the given key. If the key is not available, then returns default value None.
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

my_dict.get(key):
```

### The setdefault() method
The `setdefault()` method returns the value of the item with the specified key. If the key does not exist, insert the key, with the specified value: `dictionary.setdefault(keyname, value)`

## Tuples
A tuple is a collection of objects which are ordered and **immutable**.

```python
some_tuple = (1, )
another_tuple = ('a', 'b', 2)

```

## Sets
A set is an unordered collection with no duplicate elements. Basic uses include membership testing and eliminating duplicate entries. Set objects also support mathematical operations like union, intersection, difference, and symmetric difference.  

Curly braces or the `set()` function can be used to create sets. Note: to create an empty set you have to use `set()`, not `{}`.

```python
ages = {1, 22, 38}
empty_set = set()

a = set('abracadabra')  # {'a', 'r', 'b', 'c', 'd'}

```

A set has a significantly faster `in` search than lists.  This is because sets finds the element by computing a hash from the key - whearas, in general, the whole list needs to be searched.  Both have O(1) time complexity, however.

Lists are faster (in general) when you are iterating over values, however.  This performance increases if you sort the list.

## Regex
For Python regular expressions, you need to import the `re` module.  

```python
pattern = r'some string'
string = 'this is some string'

re.search(pattern, string)
re.findall(pattern, string)
```


## Lambda Functions
Lambda functions are known as anonymous functions.


### reduce(), filter(), map()

Functional programming that is commonly used with lambda functions. In Python 3, you need to `import functools`.


#### reduce()

`reduce()` implements a mathematical technique commonly known as folding or reduction. You’re doing a fold or reduction when you reduce a list of items to a single cumulative value. Python’s reduce() operates on any iterable. Code outline: `functools.reduce(function, iterable[, initializer])`

```python
import functools 

print(reduce(lambda x, y: x + y, [1, 2, 3, 4]))
# 1 + 2 + 3 + 4 = 10
```

#### filter()


#### map()

## Sorting
A simple ascending sort is very easy: just call the `sorted()` function. It returns a new sorted list.  The original list is not changed. 

```python
sorted([5, 2, 3, 1, 4])         ## [1, 2, 3, 4, 5]
```

You can also use the `list.sort()` method. It modifies the list in-place (and **returns None** to avoid confusion). Usually it’s less convenient than `sorted()` - but if you don’t need the original list, it’s slightly more efficient.

```python
a = [5, 2, 3, 1, 4]
a.sort()
a           ## [1, 2, 3, 4, 5]
```

The sorted() function can be customized through optional arguments. The `sorted()` optional argument reverse=True, e.g. `sorted(my_list, reverse=True)`, makes it sort backwards.

For more complex custom sorting, `sorted()` takes an optional "key=" specifying a "key" function that transforms each element before comparison. The key function takes in 1 value and returns 1 value, and the returned "proxy" value is used for the comparisons within the sort.  For example, you can sort elements of the list by length by passing in `key=len`.

## Algorithms

### Hash tables
See [dictionary](#dictionary) section of notes.



## Time complexity

### Time complexity of built-ins

The [complexity](https://stackoverflow.com/questions/13884177/complexity-of-in-operator-in-python) of `in` depends entirely on what `L` is. `e in L` will become `L.__contains__(e)`.

See this time [complexity document](https://wiki.python.org/moin/TimeComplexity) for the complexity of several built-in types.

Here is the summary for `in`:  

* list - Average: O(n)
* set/dict - Average: O(1), Worst: O(n)

The O(n) worst case for sets and dicts is very uncommon, but it can happen if `__hash__` is implemented poorly. This only happens if everything in your set has the same hash value.

* Python's built-in `sorted()` has a time complexity of O(nlogn)
* Python's built-in `.count()` on lists has a time complexity of O(n)

## Space complexity

The space complexity of an algorithm or a computer program is the amount of memory space required to solve an instance of the computational problem as a function of characteristics of the input. It is the memory required by an algorithm to execute a program and produce output [Source](https://en.wikipedia.org/wiki/Space_complexity).


## Object Oriented Programming

### Classes
There are also functions like `repr()` or `str()` that you can override.

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def myfunc(self):
    print("Hello my name is " + self.name)

p1 = Person("John", 36)
p1.myfunc()
print(p1.age)

```

## Pandas

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

### Selecting

```python
d = {'col1': [1, 2], 'col2': [3, 4]}

# Select some columns
d[['col1', 'col2]]

```

## NumPy

A library (`numpy`) in Python that is useful for mathematical operations (particularly vector operations).  

The core functionality of NumPy is its "ndarray", for n-dimensional array, data structure. These arrays are strided views on memory. In contrast to Python's built-in list data structure, these arrays are homogeneously typed: all elements of a single array must be of the same type. 

## References

* [Google for Education > Python](https://developers.google.com/edu/python)
* [Progamiz](https://www.programiz.com/)
* [Real Python](https://realpython.com/)
* [Geeks For Geeks](https://www.geeksforgeeks.org/)
* [W3Schools](https://www.w3schools.com/python)
* [Wikipedia Numpy](https://en.wikipedia.org/wiki/NumPy)