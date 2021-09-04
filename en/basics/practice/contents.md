# Practice with the basics
> **You don't have to hand in these practice exercises.** They're here for you to test yourself. Did you fully understand the theory you just learned?
>
> If there is an exercise that you don't know how to make, review the theory again. If that doesn't help, discuss the exercise with another student and/or the teacher.

Test your understanding with the following practice exercises. Create a file called `basics.py` for your solutions.

**Exercise 1** Write a piece of code that prints the text "I'm learning Python!"

**Exercise 2** Given the code below, write a program that prints "I'm not learning [X]", where X is filled by whatever the contents of the variable programming_language is. So if programming_language = "Java", the code should print "I'm not learning Java".

    programming_language = 'Java'
    # your code here

**Exercise 3** Write a program that computes the product (multiplication) of the variables x and y, and prints the result.

    x = 6
    y = 7
    # your code here

**Exercise 4** The code below computes the division between x and y. At the moment it automatically rounds down to the closest whole number (integer). Change the code such that this computes the correct floating point number.

    x = 9
    y = 4
    z = x // y
    print(f"x divided by y is {z}")

**Exercise 5** How to distribute a specific number of oranges over a number of baskets? The code below computes this. However, when the amount of oranges is not divisible by the number of baskets, there will be oranges left (for you to eat). Finish the computation of `oranges_left` in the code below.

    oranges = 9
    baskets = 4
    oranges_per_basket = x // y
    oranges_left = 0 # todo: compute the correct value
    print(f"When I divide {oranges} oranges over {baskets} baskets...")
    print(f"I have {oranges_per_basket} oranges per basket...")
    print(f"and I will have {oranges_left} oranges left, to keep for myself!")

**Exercise 6** The code below doesn't give the expected result. Fix it.

    x = '32'
    y = '10'
    z = x + y
    print(f"x plus y is {z}")

**Exercise 7** The code below doesn't give the expected result. Fix it.
    x = input("Enter the first number: ")
    y = input("Enter the second number: ")
    z = x + y
    print(f"The first number plus the second number is {z}")

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    print("I'm learning Python!")

**Exercise 2**

    programming_language = 'Java'
    # your code here
    print(f"I'm not learning {programming_language}")

**Exercise 3**

    x = 6
    y = 7
    z = x * y
    print(f"x times y is {z}")

**Exercise 4**

    x = 9
    y = 4
    z = x / y
    print(f"x divided by y is {z}")

**Exercise 5**

    oranges = 9
    baskets = 4
    oranges_per_basket = oranges // baskets
    oranges_left = oranges % baskets
    print(f"When I divide {oranges} oranges over {baskets} baskets...")
    print(f"I have {oranges_per_basket} oranges per basket...")
    print(f"and I will have {oranges_left} oranges left, to keep for myself!")

**Exercise 6**

    x = 32
    y = 10
    z = x + y
    print(f"x plus y is {z}")

**Exercise 7**

    x = input("Enter the first number: ")
    y = input("Enter the second number: ")
    number_x = int(x)
    number_y = int(y)
    z = number_x + number_y
    print(f"The first number plus the second number is {z}")

<details>
