# Practice with for-loops
> **You don't have to hand in these practice exercises.** They're here for you to test yourself. Did you fully understand the theory you just learned?
>
> If there is an exercise that you don't know how to solve, review the theory again. If that doesn't help, discuss the exercise with another student and/or the teacher.

Test your understanding with the following practice exercises. Create a file called `for-loops.py` for your solutions.

## Exercises

**Exercise 1** Write a for-loop that prints the numbers 1 to 50.

**Exercise 2** Write a for-loop that prints the numbers between 1 and 50 with steps of 2.

**Exercise 3** Write a for-loop that loops over the numbers 0 up to and including 100 with steps of 4 and adds them all together. Print the result.

**Exercise 4** Write a for-loop that prints the following:

    10
    8
    6
    4
    2

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    for i in range(1, 51):
        print(i)

**Exercise 2**

    for i in range(1, 51, 2):
        print(i)

**Exercise 3**

    total = 0
    for i in range(4, 101, 4):
        total += i
    print(total)

**Exercise 3**

    for i in range(10, 0, -2):
        print(i)
</details>
