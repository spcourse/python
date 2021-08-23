# Practice with algorithms
> You don't have to hand in these exercises. These are practice exercises that you can use to test if you fully understood the material you just studied.

Test your understanding with the following practice exercises. Create a file called `algorithms.py` for your solutions.

**Exercise 1** Write an if-statement that checks if the value of the variable `x` is lower than 50. If this is the case, print "foo", else print "bar".

    x = 12
    # your code here

**Exercise 2** Write an if-statement that checks if the value of variable `x` is lower than the value of variable `y`. If this is the case add the value `5` to `y`, else set `y` to `0`

    x = 9
    y = 10
    # your code here

print(y)

**Exercise 3** The height of a fine for speeding with a car in The Netherlands depends on how much faster than the limit you're going. On the highway the fines are given in the table below.

Highway fines in The Netherlands (2020):

| speed (exceeding limit)  | fine |
| ------------------------ | ---- |
| 5 km/h                   | 30 euros |
| 10 km/h                  | 64 euros |
| 20 km/h                  | 174 euros |
| 25 km/h                  | 232 euros |

Write a program that prints how high the fine is given the value of the variables `speed` and `limit` below. Of course, the code should also work correctly for different values of `speed` and `limit`

    speed = 120
    limit = 100
    # your code here

**Exercise 4** The code below is repeated from the video. It asks the user to enter its age. If the age is below 18 or the age is 65 or above, the user gets a discount to the museum.

Now, the museum changed it's policy: Children below 12 can enter the museum for free. Adapt the code such that if the age is below 12 it will print the text "Free entrance!" in stead of "You receive a discount at the museum."

    user_input = input('What is your age? ')
    age = int(user_input)

    if age < 18 or age >= 65:
        print("You receive a discount at the museum.")
    else:
        print("No discount.")

**Exercise 5** We continue with the code from 1.1. Students will also receive a discount. Ask the user for a second input with the question: "Are you a student (y/[n])?". If the student answers "y" or "yes", make sure the message "You receive a discount at the museum." is printed in stead of "No discount.", regardless of the age.

## Solutions
Below you can find some solutions.

Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.

You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    x = 12
    if x < 50:
        print('foo')
    else:
        print('bar')

**Exercise 2**

    x = 9
    y = 10
    if x < y:
        y += 5
    else:
        y = 0

**Exercise 3**

    speed = 120
    limit = 100

    if speed - limit > 25:
    print('Your fine is 232 euros.')
    elif speed - limit > 20:
    print('Your fine is 174 euros.')
    elif speed - limit > 10:
    print('Your fine is 64 euros.')
    elif speed - limit > 5:
    print('Your fine is 30 euros.')

**Exercise 4**

    user_input = input('What is your age? ')
    age = int(user_input)

    if age < 12:
        print("Free entrance!")
    elif age < 18 or age >= 65:
        print("You receive a discount at the museum.")
    else:
        print("No discount.")

**Exercise 5**

    user_input = input('What is your age? ')
    is_student = input('Are you a student (y/[n])? ')
    age = int(user_input)

    if age < 12:
        print("Free entrance!")
    elif age < 18 or age >= 65 or is_student == 'y' or is_student == 'yes':
        print("You receive a discount at the museum.")
    else:
        print("No discount.")

<details>
