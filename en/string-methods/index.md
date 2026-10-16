# String methods

Strings come with many built-in *methods*. You call a method with a dot after the
string: `text.upper()`. A string method never changes the original string. It
returns a **new** one, so you have to store the result:

    >>> text = "Hello"
    >>> shout = text.upper()
    >>> print(text, shout)
    Hello HELLO

Below are the methods you will use most. Try each of them yourself at the Python
prompt.

## Changing case

`lower()` and `upper()` convert all letters to lowercase or uppercase:

    >>> "Hello, World!".lower()
    'hello, world!'
    >>> "Hello, World!".upper()
    'HELLO, WORLD!'

## Removing whitespace

`strip()` removes spaces, tabs and newlines from both ends of a string, but not from
the middle:

    >>> "   to be or not   \n".strip()
    'to be or not'

`lstrip()` only removes them on the left, `rstrip()` only on the right:

    >>> "   to be   ".lstrip()
    'to be   '
    >>> "   to be   ".rstrip()
    '   to be'

## Splitting and joining

`split(" ")` cuts a string at every space, and returns the parts as a list:

    >>> "the cat sat".split(" ")
    ['the', 'cat', 'sat']

You can split on any separator, for example a comma:

    >>> "12,7,30".split(",")
    ['12', '7', '30']

`join` does the opposite: it glues a list of strings together. You call it on the
string that should go *between* the parts:

    >>> " ".join(["the", "cat", "sat"])
    'the cat sat'
    >>> "-".join(["2026", "10", "26"])
    '2026-10-26'

## Checking what is in a string

These methods answer a yes/no question about the whole string, and return `True` or
`False`:

    >>> "banana".isalpha()     # only letters?
    True
    >>> "2026".isdigit()       # only digits?
    True
    >>> "banana".islower()     # all letters lowercase?
    True
    >>> "NASA".isupper()       # all letters uppercase?
    True

They work on single characters too, which is handy in a loop:

    >>> "7".isdigit()
    True
