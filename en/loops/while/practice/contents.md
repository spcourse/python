# Practice with while-loops
> You don't have to hand in these exercises. These are practice exercises that you can use to test if you fully understood the material you just studied.

Test your understanding with the following practice exercises. Create a file called `while-loops.py` for your solutions.

## While-loop exercises
**Exercise 1** Write a while-loop that continues dividing the variable `s` until the result is 1. Print the value of s at every iteration.

    s = 128
    # your code here

**Exercise 2** Based on the code of the previous exercise. Introduce a second variable called `i`, that counts how many iterations the while-loop runs. Print the resulting value of `i` after the loop is done.

## For/while exercises
**Exercise 3** Consider the following piece of code:

    for i in range(1, 5, 2):
        print(i)

Rewrite this piece of code such that the behavior stays the same, but it uses a while-loop instead of a for.

**Exercise 4**
Consider the following piece of code:

    x = 2
    while x < 12:
        print(x)
        x += 3

Rewrite this such that the behavior stays the same, but it uses a for-loop instead of a while.

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    s = 128
    while s > 1:
        s /= 2
        print(s)

**Exercise 2**

    s = 128
    i = 0
    while s > 1:
        s /= 2
        i += 1
        print(s)
    print(i)

**Exercise 3**

    i = 1
    while i < 5:
        print(i)
        i += 2

**Exercise 4**

    for x in range(2, 12, 3):
        print(x)

</details>
