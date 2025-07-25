# Style Guide

Preferably, code is easy to read and understand. Not only for yourself, but also for any collaborators. In this course it is important to not only take the functionality of the code into account ("how do I write code to do something"), but also the quality of the code ("is my code readable"). In this text you can find more aspects that explain how to comment your code properly.

## Terminology

To start, some terminology:

- We often talk about "programs". A *program* is an entity, a piece of software designed to execute a task or an action. Think about a calculator on your phone, or Microsoft Word. Python itself is also a program. In this course, you'll write a variety of programs yourself.
- We also often talk about "code". A piece of *code* is a fragment, often a part of a program. The word code is not countable (i.e. you cannot talk about "one code" or "two codes"). You can say "my code doesn't work", in that case it is evident that you talk about the code you just have been working on.
- A program consists of "lines" of code.

## Choice of Language

Make sure you work in one language only: variable names and comments should both be in the same language.

## Comments

It is just as easy to write a lot of comments in your code as it is to write too few comments. To determine where comments are really needed, we should put ourselves in the position of the reader of the code. This could be someone else, someone that uses your code to write their own nice program. However, it could also be yourself, a few months later, desperately trying to decipher your own code. What information does this reader need?

- Summaries of blocks of code. Often, you will have divided your code in functional blocks. Sometimes, these are composed of only a few lines of code. It is usually not difficult to summarize and describe the functionality of that piece of code.
- Warnings for potential problems. Maybe you came up with a temporary solution to a problem, of which you know it will not work for some cases (but for now, it's fine). In that case, it is handy to document your doubts with a comment.
- Explanation of complex algorithms. Sometimes you write very complex code. In that case, you can give an explanation of the algorithm or provide a link for more information.
- Source references. To avoid plagiarism, it is of course important to mention all sources used when fully or partially using other people's code. Even if you change this person's code it is important to still refer to the source.

### Example 1

Comments are not always necessary. When variable or function names are very clear, and the operations are relatively simple, it might not be necessary to add a comment. Sometimes, comments are still useful though:

    # calculate the average grade for this student
    average = sum / assignment_count + 1

(We now know the average is the average grade of the student. Depending on the rest of the program, this comment can be useful.)

#### Writing Style

Also pay attention to your writing style: do not use capital letters or interpunction in your comments. Add a space after the hash. Comments should be written directly *above* the line or block of code it is about.

    # comments go here
    solution = 12 + partial_solution # not here
    # not here

Comments should always have an extra whitespace above them, such that they separate different codeblocks:

    # first block of code
    example = 12 * 3
    result = example / 3

    # second block of code
    final = example + result


### Example 2

Usually, at the top of programs some general information is provided. This part often contains the names of the authors and a summary of the goal of the program. Here, you are allowed to use full sentences with capital letters or interpunction

    # Name: Jane Lee
    # Collaborators: John Doe
    #
    # This program calculates the average values of a series
    # of numbers input by the user.

### Example 3

Documentation strings, or docstrings, are strings enclosed in double (""") or single (\'\'\') quotation marks that appear on the first line of any function, class, method, or module. You can use them to explain and document a specific block of code.


    def my_complex_function(some_value):
        """
        This complex function takes some_value and does some complicated calculations
        with it. After those calculations, the resulting value is returned.
        """
        result = some_value + 1

        return result



#### Writing style

Note the writing style in this example. The summary in the comment above is too long for one line. If that is the case, the comment should be divided over multiple lines explicitly. Just add another line with a `#` in front of it.

We have chosen to truncate after 80 characters. Lines should have a length of approximately 45-90 characters, as is the case in books. This makes your code and comments easy to read.

## Indentation

Indentation is about adding whitespace at the start of a new line. In Python it is often necessary to start a rule with spaces, for example when defining a function:

    def sum(x, y):
        result = x + y
        return result

Beware! Always use tabs OR spaces, not both! In many cases, a tab is visible as 8 spaces, but sometimes also as 4 or 2 spaces. However, this becomes a problem when tabs and spaces are used interchangeably. It is then unclear how the code should be executed.

    def sum(x, y):
        # 4 spaces
        result = x + y
            # 1 tab became 8 spaces here
            return result  

The `return` is shown slightly more to the right, although only one tab is used. The result is that the code is less readable. In addition, Python will not be able to understand your code and error messages will probably pop up. Be consequent in using spaces or tabs to indent your code.

Oh, and as mentioned before, if a line ends with a colon (`:`), all lines below should be indented if they belong to the rule with the colon.  

    def sum(array_of_numbers):
        result = 0
        for number in array_of_numbers:
            result = result + number
        return result

Here you see that the line `result = result + number` belongs to the `for`-loop. The `return` does not belong to the `for` loop and therefore has less whitespace in front of it.

## Naming Conventions

Many elements in your code, such as variables and functions, have a *name*. Here we give some guidelines for naming your variables and functions.

### Functions

Names of functions can be as long as you like, but keep it reasonable (and readable). In this case, it is important that the goal of the function is described as clearly and precisely as possible.

    def user_average_this_year():
        ...

You can see that there are multiple words in this function name, divided by an underscore (`_`). This is conventional in Python; all function names are written with multiple words divided by underscores and without capital letters.

### Variables

Preferably, names of variables are shorter, as they are generally used more often. Think about a length on one to two words, a few examples:

    wall_height = 2.34
    earth_circumference = 40007.86
    total_rainfall = 823.3

Making abbreviations of words is often not preferred. By doing so, your code will be more difficult to read (a lazy programmer could abbreviate the above examples as `wh`, `ecirc` and `t_rain`, how can you find out afterwards what was meant here?).

There are exceptions. When your program is about topics where abbreviations are conventional. Physics and mathematics, for example.

    # v is for "velocity"
    v_rabbit = 0.002

    # x is for "displacement"
    x_rabbit = 23.11

Still, explanations have to be added. Thus, avoid abbreviations unless it is evident what the abbreviation stands for.

## Blank Lines and Extra Spaces

As is the case in other media where text plays an important role, blank lines and whitespace can be used to improve readability.

### Blank Lines

As described in the "comments" section, you can divide your program in logical code blocks. This way, it is possible to describe the different steps of an algorithm. Here, a program is split in three major parts:

    user_input = input("Please enter a number: ")
    number = int(user_input)
    while number < 0:
        user_input = input("Please enter a *positive* number: ")
        number = int(user_input)

    # calculations: uses a complex loop to handle special cases
    while(number > 0):
        number -= 1
    if number == 0:
        number += 1

    # output: might not print zero (e.g., if user put in a float)
    print(number)

The three components are the user's input, the calculation and the output, respectively. You will encounter these components very often in programs. Also, pay attention to the instructions in the comments: first an explanation of the algorithm, and then a warning that that part of the code might not always work (and more important: when this happens!).

### Spaces Around Operators

Operators such as `+`, `==`, `%` and `**` are often used in formulas and equations. Use spaces around operators, in order to keep formulas readable:

    i = i + 1
    submitted += 1
    x = x * 2 - 1
    hypotenuse_squared = x * x + y * y
    c = (a + b) * (a - b)

> Note: When `=` is used to assign a default value to a function argument, do not surround it with spaces; `def function(default_parameter=5):`.

## Pure functions

Ideally functions should, given an input, always produce the same output, and not change their behavior depending on the context. This means that a function shouldn't rely on variables outside of that function. Let's look at a couple of examples.

Bad implementation:

    my_mail = "hakim@ajax.nl"

    def get_name():
        name = my_mail.split('@')[0]
        return name

    print(get_name())

Very bad implementation:

    my_mail = "hakim@ajax.nl"

    def get_name(mail):
        name = my_mail.split('@')[0]
        return name

    print(get_name(my_mail))

Good implementation:

    my_mail = "hakim@ajax.nl"

    def get_name(mail):
        name = mail.split('@')[0]
        return name

    print(get_name(my_mail))

In the first two examples, the function contains a reference to the variable `my_mail` that is defined _outside_ of the function. This means that the output of the function depends on the value of that variable, which is not the input of the function. The second might look better but is actually worse: The function has an input parameter `mail`, but that parameter is not used inside of that function.

The last example shows the correct implementation of this function. It contains no reference to the variables outside the function (`my_mail`), but instead refers to the input parameter (`mail`).

Another example:

Bad implementation:

    number_list = [1, 2, 3, 4]

    def sum(numbers):
        sum_agg = 0
        for i in number_list:
            sum_agg = sum_agg + i
        return sum_agg

    print(sum(number_list))

Good implementation:

    number_list = [1, 2, 3, 4]

    def sum(numbers):
        sum_agg = 0
        for i in numbers:
            sum_agg = sum_agg + i
        return sum_agg

    print(sum(number_list))


## Structure

It is important to keep the structure of your code simple. An overly complex
structure and a lot of duplicated code is hard to understand and prone to bugs.
Let's have a look at some examples.

#### Example 1

The bad implementation below contains two duplicated lines of code. _In this case_,
this can be easily avoided by moving the duplicated lines outside of the if-statement.

Bad implementation:

    number = int(input('Enter a number: '))

    if number < 22:
        print(f'{number} is smaller than 22')
        x = number + 10
        print(f'The value of x is {x}')
    else:
        print(f'{number} is bigger than or equal to 22')
        x = number + 10
        print(f'The value of x is {x}')

Good implementation:

    number = int(input('Enter a number: '))

    if number < 22:
        print(f'{number} is smaller than 22')
    else:
        print(f'{number} is bigger than or equal to 22')

    x = number + 10
    print(f'The value of x is {x}')    


#### Example 2

Don't use unnecessary conditions. In the code below, the _condition_ in the `elif`
statement is mutually exclusive with the condition from the `if` statement above.
In this case, an `else` suffices.

Bad implementation:

    if number < 22:
        print(f'{number} is smaller than 22')
    elif number >= 22:
        print(f'{number} is bigger than or equal to 22')

Good implementation:

    if number < 22:
        print(f'{number} is smaller than 22')
    else:
        print(f'{number} is bigger than or equal to 22')

#### Example 3

Avoid very deeply nested code. Nesting many `if`, `for` and `while` statements inside of each other
makes code very hard to understand, which will inevitably lead to bugs.

Bad implementation:

    i = 8
    if i < 10:
        while i < 10:
            if i % 2 == 0:
                print(f'{i} is even')
            else:
                if i % 3 == 0:
                    print(f'{i} is divisible by three')
            i = i + 1

Good implementation:

    i = 8
    while i < 10:
        if i % 2 == 0:
            print(f'{i} is even')
        elif i % 3 == 0:
            print(f'{i} is divisible by three')
        i = i + 1

In the code above, it was rather easy to avoid a lot of the nesting. The bad
implementation is nested four levels deep whereas the good implementation has only
two levels. It is not always this straight forward, but it is rarely necessary to
have very deeply nested code.

#### Example 4

Always write all your functions first, followed by the code that uses them at the bottom of the file. This approach enhances readability and allows readers to easily locate and understand the functional components of your code.

Bad implementation:

    number = int(input('Enter a number: '))

    def add_ten(n):
        return n + 10

    print(add_ten(number))

    number = int(input('Enter another number: '))
    print(add_ten(number))

Good implementation:

    def add_ten(n):
        return n + 10

    number = int(input('Enter a number: '))
    print(add_ten(number))

    number = int(input('Enter another number: '))
    print(add_ten(number))

This practice is particularly crucial for larger files with multiple functions. By defining all functions at the top, your script remains logically organized, making it easier to understand each function's purpose and functionality. The execution code goes at the bottom, ensuring a clear separation between function definitions and their usage.

#### Rule of thumb

This is by no means an exhaustive list of examples, and it would be impossible to
give you one. But, as a general rule of thumb, typical indicators of overly complex
code are repeated code fragments and deeply nested code fragments. When you catch
yourself writing such code, always ask yourself if it can be simplified.
