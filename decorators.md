# Python Decorators

-   The point of decorators in python is to have the ability to change different functions in the same way without having to repeat yourself. Thus, stay DRY.
-   It is hard to give a concrete example or a reason for creating decorators.
-   An example of using decorators will be if you have a property that takes a long time to calculate, you might want to use a caching or memorization decorator to store the value of that property.
-   One of the big advantages of using decorators is that they are clean, small and easy to add or remove.
-   Yet, decorators are not the go to solution for a certain type of problems. it is kind of case by case basis.
-   Generally look for places where you repeat a lot of ancillary functionality. Places where you are bookkeeping are great places for decorators.
-   Decorators are functions that accept functions as arguments. And they have an inner function that performs some action before returning the accepted function, and, the outer function.

## Using Decorators For logging

-   What we are gonna do here in this exmaple does not have to be necessarly a decorator. We can write a function to call in every function to print the logging statement that we need to see.
-   But, the approach of writing a callable function in every function means we our functions will have this debugging and secretarial work inside of them.
-   it is easier to find an delete a bunch of lines that all start with the decorative symbol
-   Plus, using decorators will help in the separation of concerns leaving your function focus on one single thing instead of two (in this case logging and logic)

## Housekeeping

-   If you called one of the decorated functions attributes like `__name__` or `__doc__` what you will actually get is the attributes values for the function `__inner__` which is note quite right.
-   There are two ways to fix this:

**1- Change the decorating function:**
The hard way is by doing the following. Edit the decorating function itself to inheret the given function attributes.

      def close(func):
        number = 5
        def inner(*args, **kwargs):
            print(number)
            return func(*args, **kwagrs)
        inner.__name__ = func.__name__  # here we renamed the inner func
        inner.__doc__ = func.__doc__    # here we took the doc string if it exists
        return inner

**2- Using Python functools module**

-   The easier way is by using python functools module
-   The functools module includes a function called `wraps`.
-   `wraps` itself is a decorator, it handles the overriding of the decorating function attributes with the decorated function attributes for you.


        from functools import wraps

        def close(func):
          number = 5

          @wraps(func) # As simple as that!
          def inner(*args, **kwargs):
              print(number)
              return func(*args, **kwagrs)
          return inner

### Examples:

**No arguments function**

      def logme(func):
        import logging  # Make logging available only withing this scope and to avoid making others importing it to work
        logging.basicConfig(level=logging.DEBUG)

        def inner():
          logger.debug("Called {}".format(func.__name__))
          return func()

        return inner

**Functions with arguments**

      def logme(func):
        import logging  # Make logging available only withing this scope and to avoid making others importing it to work
        logging.basicConfig(level=logging.DEBUG)

        def inner(*args, **kwargs):
          logger.debug("Called {} with args {} and kwargs {}".format(
          func.__name__, args, kwargs))
          return func(*args, **kwargs)

        return inner

#### How to decorate a function:

_**Explicit Way**_: `print_2() = logme(print_2)`

_**Common convention**_:

        @logme
        def print_2():
            print(4)

## Addditional Notes:

-   Using `func.__name__` will print out the name of the called function.
-   Using `*args` and `**kwargs` withput the asterisk will give us the tuple itself. While keeping the astersiks will make be used as arguments
-   Decorators can take arguments like what we have seen in `@wraps(func)`. You can do that, decorators can take arguments that are then applied to the functions.
