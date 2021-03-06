# programmedpatterns

Practice exercises in pattern recognition, ideal for beginner and intermediate programmers.

This uses the patterns at [https://www.visualpatterns.org/](https://www.visualpatterns.org/) by Fawn Nguyen. The site and this module are licensed under a Creative Commons Attribution license.

The patterns are *not* in order of difficulty. Many are simple, some are incredibly hard.

THIS MODULE IS CURRENTLY UNDER CONSTRUCTION AND NOT WORKING YET.

Installation
------------

To install with pip, from the Command Prompt/terminal run:

    python -m pip install programmedpatterns


Contribute
----------

Currently a lot of basic programming work is needed (in Python and other languages) to make Programmed Patterns work.

First, we need the solutions for all 468 patterns. Each solution is comprised of a `visX(n)` function that returns a multiline string for pattern *X* at iteration *n*, and a `numX(n)` function that returns a numeric count of the number of shapes in pattern *X* at iteration *n*.

For example, here's pattern #5 which has a medium level of difficulty:

     OO    OOO     OOOO
    O O     OO      OOO
    OOO  O  OO      OOO
         OOOO   O   OOO
         OOO    OOOOO
                OOOO
                OOOO
    Number of Os:
    7    15     27

The `vis5()` function you write should take an integer `n` and return a multiline string for the pattern at iteraton *n*:

    def vis5(n):
        result = ''
        result += (' ' * n) + ('O' * (n + 1)) + '\n'
        for i in range(n - 1):
            result += (' ' * (n + 1)) + ('O' * n) + '\n'
        result += 'O' + (' ' * n) + ('O' * n) + '\n'
        result += 'O' * (n + 2) + '\n'
        for i in range(n - 1):
            result += 'O' * (n + 1) + '\n'
        return result

The `num5()` function you write should take an integer `n` and return the number of `'O'` characters in the pattern at iteration *n*:

    def num5(n):
        return 3 + (2 * ((n + 1) * n))

These functions will be used to check student solutions. Each pattern puzzle has a visual string-manipulation component and a mathematical algebra component. This provides a lot of practice for intermediate-level programmers who have learned language syntax but need to become more skillful at writing code.

Where you can help is by writing the solution functions for the unsolved patterns. Check out https://visualpatterns.org and find a pattern to write function solutions for. To avoid working on patterns that other people may be working on, pick patterns to solve randomly by running `random.randint(1, 468)` in Python (or some other random selection method) and then check the GitHub repo to make sure it hasn't already been solved.

The source code file has boilerplate `visX()` and `numX()` functions that you can fill in with your solution. You can then run `getPatternMultilineString(X, 1, 10)` (where `X` is the pattern number) to verify that the solution looks correct for iterations 1 through 10.

While the strings returned by the `visX()` functions have multiple lines (that is, they contain \n newline charactrs) each line should remove all trailing whitespace for their canonical answer. For example, this pattern:

    O
    OO
    OOO

....should be represented as `'O\nOO\nOOO'` and not `'O  \nOO \nOOO\n'`.

You should also draw each pattern as far up and to the left as possible. For example, pattern #22's 2nd iteration should be `'O\nOO'` and not `'\n\nO\nOO'`.

Special Case Patterns
-------------

Most of the patterns involve a progressive growth of generic shapes which are represented by `'O'` strings. For example:

Pattern #9:

    O    OO    OOO    OOOO    OOOOO
    OO   OOO   OOOO   OOOOO   OOOOOO
    OOO  OOOO  OOOOO  OOOOOO  OOOOOOO
    Number of Os:
    6    9     12     15      18

Pattern #11:

    O   O    O     O      O
    OO  O    O     O      O
        OOO  O     O      O
             OOOO  O      O
                   OOOOO  O
                          OOOOOO
    Number of Os:
    3   5    7     9      11

Pattern #14:

    O       O       O       O       O
    OOOOOO  OOOOOO  OOOOOO  OOOOOO  OOOOOO
            OOOOOO  OOOOOO  OOOOOO  OOOOOO
                    OOOOOO  OOOOOO  OOOOOO
                            OOOOOO  OOOOOO
                                    OOOOOO
    Number of Os:
    7       13      19      25      31

But some patterns have multiple kinds of shapes. For example, pattern #15:

     O    O O    O O O    O O O O    O O O O O
    OXO  OXOXO  OXOXOXO  OXOXOXOXO  OXOXOXOXOXO
     O    O O    O O O    O O O O    O O O O O
    Number of Os, Xs:
    (4, 1)(7, 2) (10, 3)  (13, 4)    (16, 5)

In these cases, other letters such as `'X'` are used in addition to `'O'` for the visual component. For the numerical component, the `numX()` function doesn't return a simple integer but a tuple of integers. For pattern #15, the tuple returned is in the format `(number of Os, number of Xs)`.

Other patterns have line drawings rather than discreet shapes. For example, pattern #44 looks like this:

        __          __    __          __    __    __
     __/##\__    __/##\__/##\__    __/##\__/##\__/##\__
    /##\##/##\  /##\##/##\##/##\  /##\##/##\##/##\##/##\
    \##/  \##/  \##/  \##/  \##/  \##/  \##/  \##/  \##/
    /##\__/##\  /##\__/##\__/##\  /##\__/##\__/##\__/##\
    \##/##\##/  \##/##\##/##\##/  \##/##\##/##\##/##\##/
       \##/        \##/  \##/        \##/  \##/  \##/
    Number of filled hexagons:
    6           10                14

These patterns often use `/`, `\`, `_`, and `|` for line-drawing characters. In many programming languages, the `\` forward slash must be escaped as `\\` when written in string literals in your code. In Python, raw strings are a helpful shortcut that allows you to write forward slashes without escaping them: `print(r'Hello\\world')` will print `Hello\\world` and not `Hello\world`.

However, Python has a slight bug in its language design where \ slashes cannot be the last character in a raw string. The code `print(r'\Hello\')` produces a syntax error instead of displaying `\Hello\`. You cannot use raw strings in these cases and instead must use normal strings with escape characters: `print('\\Hello\\')`

Please contact me at al@inventwithpython.com or on Twitter @AlSweigart if you'd like to contribute to this git repo.

Support
-------

If you find this project helpful and would like to support its development, [consider donating to its creator on Patreon](https://www.patreon.com/AlSweigart).
