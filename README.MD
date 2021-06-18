# Python Notes

Notes and references on Python. Taken from various places on the internet.

## Table of Contents
* [Strings](#Strings)
    * [String Methods](#String-Methods)
    * [String Slices](#String-Slices)
    * [f-Strings](#f-Strings)
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
* [Deletion](#deletion)
* [Regex](#Regex)
* [Functions](#Functions)
    * [Arguments](#Arguments)
        * [*args](#args-non-keyword-argument)
        * [**kwargs](#kwargs-keyword-argument)
        * [Ordering](#ordering)
* [Lambda Functions](#Lambda-Functions)
    * [reduce(), filter(), map()](#reduce-filter-map)
        * [reduce()](#reduce)
        * [filter()](#filter)
        * [map()](#map)
* [Iterators, Generators, and Decorators](#iterators-generators-and-decorators)
    * [Iterators](#iterators)
    * [Generators](#generators)
    * [Decorators](#decorators)
* [Syntatic Sugar and Other](#syntatic-sugar-and-other)
    * [Try Except](#try-except)
    * [Any and All](#any-and-all)
    * [Max And Min](#max-and-min)
    * [Zip](#zip)
    * [Type Hinting](#type-hinting)
* [Sorting](#Sorting)
* [Data Structures](#data-structures)
    * [Queues](#queues)
        * [Priority Queues](#priority-queues)
    * [Hash Tables](#Hash-tables)
    * [Heaps](#Heaps)
    * [Binary Search Tree](#binary-search-tree)
* [Algorithms](#Algorithms)
    * [Depth First Search](#depth-first-search)
    * [Breadth First Search](#breadth-first-search)
* [Dynamic Programming](#dynamic-programming)
* [Recursion](#recursion)
* [Time complexity](#Time-complexity)
    * [Big O Notation](#big-o-notation)
    * [Time complexity of built-ins](#time-complexity-of-built-ins)
* [Space complexity](#Space-complexity)
* [Object Oriented Programming](#object-oriented-programming)
    * [Classes](#Classes)
* [Pandas](#Pandas)
    * [Selecting](#Selecting)
* [NumPy](#NumPy)
* [References](#References)

 
## Strings
A "raw" string literal is prefixed by an 'r' and passes all the chars through without special treatment of backslashes, so `r'x\nx'` evaluates to the length-4 string 'x\nx'.

### String Methods
* `s.split('delim')`: returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text.
  * `'aaa,bbb,ccc'.split(',')` -> `['aaa', 'bbb', 'ccc']`.
  * As a convenient special case `s.split()` (with no arguments) splits on all whitespace chars.
* `s.join(list)`: opposite of `split()`, joins the elements in the given list together using the string as the delimiter.
  * Example: `'---'.join(['aaa', 'bbb', 'ccc'])` -> `aaa---bbb---ccc`
* `s.count()`: In simple words, `count()` method searches the substring in the given string and returns how many times the substring is present in it.
  * The syntax is: `string.count(substring, [start=...], [end=...])`

### String Slices
The "slice" syntax is a handy way to refer to sub-parts of sequences -- typically strings and lists. The slice `s[start:end]` is the elements beginning at start and extending up to but not including the end.

String slices can also take a 3rd argument, the stride, `str_[start:stop:stride]`

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
    * Returns `None`
    * If the element doesn't exist, it throws a `ValueError`.
    * If a list contains duplicate elements, the `remove()` method only removes the first matching element.
* The `count()` method returns the number of times the specified element appears in the list.
* The `index()` method returns the index of the specified element in the list.

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
 Slicing creates a shallow copy of the original list.

### Creating Lists
If you want to create a list.

```python
my_list = ['bob']*3 # can't be an empty list
# ['bob', 'bob', 'bob']

[1,2] * 2
# [1,2,1,2]

[[1,2] for i in range(0, 2)]
# [[1, 2], [1, 2]]

my_list = list(range(2,20,3)) # last argument is stride
# [2, 5, 8, 11, 14, 17]
```

### Adding Lists
Adding lists in Python is **not** done element wise.

```python
[1,2] + [1,1]
# [1, 2, 1, 1]
```

## Dictionaries

This is essentially Python's version of a Hash Table.  Dictionaries have key value pairs.  The keys in the dictionary need to be hashable.  For example, lists cannot be used as keys as they are not hashable.  The actual implementation is pretty interesting - read about it [here](https://docs.python.org/3/faq/design.html#how-are-dictionaries-implemented-in-cpython).

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

# delete a key
del my_dict['bob]

# clear dictionary
my_dict.clear()

# list keys
my_dict.keys()

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
```
### Searching for a key
Searching for a key:
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

if key in my_dict:
    print(str(key) + ' exists')
```

There is also the `get()` method.  This method returns a value for the given key. If the key is not available, then returns default value `None`.
```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}
key = 'bob'

my_dict.get(key):

# if you want to specify a default value if key cannot be found
my_dict.get(key, 'DEFAULT_VAL')
```

If you try to access a key that does not exist, an error with be thrown:

```python
my_dict = {'bob': 20, 'james': 33, 'mary': 18}

my_dict['obama']
# Will throw an error
```



### Sorting a dictionary

```python
x = {1: 2, 3: 4, 4: 3, 2: 1, 0: 0}

sorted_list = sorted(x.items(), key = lambda i: i[1])
#  [(0, 0), (2, 1), (1, 2), (4, 3), (3, 4)]

dict(sorted_list)
# {0: 0, 2: 1, 1: 2, 4: 3, 3: 4}

```

### The setdefault() method
The `setdefault()` method returns the value of the item with the specified key. If the key does not exist, insert the key, with the specified value: `dictionary.setdefault(keyname, value)`

### The defaultdict collection

If a key is not found in the dictionary, then instead of a KeyError being thrown, a new entry is created. Read [more](https://docs.python.org/3/library/collections.html#collections.defaultdict).

```python

hash_map = defaultdict(int)

```

## Tuples
A tuple is a collection of objects which are ordered and **immutable**.

```python
some_tuple = (1, )
another_tuple = ('a', 'b', 2)

```

## Sets
A set is an unordered collection with no duplicate elements. Basic uses include membership testing and eliminating duplicate entries. Set objects also support mathematical operations like union, intersection, difference, and symmetric difference.  

Curly braces or the `set()` function can be used to create sets. Note: to create an empty set you have to use `set()`, not `{}`.  The latter creates an empty dictionary.

```python
ages = {1, 22, 38}
empty_set = set()

a = set('abracadabra')  # {'a', 'r', 'b', 'c', 'd'}

```

A set has a significantly faster `in` search than lists.  This is because sets finds the element by computing a hash from the key - whereas, in general, the whole list needs to be searched.  Both have O(1) time complexity, however.

Lists are faster (in general) when you are iterating over values, however.  This performance increases if you sort the list.

Set operations include 
* `.add()`
* `.remove()`
* `.discard()`
* `.pop()`
* `.clear()`
* `.update()`
* `.union()`
* `intersection()`
* `.symmetric_difference()`
* `.isdisjoint()`
* `.issubset()`
* `.issuperset()`

A set is mutable.  However, a set cannot have mutable elements (list lists, tuples) as its element.

## Deletion
You can use the `del` keyword to delete variables, user-defined objects, lists, items within lists, dictionaries, etc.

You cannot delete tuple elements, but you can delete an entire tuple.
```python
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

# deleting the third item
del my_list[2]

# Output: [1, 2, 4, 5, 6, 7, 8, 9]
print(my_list)

# deleting items from 2nd to 4th
del my_list[1:4]

# Output: [1, 6, 7, 8, 9]
print(my_list)

# deleting all elements
del my_list[:]

# Output: []
print(my_list)

# Removing a key-value pair from a dict
person = { 'name': 'Sam',
  'age': 25,
  'profession': 'Programmer'
}

del person['profession']

# Output: {'name': 'Sam', 'age': 25}
print(person)

```

## Regex
For Python regular expressions, you need to import the `re` module.  

```python
pattern = r'some string'
string = 'this is some string'

re.search(pattern, string)
re.findall(pattern, string)
```
## Functions

### Arguments
There are keyword and positional arguments.  Usually denoted `*args` and `**kwargs`. They allow you to pass an unspecified number of arguments to a function.

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
    print("\nData type of argument:",type(data))

    for key, value in data.items():
        print("{} is {}".format(key,value))

intro(Firstname="Sita", Lastname="Sharma", Age=22, Phone=1234567890)
intro(Firstname="John", Lastname="Wood", Email="johnwood@nomail.com", Country="Wakanda", Age=25, Phone=9876543210)

# Data type of argument: <class 'dict'>
# Firstname is Sita
# Lastname is Sharma
# Age is 22
# Phone is 1234567890
# 
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



## Iterators, Generators, and Decorators

### Iterators
An iterator is just any object that you can iterate over.

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

or you can use a `for` loop.

```python
for elem in my_list:
    print(elem)
```

### Generators
Python generators are a simple way of creating iterators.

A generator is a function that returns an object (iterator) which we can iterate over (one value at a time).

A generator is simply a normal function, but with a yield statement instead of a return statement.

The difference is that while a `return` statement terminates a function entirely, `yield` statement pauses the function saving all its states and later continues from there on successive calls.

```python
def rev_str(my_str):
    length = len(my_str)
    for i in range(length - 1, -1, -1):
        yield my_str[i]

# For loop to reverse the string
for char in rev_str("hello"):
    print(char)
```

Generators have lazy execution ( producing items only when asked for ). For this reason, a generator expression is much more memory efficient than an equivalent list comprehension.

```python
generator = (x**2 for x in my_list)
print(next(a))
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
```

### Decorators


## Syntatic Sugar and Other

### Try Except

* `try`: Try to run this code
* `except`: Execute this code when there is an exception
* `else`: No exceptions? Then run this code
* `finally`: Always run this code

You can also raise exceptions and catch specific exceptions.

The `assert` statement enables you to verify if a certain condition is met and will throw an exception if it isn’t.

```python
x = "hello"

# if condition returns True, then nothing happens:
assert x == "hello"

# if condition returns False, AssertionError is raised:
assert x == "goodbye"
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

* iterable - an iterable such as list, tuple, set, dictionary, etc.
* *iterables (optional) - any number of iterables; can be more than one
* key (optional) - key function where the iterables are passed and comparison is performed based on its return value
* default (optional) - default value if the given iterable is empty

```python
square = {2: 4, -3: 9, -1: 1, -2: 4}

# the largest key
key1 = max(square)
print("The largest key:", key1)    # 2

# the key whose value is the largest
key2 = max(square, key = lambda k: square[k])

print("The key with the largest value:", key2)    # -3

# getting the largest value
print("The largest value:", square[key2])    # 9
```

### Zip

The zip() function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together etc.

```python
a = ["John", "Charles", "Mike"]
b = ["Jenny", "Christy", "Monica", "Vicky"]

x = zip(a, b)

for i in x:
	print(i) # i is type tuple

# ('John', 'Jenny')
# ('Charles', 'Christy')
# ('Mike', 'Monica')
```

Note: If there are more pairs, the ones at the end are ignored.

### Type Hinting

## Bitwise Operators
In Python, bitwise operators are used to perform bitwise calculations on integers. The integers are first converted into binary and then operations are performed on bit by bit, hence the name bitwise operators. Then the result is returned in decimal format.

## Sorting
A simple ascending sort is very easy: just call the `sorted()` function. It returns a new sorted list.  The original list is not changed. 

```python
sorted([5, 2, 3, 1, 4]) # [1, 2, 3, 4, 5]
```

You can also use the `list.sort()` method. It modifies the list in-place (and **returns None** to avoid confusion). Usually it’s less convenient than `sorted()` - but if you don’t need the original list, it’s slightly more efficient.

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
```

Timsort is the sorting algorithm used by Python.

## Data Structures
The [official](https://docs.python.org/3/tutorial/datastructures.html) Python documentation has good notes on this. A brief summary is provided below.

### Linked List


### Queues

#### Priority Queues
A [priority queue](https://en.wikipedia.org/wiki/Priority_queue) is an abstract data type similar to a regular queue or stack data structure in which each element additionally has a "priority" associated with it.

The items in the queue must be able to be assigned a priority.

### Hash tables
See [dictionary](#dictionary) section of notes.


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


## Dynamic Programming

## Recursion

## Time complexity

### Big O Notation

Given n, the size of the input to the algorithm, Big O notation represents the relationship between n and the number of steps the algorithm takes to find a solution.

We have: 
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

## Space complexity

The space complexity of an algorithm or a computer program is the amount of memory space required to solve an instance of the computational problem as a function of characteristics of the input. It is the memory required by an algorithm to execute a program and produce output.

[Source](https://en.wikipedia.org/wiki/Space_complexity)


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
There are also functions like `repr()` or `str()` that you can override.

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

### Dates and Times
* Datetime can be converted using `pd.to_datetime()`

## NumPy

A library (`numpy`) in Python that is useful for mathematical operations (particularly vector operations).  

The core functionality of NumPy is its "ndarray", for n-dimensional array, data structure. These arrays are strided views on memory. In contrast to Python's built-in list data structure, these arrays are homogeneously typed: all elements of a single array must be of the same type. 

## References

* [Google for Education > Python](https://developers.google.com/edu/python)
* [Progamiz](https://www.programiz.com/)
    * [args and kwargs](https://www.programiz.com/python-programming/args-and-kwargs)
    * [del](https://www.programiz.com/python-programming/del)
* [Real Python](https://realpython.com/)
    * [Sets](https://realpython.com/python-sets/)
* [Geeks For Geeks](https://www.geeksforgeeks.org/)
* [W3Schools](https://www.w3schools.com/python)
  * [assert keyword](https://www.w3schools.com/python/ref_keyword_assert.asp)
  * [zip](https://www.w3schools.com/python/ref_func_zip.asp)
* [Wikipedia Numpy](https://en.wikipedia.org/wiki/NumPy)
* [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-args-and-kwargs-in-python-3)
* [GCoder: 3 Python practice interview questions](https://gdcoder.com/interview-coding-problems-1-implement-trie-prefix-tree-2-longest-substring-with-at-most-k-distinct-characters-3-3sum/)

Materials taken from other websites too used only for educational purposes.