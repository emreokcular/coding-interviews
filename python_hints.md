# Python Hints:

This file contains pythonic hints and tricks that I learned during my Python journey.

## Q : What is the difference between `sort()` and `sorted()`?

Both `sort()` and `sorted()` can be used to sort a list. What is the difference between them and when would I want to use one versus the other?

## A : The primary difference between the list `sort()` function and the `sorted()` function is that the `sort()` function will modify the list it is called on. 

## Q : Unique elements in list of lists

```python
l = [[-1,-1,2],[-1,0,1],[-1,0,1]]
```

## A :

```python
[list(i) for i in set(tuple(i) for i in l)]
```

## Q : Diff between `range()` and `xrange()`

## A :

* `range()` – This returns a range object (a type of iterable). 
* `xrange()` – This function returns the generator object that can be used to display numbers only by looping. The only particular range is displayed on demand and hence called “lazy evaluation“.

## Q : How to find the longest list in a list?

## A : 
```python
max(values, key=len)
```

## Q : How to reverse a string?

## A :

```python
mystring[::-1]
```

## Q : What is throwaway variable ?

## A : 
```python
for _ in range(10):
    print("foo")
```

## Q : How to swap variables ?

## A : 

```python
a,b = 1,2
a,b = b,a
```

## Q : How to use Numeric laterals underscore ?

## A :

```python
billion = 1_000_000_000
```


