# Practice with lists
> **You don't have to hand in these practice exercises.** They're here for you to test yourself. Did you fully understood the theory you just learned?
>
> If there is an exercise that you don't know how to make, review the theory again. If that doesn't help, discuss the exercise with another student and/or the teacher.

Create a file called `lists.py` for your solutions.


**Exercise 1**
Print the first and last element of the list below:

    list = ["banana", 10.9, 2, "fruit", 42]
    # your code here

**Exercise 2**
Change the second element (`10.9`) of the list from the previous exercise, by the value `"hello"`

**Exercise 3**
Write a loop that prints each of the elements of the list below on a new line:

    list = ["1kg apples", "100g sugar", "1 tsp cinnamon", "1 lemon", "300g flour", "1 tsp baking powder"]
    # your code here

**Exercise 4**
Write a loop that creates a list containing the numbers 1 to 30.

**Exercise 5**
Write a loop that determines the sum of the elements of the list below:

    list = [9, 10, 11, 12]
    sum = 0

    # your code here

    print(sum)

**Exercise 6**
The code below goes over each element from `numbers`, if it is bigger than 5, it is stored in `numbers2`:

    numbers = [8, 2, 3, 15, 7, 19]

    numbers2 = []
    for number in numbers:
        if number > 5:
            numbers2.append(number)

    print(numbers2)

Change this code, such that it selects all numbers that are above 5 *and* below 16.


**Exercise 7**
Change the code from the exercise above, such that it does *not* create the new list `numbers2`.
Instead it maintains a variable `count` that counts the *number of elements* that are above 5 *and* below 16.

**Exercise 8**
Create a piece of code that creates a list of all numbers between `0` and `n` that are divisible by 3 and 5. (You might want to use `range()` here).

    n = 123
    # your code here


## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    list = ["banana", 10.9, 2, "fruit", 42]
    print(list[0])
    print(list[4]) # or print(list[-1])
    # your code here

**Exercise 2**

    list[1] = "hello"
    print(list)

**Exercise 3**

    list = ["1kg apples", "100g sugar", "1 tsp cinnamon", "1 lemon", "300g flour", "1 tsp baking powder"]
    for e in list:
        print(e)

**Exercise 4**

    l = []
    for i in range(1, 31):
        l.append(i)
    print(l)

**Exercise 5**

    list = [9, 10, 11, 12]
    sum = 0

    for e in list:
        sum += e

    print(sum)

**Exercise 6**

    numbers = [8, 2, 3, 15, 7, 19]

    numbers2 = []
    for number in numbers:
        if number > 5 and number < 16:
            numbers2.append(number)

    print(numbers2)

**Exercise 7**

    numbers = [8, 2, 3, 15, 7, 19]

    count = 0
    for number in numbers:
        if number > 5 and number < 16:
            count += 1

    print(count)

**Exercise 8**

    n = 123
    list = []
    for i in range(n):
        if i % 3 == 0 and i % 5 == 0:
            list.append(i)
    print(list)


</details>
