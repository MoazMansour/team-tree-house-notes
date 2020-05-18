# Python testing
- **TDD**: Test Driven Development
  - In TDD you write the test framework before you write the code!
- Tests are unit test

### Unit Test:
 - A unit is a single feature or aspect of your code.
 - Think about a class object.
 - Each attribute and each method is considered a unit.
 - And each will need a test for it.

### Regression Test:
- Make sure that previous mistakes do not happen again.

### Integration Test:
- run your code through a battery of uses to make sure that a certain process, one that uses multiple units, works from beginning to end.
> _Example:_ If you wanted to test the registration flow of a Flask App, you'd have a test that loads the account creation page, fills out and submits the form follows the redirect. Checks that the user model was created, and that you ended up on the sign in page.

## Doctests:
- Inside the doc string of a function. you can also write a test! #impressive
- inside the docstring:
  - Leave white space to help python find the doctest.
  - Write three chevrons `>>>` that looks like the python shell. This is how you tell python to run the code inside the docstring.
  - you can use other functions that are in the file in your doctest.
  - Add as much testcases as you would like.
- Use `import doctest` and `doctest.testmod()` in two separate lines in your script to run the tests everytime you run the script. Yet, you usually don't want docttest to run everytime you are running the scripts.
- Instead run `python -m doctest your_script.py`. This will run all the doctests you have in your scripts just for this time. When nothing comes back this means your script passed the test.

**Examples**

_Example#1_

      def build_cells(width, height):
        '''
          Create and return a 'width' x 'height' grid of two-tuples

          >>> cells = build_cells(2, 2) # This is what you want to test
          >>> len(cells) # An expected condition
          4  # This is what you are expecting back from your code

        '''

_Example#2_        

        def get_locations(cell):
          '''
            Randomly pick a starting locations for the monster, the door, and the player

            >>> cells = build_cells(2, 2) # another function in the file
            >>> m, d, p = get_locations(cells) # what you want to test
            >>> m != d and d != p # what are you expecting out of the function
            True  # expected result
            >>> d in cells
            True

          '''

## Unit Test Module
- Everything is included in the module `unittest`.
- The main way to approach this is by building what is known as a "test case".
- A test case is a class that contains multiple methods, some of which are test, another are just methods that you need.
- There are two special methods, Set Up and Tear Down, that are run before and after each test.
- Unlike doctest we are gonna write our unit test code in a separate file more like how CSS work with HTML.
- Test class definition: `class MoveTests(unittest.TestCase)`
- _Naming convention:_ all test methods should start by the word `test_` so `def test_five_plus_five(self)`.
- `assert` key word: makes sure whatever comes after it is true.
- To run your test script in test mode. Run `python3 -m unittest tests.py` in the shell.
- Unlike doctest which is included in the original script we want to run the tests everytime we run the unit test script. To do so we are gonna add the following block to the script to run the test natively.
      if __name__ == "__main__":
          unittest.main()
- All testing libraries work on the idea of assertions.
- An assertion test a condition in your code that must be met.

### Main methods
- `setUp()`: Method that is run before each test. Use this to set up state for the tests.
- `assertEqual(x, y)`: Make sure x and y are equal.
- `assertNotEqual(x, y)`: Make sure x and y are not equal.
- `assertGreater(x, y)`: Make sure x is greated than y.
- `assertLess(x, y)`: Make sure x is less than y.
- `assertIn(x, y)`: Make sure x is a member of y.
- `assertNotIn(x, y)`: Make sure x is not a member of y.
- `assertIsInstance(x, y)`: Make sure x is an instance of the y class.
- `assertGreaterEqual(x, y)`: Make sure x is greater than or equal to y.
- `assertLessEqual(x, y)`: Make sure x is less than or equal to y.
- `assertRaises(x)`: Make sure the following code raises the x exception.
- `assertWarns(SomeWarning)`: Test that a warning is triggered when callable is called.
- `assertLogs(x, level='INFO')`: Make sure that at least one message is emitted inside the `with` block matches the logger level and conditions.

> 'setUp()' is basically the the `__init__()` function of the test case class

> you can use `@unittest.expectedFailure` on a test that you know will fail. But not a good practice. There is no point of having a test that you know will fail. Just ignore it.

**Examples**

_Example#1_

        with self.assertRaises(ValueError):
          dice.Roll('2b6') # we are expecting input format to be '2d6'
_Example#2_

        self.assertIn(test_die, self.hand1.results)
_Example#3_

        self.assertLessEqual(self.hand3, 18)
_Example#4_

        self.assertGreaterEqual(self.hand3, 3)
_Example#5_

        with self.assertLogs('foo', level='INFO') as cm:
          logging.getLogger('foo').info('first message')
          logging.getLogger('foo.bar').error('second message')
_Example#6_

        with self.assertWarns(SomeWarning):
          do_something()

## Using Coverage
- How to make sure your test case has covered all lines in your code.
- Don't worry there is a tool for that.
- `pip3 install coverage` to install the library.
- Before using coverage you have to make sure your test script can be run without the `python -m` line in the shell.
- You can do that by adding the `if __name__` block to your code like this:
        if __name__ == '__main__':
            unittest.main()
- Once you have this in place you run coverage from the shell using `coverage run tests.py`.
- You will get the same results as running the tests.py normally in your shell.
- The magic happens under the hood. And to reveal it you should run `coverage report` afterwards.
- The report will contain two or more rows.
  - Ignore the `tests` row. it should be always set at `100%` as it shows our tests
  - The juicy rows are the others pointing at the class you are testing.
  - The stats `Miss` and `Cover` show how many statements did you miss for testing and the percentile of covered statements in your tests on the subject class.
- Now that you know you are missing some statements you need to know which statements these are.
  - To do so run `coverage report -m` the `-m` flag stands for missing.
  - You will get a familiar report but this time with a `Missing` column indicating which lines are missing from your tests.
  - Generally you want to aim at `90%` or better.
- One other mind blowing trick is to have a visual report of what you have covered.
  - instead of generating reporting in the terminal. Do `coverage html` which will generate a `htmlcov` folder.
  - You will get a very nice html viewable in your browser for the error report.
  - Clicking on the class name that is being tested in this html page will display your script file in the browser in a decent github code like format where you can actually see which lines are not covered red and highlighted. Isn't this awesome!!
- You can skip lines in your script from getting covered. They will appear highlighted in yellow in your nice html view.

## Additional Notes
> use `python -m http.server` in the shell to serve up a very basic HTTP server
