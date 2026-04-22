# From algorithm to function

Here is the full solution to `sum_list.py`, exactly as you wrote it:

    numbers = []
    number = float(input("Enter a positive number: "))
    while number > 0:
        numbers.append(number)
        number = float(input("Enter a positive number: "))

    total = 0
    for x in numbers:
        total = total + x

    print(f"The sum of {numbers} is {total}.")

The program has two clearly separate parts:

1. **Collecting input** — the `while` loop that builds up `numbers`
2. **Computing the sum** — the `for` loop that produces `total`

The second part is the interesting one. It is a reusable piece of logic: given *any* list of numbers, compute their sum. The first part is just the specific way *this* program happens to get its data. Let's turn the second part into a function.

## Extracting the function

To turn the computation into a function, we lift it out of the program and give it a name. Inside the function, the list is no longer called `numbers` — that name belongs to the program. Instead, we call it `lst`, a generic name that signals the function works on any list, not just one called `numbers`:

    def sum_list(lst):
        total = 0
        for x in lst:
            total = total + x
        return total

Notice what changed and what stayed the same:

- The `for` loop is **identical** — only `numbers` was replaced by `lst`
- `total` is computed the same way, but instead of printing it, we `return` it
- `lst` is not defined anywhere inside the function — it is the *parameter*, the placeholder that will be filled in when the function is called

## Calling the function

When you write `sum_list(numbers)`, Python takes the list that `numbers` points to and makes `lst` point to the same list for the duration of that call. The names are different; the data is the same.

## The full refactored program

    def sum_list(lst):
        total = 0
        for x in lst:
            total = total + x
        return total


    numbers = []
    number = float(input("Enter a positive number: "))
    while number > 0:
        numbers.append(number)
        number = float(input("Enter a positive number: "))

    total = sum_list(numbers)
    print(f"The sum of {numbers} is {total}.")

The program produces exactly the same output as before. The difference is that `sum_list` can now be called with *any* list — from user input, from a file, or hardcoded — without touching the input logic. That separation is the point of writing a function.