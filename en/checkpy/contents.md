# Using checkpy

Once you feel you're done with the assignment, it's time run it through `checkpy`. Of course, you get frowny faces indicating there is something wrong. But what?!?

The output you get from `checkpy` can sometimes be a bit overwhelming. So it might be hard to figure out what is wrong. Below we will discuss some common issues.

### All ok

Ideally all went well and you get only smiley faces. Hello.py was supposed to print the text "Hello, world!" and it did so correctly:

  	$ checkpy hello
    Testing: hello.py
    :) prints "Hello, world!"

So the description of the test is `prints "Hello, world!"` and `:)` shows that all was good.

### Small mistakes in the output:

But when your output doesn't match **exactly** what `checkpy` expects, you will get a frowny face. This can be frustrating but `checkpy` often give you very specific feedback about what went wrong. And once you understand how to interpret the test output, these mistakes are often easy to fix.

    $ checkpy hello
    :( prints "Hello, world!"
       assert 'Hello, world!\n' == 'Hello, zorld!!!\n'
         - Hello, world!
         ?        ^
         + Hello, zorld!!!
         ?        ^     ++

So the description of the test is still `prints "Hello, world!"`, but now the `:(` shows that something went wrong.

In the above case your program didn't print "Hello, world!", "Hello, zorld!!!" (so with a `z` instead of `w` and with three exclamation marks).

The first line shows the actual test that was run: `assert 'Hello, world!\n' == 'Hello, zorld!!!\n'`. This essentially asserts that `checkpy` expects to see `Hello, world!`, but instead it gets `'Hello, zorld!!!\n'`. When you run checkpy and something went wrong you often see this type of `assert` error. They almost always have the form:

    assert expected_value == actual_value

On the lines below you see that `checkpy` gives more detail about the `assert` error.

    - Hello, world!             <---- expected output
    ?        ^                  <---- the ^ symbol shows where the expected output differs from your output
    + Hello, zorld!!!           <---- actual/your output
    ?        ^     ++           <---- the + symbol shows where you added more text than expected


### Paused output

Running checkpy for `pyramid` as shown below exposes some error with the output.

    $ checkpy pyramid
    :) the program does not use break or import statements
    :) the program does not use string multiplication
    :) rejects heights of -100 and 24, then accepts a height of 3
    :( prints a well-formed pyramid of height 1
       assert '# #\n' == '* *\n'
         - # #
         + * *
    :| prints a well-formed pyramid of height 3
       can't check until another check passes
    :| prints a well-formed pyramid of height 23
       can't check until another check passes

Here we see that your code passed the first three tests. But the test with description `prints a well-formed pyramid of height 1` failed. Can you guess what went wrong?

The output of the test is:

    assert '# #\n' == '* *\n'
      - # #
      + * *

So the `assert` expected `# #\n` but instead your code produced `* *\n`. on the lines below you see more detailed feedback, although in this case that doesn't provide much more info. (Note that the `\n` means a new line.)

The last two tests are not run at all. The `:|` indicates that a test cannot be run. In this case that is because these last two test will only run if the tests before it succeeded.

### Multi line output

When your code is supposed to produce multiple lines of output the output of `checkpy` can get more confusing. For example:

    :( prints a well-formed pyramid of height 3
       assert '    # #\n  # # #\n# # # #' == '     # #\n  ...#\n # # # #\n'
         -     # #
         +      # #
         ? +
         -   # # #
         +    # # #
         ? +
         - # # # #
         +  # # # #
         ? +       +


Here the expected output was `'    # #\n  # # #\n# # # #'` but the actual value was `'     # #\n  ...#\n # # # #\n'`. The `\n` means that everything following it should be on a new line. So the expected output was:

        # #
      # # #
    # # # #

But the actual output:

         # #
       # # #
     # # # #

It's a subtle difference, but the detailed information below actually gives us all the info we need:


    -     # #              <---- expected first line
    +      # #             <---- actual first line
    ? +                    <---- the actual first line has an additional character (a space)
    -   # # #              <---- expected second line
    +    # # #             <---- actual second line
    ? +                    <---- the actual second line has an additional character (a space)
    - # # # #              <---- expected third line
    +  # # # #             <---- actual third line
    ? +       +            <---- the actual third line has an additional character (a space)

So all lines of the output of your code have an additional leading space.

### An actual Python error

Sometimes you get something like this:

    $ checkpy greedy
    Testing: greedy.py
    :) the program does not use break or import statements
    :( rejects negative input, then accepts an input of 0.41
       "ZeroDivisionError('division by zero')" occured while trying to import the code

Anytime you get something of the form "[Some error] occured while trying to import the code", that checkpy got an error while importing your code. So this has nothing to do with the test `rejects negative input, then accepts an input of 0.41`, but if we would run your code normally using `python greedy.py` we would also get an error:

    $ python greedy.py
    How much change is owed? 0.41
    Traceback (most recent call last):
    File "greedy.py", line 23, in <module>
    1/0
    ZeroDivisionError: division by zero        <---- this is the error that tripped up checkpy


### Function arguments

When you use functions `checkpy` also often checks if you defined the function exactly according to specification. For example for `list_words.py` you're supposed to define a function `text_to_unique_words(text)`. If instead of the argument `text` you name the argument of the function `tekst`, you get this error:

    $ checkpy list_words
    Testing: list_words.py
    :) the program does not use break or import statements
    :) correctly defines the cleanup() function
    :( testing text_to_unique_words() >> defines the function as text_to_unique_words(text)
       parameters should exactly match the requested function definition
       assert ['text'] == ['tekst']
         At index 0 diff: 'text' != 'tekst'

Also the order of arguments should meet the spec. For example, in `reformatting` you should define `text_to_lines(text, max_length)`, but if you switch around the arguments (`text_to_lines(max_length, text)`), you get this error:

    $ checkpy reformatting
    Testing: reformatting.py
    :) the program does not use break or import statements
    :( testing text_to_lines() >> defines the function as text_to_lines(text, max_length)
       parameters should exactly match the requested function definition
       assert ['text', 'max_length'] == ['max_length', 'text']
         At index 0 diff: 'text' != 'max_length'


### Return None

A common mistake is to forget to put a `return` statement at the end of the function or to put a `print` statement in a return `return print(something)`. In both cases the function will return the value `None`. This is often gives an assert error in the form of `assert None is of type ...`, like so:

    Testing: list_words.py
    :) the program does not use break or import statements
    :) correctly defines the cleanup() function
    :( testing text_to_unique_words() >> text_to_unique_words("Test sentence") returns a value of type List[str]
       text_to_unique_words("Test sentence") returned: None
       assert None is of type List[str]
