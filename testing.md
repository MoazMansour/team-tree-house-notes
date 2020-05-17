# Python testing
- **TDD**: Test Driven Development
  - In TDD you write the test framework before you write the code!
- Tests are unit test

### Unit Test:
 - a unit is a single feature or aspect of your code.
 - Think about a class object. Each attribute and each method is considered a unit. And each will need a test for it.

### Regression Test:
- Make sure that previous mistakes do not happen again

### Integration Test:
- run your code through a battery of uses to make sure that a certain process, one that uses multiple units, works from beginning to end.
> _Example:_ If you wanted to test the registration flow of a Flask App, you'd have a test that loads the account creation page, fills out and submits the form follows the redirect. Checks that the user model was created, and that you ended up on teh sign in page

## Doctests:
- Inside the doc string of a function. you can alos write a test! #impressive
- inside the docstring:
  - Leave white space to help python find the doctest
  - Write three chevrons `>>>` that looks like the python shell. This is how you tell python to run the code inside the docstring
  - you can use other functions that are in the file in your doctest
  - Add as much testcases as you would like.
- Use `import doctest doctest.testmod()` in your script to run them everytime you run the scritp. Yet, you usually don't want docttest to run.
- Intead run `python -m doctest your_script.py`. This will run all the doctests you have in your scripts just for this time. When nothing comes back this means your script passed the test.

**Examples**

_Example#1_

      def build_cells(width, height):
        '''
          Create and return a 'width' x 'height' grid of two-tuples

          >>> cells = build_cells(2, 2) # this is what you want to happen
          >>> len(cells)
          4  # This is what you are expecting back from your code
        '''

_Example#2_        

        def get_locations(cell):
        '''Randomly pick a starting locations for the monster, the door, and the player

        >>> cells = build_cells(2, 2) # another function in the file
        >>> m, d, p = get_locations(cells) # what you want to test
        >>> m != d and d != p # what are you expecting out of the function
        True  # expected result
        >>> d in cells
        True
        '''

## Unit Test Module
- Everything is included in the module `unittest`
- The main way to approach this is by building what is known as a "test case".
- a test case is a class that contains multiple methods, some of which are test, another are just methods that you need
- There are two special methods, Set Up and Tear Down, that are run before and after each test.
- Unlike doctest we are gonna write our unit test code in a separate file more like how CSS work with HTML.
- Test class definition: `class MoveTests(unittest.TestCase)`
- Naming convention: all test methods should start by the word test_ so `def test_five_plus_five(self)`
- `assert` key word: makes sure whatever comes after it is true
- to run your test script in test mode. Run `python3 -m unittest tests.py` in the shell
- unlike doctest which is included in the original script we want to run the tests everytime we run the unit test script. To do so we are gonna add the following line to the script to run the test natively
      if __name__ == "__main__":
        unittest.main()
