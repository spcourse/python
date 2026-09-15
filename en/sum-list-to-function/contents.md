# From algorithm to function

Let's have a look at a `sum_list.py` solution:

    numbers = []
    number = float(input("Enter a positive number: "))
    while number > 0:
        numbers.append(number)
        number = float(input("Enter a positive number: "))

    total = 0
    for x in numbers:
        total = total + x

    print(f"The sum of {numbers} is {total}.")

The program has two clearly separate parts 1) Collecting input and 2) Computing the sum.

The second part is the interesting one for learning about functions. It is a reusable piece of code: given *any* list of numbers, compute their sum. 

## Extracting the function

To turn the computation into a function, we copy that peace of code and put it inside the function. We have to make sure that the **input parameter** is called `numbers`, because that is the variable that serves as the input of this code:

    def sum_list(numbers):
        total = 0
        for x in numbers:
            total = total + x
        return total

## The full refactored program

This function in the context of the full program will look like this:

    def sum_list(numbers):
        total = 0
        for x in numbers:
            total = total + x
        return total

    input_numbers = []
    input_numbers = float(input("Enter a positive number: "))
    while number > 0:
        input_numbers.append(number)
        number = float(input("Enter a positive number: "))

    sum = sum_list(input_numbers)
    print(f"The sum of {input_numbers} is {sum}.")

The program produces exactly the same output as before. The difference is that `sum_list` can now easily be used in any context where we would want to compute the sum of a list.
