# Python Type Hinting

Pythonistas have always relied on duck typing to handle different values in variables. Starting with Python 3.0, continuing in 3.5, and wrapping up in 3.6, type hints have been added to Python. What are these strange constructs and what have they done with all the ducks?

-   Python is dynamically typed. This means that a variable like `name` could change from an int to a string to a list.
-   Python now has an official way of doing type hinting.
-   This started a few years ago with the launch of Python 3.0. This PEP allowed for functions annotations.
-   Using function annotations you could provide information about the paramaters that a function took and its return value and this will show up in`__annotations__` attribute of the function.
-   Then came MyPy: A static type checker for Python. It will look for special formatting in your python code when you declare what a certain variable should be and it will tell you if you ever gave it something else.
-   These tools didn't and won't make Python staticly typed. The didn't and don't enforce anything at runtime. Instead they are being used in code reviews to make sure that the code meets the standards.
-   Like testing, and naming conventions Python Type Hinting is a tool that make your work easier. But, it is an opt in basis kinda tool.

## Anotating

-   To anotate a function you don't neeed to import anything.
-   Just declare the variable type in the function definition as follows:

        def add(num1: int, num2: int) -> int: # using the arrow then type annotates the return value type.
            return num1 + num2

## The Typing Module

-   In Python 3.5 the module typing was introduced defining a bunch of types that we can use when creating hints in our code

**_List Type_**

-   The List type let you say that you want a list of items of a particular type.
-   Just like when we hint function parameters, we use a colon and then the type we are hinting.
-   If you don't wanna set a default value for the paramter as I am declaring it. You can just name it and hint it


        from types import List
        things: List[Object] = []

**_Union Type_**

-   Union let you specify two or more valid types.

        from types import Union
        def func(para: Union[Object, str]):
            do something

**_Optional Type_**

-   It specifies that a type is Optional.
-   This means the value can be one of the types that are specified or `None`


        from types import Optional
        def func(para: Optional[str]):
            do something

## Older Python Versions

**_Stub Files_**

-   Stub files in Python always have a `.pyi` extension.
-   They have share the same module name with the module they define types for.
-   In the `.pyi` file you are just redefining your functions and types.
-   It doesn't have to include any logic in it. Which means you can remove the body of the functions and colons

## Additional Notes

-   Specific to the above exmaple tho, what if I wanna add an int and a float.
-   An easy way to do so is by using the Python built-in type: `complex` that encompass both integers and floats.
-   If I wanna use real numbers instead I should import the `Real` type from the `numbers` module.
-   The `Real` type encompasses integers and floats
-   Much like the actual list type you don't want to use List annotation when declaring types for parameters in a function or a method
-   You can use the `Mypy` package to check your code types.
