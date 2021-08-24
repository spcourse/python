# Practice with time complexity of dictionaries
> **You don't have to hand in these practice exercises.** They're here for you to test yourself. Did you fully understood the theory you just learned?
>
> If there is an exercise that you don't know how to make, review the theory again. If that doesn't help, discuss the exercise with another student and/or the teacher.


Create a file called `functions.py` to work in.

**Exercise 1** Create a function `half` that accepts one number and returns that number divided by 2. So

    # your code here

    x = 4
    y = 3
    a = half(x)
    b = half(y)

    print(a, b)

should print

    2.0 1.5

**Exercise 2** Create a function `mean` that returns the mean between two numbers. So

    # your code here

    x = mean(4, 6)
    print(x)

should print

    5.0

**Exercise 3** Create a function `max` that takes two numbers and returns the maximum of the two. So

    # your code here

    x = 4
    y = 18
    z1 = max(x, y)
    z2 = max(y, x)

    print(z1, z2)

should print

    18 18

**Exercise 4** Create a function `maxx` that takes three numbers and returns the maximum. (If you're clever, you can do this by calling the function `max` from the previous exercise twice inside the function `maxx`)

**Exercise 5** Create a function `my_sum` that takes a list and computes the sum of its elements. So

    my_list = [1,2,3,4]
    s = my_sum(my_list)
    print(s)

should print

    10


## Answers
Below you can find answers to *some* of the exrecises.

Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.

You should not have to rely on the answers to the practice exercise. If you cannot make the practice exercises at all without looking at these answers, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers.</summary>
**Exercise 1**

    def half(val):
        c = val / 2
        return c

    x = 4
    y = 3
    a = half(x)
    b = half(y)

    print(a, b)

**Exercise 2**

    def mean(a, b):
        c = (a + b) / 2
        return c

    x = mean(4, 6)
    print(x)

**Exercise 3**

    def max(a, b):
        if a < b:
            return b
        else:
            return a

    x = 4
    y = 18
    z1 = max(x, y)
    z2 = max(y, x)

    print(z1, z2)

**Exercise 4**

    def maxx(a, b, c):
        max1 = max(a, b)
        max2 = max(max1, c)
        return max2

    m = maxx(1, 9, 4)
    print(m)

**Exercise 5**

    def my_sum(lst):
        acc = 0
        for number in lst:
            acc += number
        return acc

    my_list = [1,2,3,4]
    s = my_sum(my_list)
    print(s)

</details>
