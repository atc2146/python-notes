# Python Notes

Notes on Python.

## Table of Contents



## Strings
* A "raw" string literal is prefixed by an 'r' and passes all the chars through without special treatment of backslashes, so r'x\nx' evaluates to the length-4 string 'x\nx'.

### Methods
* s.split('delim') -- returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text. 'aaa,bbb,ccc'.split(',') -> ['aaa', 'bbb', 'ccc']. As a convenient special case s.split() (with no arguments) splits on all whitespace chars.
* s.join(list) -- opposite of split(), joins the elements in the given list together using the string as the delimiter. e.g. '---'.join(['aaa', 'bbb', 'ccc']) -> aaa---bbb---ccc

### String Slices
The "slice" syntax is a handy way to refer to sub-parts of sequences -- typically strings and lists. The slice s[start:end] is the elements beginning at start and extending up to but not including end.

You can reverse a string (or list) with the following slice:
```python
my_string = 'a string'

my_string[::-1]
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


## Dictionaries

*This is essential a Hash Table  

To iterate over a dictionary:

```python
my_dict = { 'bob': 20, 'james': 33, 'mary': 18}

for k, v in my_dict.items():
	print(k, v)
```

## Sorting
A simple ascending sort is very easy: just call the sorted() function. It returns a new sorted list.  The original list is not changed.

```python
sorted([5, 2, 3, 1, 4]) 	## [1, 2, 3, 4, 5]
```

You can also use the list.sort() method. It modifies the list in-place (and **returns None** to avoid confusion). Usually it’s less convenient than sorted() - but if you don’t need the original list, it’s slightly more efficient.

```python
a = [5, 2, 3, 1, 4]
a.sort()
a						## [1, 2, 3, 4, 5]
```

The sorted() function can be customized through optional arguments. The sorted() optional argument reverse=True, e.g. sorted(my_list, reverse=True), makes it sort backwards.

For more complex custom sorting, sorted() takes an optional "key=" specifying a "key" function that transforms each element before comparison. The key function takes in 1 value and returns 1 value, and the returned "proxy" value is used for the comparisons within the sort.



## Time complexity
* https://stackoverflow.com/questions/13884177/complexity-of-in-operator-in-python
* https://wiki.python.org/moin/TimeComplexity

## Notes
* [Google for Education > Python](https://developers.google.com/edu/python)
