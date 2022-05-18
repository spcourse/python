# Functions from Modules

In previous exercises you've already worked with several built-in Python commands (or, *functions*): `input` and `print` are two examples. The Python interpreter has several functions built into it that are always available. There are many more functions which are not available by default.

To calculate the sine of a number, the function `sin` is available. But if you try to calculate this in Python with `sin(1.0)`, an error will appear:

    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'sin' is not defined

Note the final line of this error message. This is what it says formulated in understandable English: Python does not know the name `sin` and therefore cannot execute the function!

To be able to use the `sin`-functionality you have to make sure the `math`-library and all the functions within this library are available in your program:

    import math         # import the math library

    x = 0.5
    print(math.sin(x))

If you want to use the `sin()` function you should indicate in which library Python can find this function. There could also be other libraries that contain a `sin` function. We should thus explicitly choose for the `math` library.

## Documentation

- The functions that are available within the math library can be found in the documentation:

  <https://docs.python.org/3/library/math.html>

- And there are many more libraries available for standard-Python:

  <https://docs.python.org/3/library/>

- For many areas of expertise and applications, libraries can be found. If you work on larger programs in the future, it might even be handy to write and store your own standard code in a library. This benefits the readability and structure of your code and it is then easy to share your code with others.
