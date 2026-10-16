# String methods

Strings come with many built-in *methods*. You call a method with a dot after the
string: `text.upper()`. A string method never changes the original string. It
returns a **new** one, so you have to store the result:

    text = "Hello"
    shout = text.upper()
    print(shout)

This prints:

    HELLO

Below are the methods you will use most. Try each of them yourself in a Python file.

## Changing case

`lower()` and `upper()` convert all letters to lowercase or uppercase:

    title = "Hello, World!"
    small = title.lower()
    big = title.upper()
    print(small)
    print(big)

This prints:

    hello, world!
    HELLO, WORLD!

## Removing whitespace

`strip()` removes spaces, tabs and newlines from both ends of a string, but not from
the middle. The brackets in the output show where the string starts and ends:

    line = "   to be or not   \n"
    cleaned = line.strip()
    print(f"[{cleaned}]")

This prints:

    [to be or not]

`lstrip()` only removes them on the left, `rstrip()` only on the right:

    padded = "   to be   "
    left = padded.lstrip()
    right = padded.rstrip()
    print(f"[{left}]")
    print(f"[{right}]")

This prints:

    [to be   ]
    [   to be]

## Splitting and joining

`split(" ")` cuts a string at every space, and returns the parts as a list:

    sentence = "the cat sat"
    words = sentence.split(" ")
    print(words)

This prints:

    ['the', 'cat', 'sat']

You can split on any separator, for example a comma:

    measurements = "12,7,30"
    values = measurements.split(",")
    print(values)

This prints:

    ['12', '7', '30']

`join` does the opposite: it glues a list of strings together. You call it on the
string that should go *between* the parts:

    words = ["the", "cat", "sat"]
    sentence = " ".join(words)
    print(sentence)

    parts = ["2026", "10", "26"]
    date = "-".join(parts)
    print(date)

This prints:

    the cat sat
    2026-10-26

## Checking what is in a string

These methods answer a yes/no question about the whole string, and return `True` or
`False`:

    word = "banana"
    only_letters = word.isalpha()     # only letters?
    all_lower = word.islower()        # all letters lowercase?
    print(only_letters)
    print(all_lower)

    year = "2026"
    only_digits = year.isdigit()      # only digits?
    print(only_digits)

    agency = "NASA"
    all_upper = agency.isupper()      # all letters uppercase?
    print(all_upper)

This prints:

    True
    True
    True
    True

They work on single characters too, which is handy in a loop:

    char = "7"
    is_digit = char.isdigit()
    print(is_digit)

This prints:

    True
