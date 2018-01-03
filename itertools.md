# Itertools (Notes and Exploration)

A non-comprehensive set of Itertools examples.
Itertools is cool! It makes code easier to reason with (once you learn them). 

## Groupby
- Groups an iterable based on a keyfunc
- Sort first, or you'll get duplicate groups
- The groups share an iterable with the groupby(), so make sure to iterate in order. Calling list() on the groupby() result will break things.

```
>>> data = [1,2,3,4]
>>> itertools.groupby(data, lambda n:n%2)
<itertools.groupby object at 0x10db46188>
    [(1, <itertools._grouper object at 0x10db405f8>), 
     (0, <itertools._grouper object at 0x10db40630>), 
     (1, <itertools._grouper object at 0x10db40668>), 
     (0, <itertools._grouper object at 0x10db406a0>)]
```
Each of the sub-iterators contain the actual elements that fulfill the grouping.

The quirk you may have noticed: Groupby iterates the list and creates a new group *every time* the keyfunc changes. This is documented.

If you don't want this, make sure to sort the list first!
```
>>> data = sorted(data, key=lambda n:n%2)
>>> data
[2, 4, 1, 3]
>>> itertools.groupby(data, lambda n:n%2)
<itertools.groupby object at 0x10d95ab88>
    [(0, <itertools._grouper object at 0x10db40668>), 
     (1, <itertools._grouper object at 0x10db406a0>)]
```
A scarier quirk is that calling list() on the groupby object causes bad things to happen:
> The returned group is itself an iterator that shares the underlying iterable with groupby(). Because the source is shared, when the groupby() object is advanced, the previous group is no longer visible.
list() implicitly advances the groupby()
```
>>> z = itertools.groupby(data, lambda n:n%2)
>>> z
<itertools.groupby object at 0x10d95ab88>
>>> for i in z:
...   for elem in i[1]:
...     print(elem, end=' ')
2 4 1 3
```
*BUT:*
```
>>> z = list(itertools.groupby(data, lambda n:n%2))
>>> z
[(0, <itertools._grouper object at 0x10db405f8>), (1, <itertools._grouper object at 0x10db40668>)]
>>> for i in z:
...   for elem in i[1]:
...     print(elem, end=' ')
3
```
