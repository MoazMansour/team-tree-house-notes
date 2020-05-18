# Python Comprehensions
- Comprehensions are a convenient way to work with iterables in Python.
- Comprehensions let you skip the for loop and start creating lists, dicts, and sets straight from your iterables.
- Comprehensions also let you emulate functional programming aspects like map() and filter() in a more accessible way.
- You can add `ifs` into your Comprehensions which let us filter out things. Preferred not use any elses at the end.
- Keep your comprehension in one line to keep your code pythonistic.
- You can have comprehensions included in other type fo constructs. Like a Dict.

**Examples**

_Example#1_ list comprehension

        >>> [num * 2 for num in range(1, 6)]
        [2, 4, 6, 8, 10, 12]

_Example#2_ dict comprehension

        >>> {letter: num for letter, num in zip('abcdef', range(1, 7))}
        {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5, 'f': 6}

_Example#3_ set comprehension

        >>> {num * 2 for num in [5, 2, 18, 2, 42, 2, 2]}
        {84, 10, 4, 36}

_Example#4_ list with ifs

        >>> [num/2 for num in range(1,5) if num % 2 == 0]
        [1.0, 2.0]

_Example#5_ create a grid (without zip)

        >>> rows = range(4)
        >>> cols = range(10)
        >>> [(x, y) for y in rows for x in cols]
        [(0, 0), (1, 0), (2, 0), ...]

## Additional Notes

> What `zip` does is that it takes two or more iterables and gives you back one item form each iterable at the same index position.

> `set` is a datatype that is more like a list but doesn't have an order. And every item in this `set` is unique.

> `set` intersections: one of the set unique methods is that you can get the intersection between two different sets using `set_A.intersection(set_B)`
