
## Conditional Expressions
```Python
## Shortcut conditional expression

'true' if True else 'false'

# The syntax will be
A if C else B
# This first evaluates C; if it is true, A is evaluated to give the result, 
# otherwise, B is evaluated to give the result.

# The priorities will be such that you can write
x = A if C else B
x = lambda: A if C else B
x = A if C else B if D else E


## More examples:
a = 1
b = 2

1 if a > b else -1  # Output is -1

# Equivalent:
if a > b:
 1
else:
 -1

1 if a > b else -1 if a < b else 0 # Output is -1
# Equivalent:
if a > b:
 1
else:
 if a < b:
  -1 
 else:
  0

```
- https://mail.python.org/pipermail/python-dev/2005-September/056846.html


## List

#### Slicing
```Python
a[start:stop]  # items start through stop-1
a[start:]      # items start through the rest of the array
a[:stop]       # items from the beginning through stop-1
a[:]           # a copy of the whole array
a[start:stop:step] # start through not past stop, by step

a[-1]    # last item in the array
a[-2:]   # last two items in the array
a[:-2]   # everything except the last two items

a[::-1]    # all items in the array, reversed
a[1::-1]   # the first two items, reversed
a[:-3:-1]  # the last two items, reversed
a[-3::-1]  # everything except the last two items, reversed

L[x::y]    # means a slice of L where the x is the index to start from and y is the step size
L[::3]     # If you want every 3rd element
L[1::3]    # Now every third element starting from L[1]


```

###### References:
- [SO - understanding-slice-notation](https://stackoverflow.com/questions/509211/understanding-slice-notation/509295#509295)
- https://stackoverflow.com/questions/9027862/what-does-listxy-do?noredirect=1&lq=1
