# Functional Programming in Python

Functional programming is a great addition to any programmer's toolset. FP allows you to quickly filter lists, modify values, find answers, and other repetitious tasks with less code than other approaches.

## Core Theories

**Computation is the evaluation of functions:**
We do our work, copmuting values and outcomes, all in functions. We'll try to keep as much of our work inside discrete functions as possible.

**Programming is done with experssions:**
We do our work by using experssions, passing the output of one function into another, either through chaining or by assigning the output to a variable and then using that variable

**No side-effects from computation:**
We don't want to change values outside of our function's scope. We have to be careful with this when we are using mutable types such as lists and dictionaries.

**Functions are first class citizens:**
In Python, functions can be provided as an argument to a function callor returned from a function. Since functions are useable as values just like variables are, they are considered to be "First Class".

**Functions should be limited in Scope and functionality:**
We want to make sure that our functions have a well-defined purpose. We want them to achieve a single task and then give us the answer from that task

## Bad Examples

What we should be avoiding in functional programming

-   Don't call methods on mutable objects unless you know exactly what you are doing and why.
-   Avoid overriding global variables in function scopes.
-   Avoid functions that are too long
-   Avoid giving too many inputs to one function

## Sorting

If we wanna avoid side-effects, hence avoid changing mutable variables inside functions. Then, how can we run specific small tasks on mutable objects without affecting them if needed?

**Return Copies**

-   To achieve changing mutable objects without actually changing them we can return copies of that object instead.
-   One example of that is using `sorted()` function with a list instead of using the list mehtod `list.sort()`. The `sorted()` functions creates a copy of the list, get it sorted, send back the sorted copy instead of sorting the original list in place.

    > What if we wanna achieve the same functionality of the `sorted()` function but not on default straightforward types like strings and numbers?

-   To get the same functionality we are gonna use `attrgetter` and `itemgetter` from the `operator` python module.

        from operator import attrgetter, itemgetter
        sorted(raw_data, key=itemgetter('publish_date')) # raw data here is a list of dictionaries in this example
        sorted(BOOKS, key=attrgetter('number_of_pages'))

## Map()

-   `map()` lets us apply transformations to each item in an iterable.
-   What `map()` does is effectively a list comprehension.
-   Why would you use `map()` over a list comprehension if they are both effectivly the same. The only difference is that `map()` is easily nestable while it is not easy to acheive the same complications with other functionalities when using list comprehensions
-   Functions used with `map()` usually should start with an affirmative verb. Just a naming convention to give you a sense of what's going on inside the `map()`

**Example**

        a = [1, 2, 3]
        def apply_double(n):
            return n * 2
        list(map(apply_double, a)) # the double function will be applied to all items in list a

## Filter

-   `filter()` like a `map()` takes a function and an iterable and run this function against each item in the iterable.
-   If the function returned a truthy item, then this item gets added to the iterable that filter returns.
-   Functions used with `filter()` usually should be in the form of a question which is what you are asserting against. A naming convention that give a sense what you are usinmg the filter for

**Example**

        a = [a for a in range(15)]
        def is_divisable_by_two(num):
            if num % 2:
                return None
            return num
        list(filter(is_divisable_by_two, a)) # is_divisable_by_two will be applied on all items in list and the returning list will be limited to the only the numbers divisible by 2

## Combinations

-   As long as your function (map, filter, sorted, reversed, etc.) returns a list they can be chained together because they all work together.

**Example**

        e = [a for a in range(15)]
        def double(num):
            return num * 2

        def check(num):
            return bool(num > 20)

        list(filter(check, map(double, e)))

## Additional Notes

-   You can set `reversed` attribute as True when calling `sorted(reversed=True)` to have the sort happen in a reverse order.
-   Another useful modules in Python is `copy`. `copy` makes us make copies of something. Usually used with mutual objects when operating on them in a function just to be safe by avoiding modifying the original object.
-   In the `itertools` module there is a function called `filterfalse` that works just like filter but only caputres the items that return false.
-   You can wrap a list comprehension in a function called `any()`. `any()` returns `True` or `False` if any of the things in the iterable that its passed are `True`.
