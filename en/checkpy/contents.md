# Using checkpy

Once you believe you've completed an assignment, it's time to test it through `checkpy`. Unfortunately, you might encounter unhappy faces indicating something is amiss. But what exactly is the problem? The feedback from `checkpy` can be a bit overwhelming at times, making it challenging to pinpoint the issue. Below, we'll discuss some common problems and how to interpret them.

Reading this document might help in understanding why `checkpy` doesn't accept your code. However, please note that there are many issues that we do not address here. Even when you identify what's wrong, the solution might still not be immediately apparent. If you have questions after reading this document, feel free to ask questions to seek further assistance during the tutorials!

### Everything is fine

Ideally, if everything went well, you'll only see smiling faces. For instance, in the case of `hello.py`, where the expected output is "Hello, world!" and it's correct:

  	$ checkpy hello
    Testing: hello.py
    :) prints "Hello, world!"

So, the test description is "prints 'Hello, world!'" and `:)` indicates that everything is good.

### Minor discrepancies in the output:

However, if your output doesn't exactly match what `checkpy` expects, you'll see a frowning face. This can be frustrating, but `checkpy` often provides specific feedback on what went wrong. Once you understand how to interpret the test output, these issues are usually easy to resolve.

    $ checkpy hello
    :( prints "Hello, world!"
       assert 'Hello, world!\n' == 'Hello, zorld!!!\n'
         - Hello, world!
         ?        ^
         + Hello, zorld!!!
         ?        ^     ++

Here, the test description is still "prints 'Hello, world!'," but now `:(` indicates that something went wrong.

In this case, your program didn't print "Hello, world!" but instead printed "Hello, zorld!!!" (with a 'z' instead of 'w' and three exclamation marks).

The first line shows the actual test that was run: `assert 'Hello, world!\n' == 'Hello, zorld!!!\n'`. This means `checkpy` expected to see 'Hello, world!', but it got 'Hello, zorld!!!'. When something goes wrong, you often see this type of `assert` error, which typically follows the format:

    assert expected_value == actual_value

Below that, `checkpy` provides more details about the `assert` error.

    - Hello, world!             <---- expected output
    ?        ^                  <---- the ^ symbol shows where the expected output differs from your output
    + Hello, zorld!!!           <---- actual/your output
    ?        ^     ++           <---- the + symbol shows where you added more text than expected


### Interrupted output

Running `checkpy` for `pyramid` as shown below reveals an error in the output.

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

 Here, your code passed the first three tests, but the test with the description "prints a well-formed pyramid of height 1" failed. Can you guess what went wrong?

 The test's output is:

    assert '# #\n' == '* *\n'
      - # #
      + * *

So, the `assert` expected `'# #'` but your code produced `'* *'`. The lines below provide more detailed feedback, although in this case, they don't offer much more information. (Note that '\n' represents a new line.)

The last two tests are not run at all. The `:|` indicates that a test cannot be run because these last two tests will only run if the previous tests have succeeded.

### Multi-line output

When your code is supposed to produce multiple lines of output, `checkpy`'s output can become more confusing. For example:


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


 Here, the expected output was `'    # #\n  # # #\n# # # #'`, but the actual value was `'     # #\n  ...#\n # # # #\n'`. The '\n' indicates that everything following it should be on a new line. So, the expected output was:

        # #
      # # #
    # # # #

But the actual output:

         # #
       # # #
     # # # #

It's a subtle difference, but the detailed information below provides all the necessary information:

    -     # #              <---- expected first line
    +      # #             <---- actual first line
    ? +                    <---- the actual first line has an additional character (a space)
    -   # # #              <---- expected second line
    +    # # #             <---- actual second line
    ? +                    <---- the actual second line has an additional character (a space)
    - # # # #              <---- expected third line
    +  # # # #             <---- actual third line
    ? +       +            <---- the actual third line has an additional character (a space)

So, all lines of the output from your code have an additional leading space.

### Actual Python error

Sometimes, you might encounter something like this:

    $ checkpy greedy
    Testing: greedy.py
    :) the program does not use break or import statements
    :( rejects negative input, then accepts an input of 0.41
       "ZeroDivisionError('division by zero')" occured while trying to import the code

When you see something like "[Some error] occurred while trying to import the code," it means `checkpy` encountered an error while importing your code. This issue is unrelated to the test "rejects negative input, then accepts an input of 0.41." If you were to run your code normally using `python greedy.py`, you would also encounter an error:

    $ python greedy.py
    How much change is owed? 0.41
    Traceback (most recent call last):
    File "greedy.py", line 23, in <module>
    1/0
    ZeroDivisionError: division by zero        <---- this is the error that tripped up checkpy


### Function arguments

When using functions, `checkpy` often checks whether you defined the function exactly as specified. For example, in `list_words.py`, you are supposed to define a function `text_to_unique_words(text)`. If you name the function argument `tekst` instead of `text`, you'll get this error:

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

A common mistake is to forget to include a `return` statement at the end of the function. Another common mistake is to include a `print` statement within a `return` statement, like this: `return print(something)`. In both cases the function will return the value `None`. This often results in an assert error in the form of `assert None is of type ...`:

    Testing: list_words.py
    :) the program does not use break or import statements
    :) correctly defines the cleanup() function
    :( testing text_to_unique_words() >> text_to_unique_words("Test sentence") returns a value of type List[str]
       text_to_unique_words("Test sentence") returned: None
       assert None is of type List[str]
