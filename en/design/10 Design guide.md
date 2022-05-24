# Design

So far, we’ve only really cared about two aspects of code: whether the program works and the style and layout of the code itself. A third aspect is the design of the code. Have a look at this program, which prints all elements from a list:

      L = [3,1,4,1,5,2,9]
      for pos in range(len(L)):
          print(L[pos])

Here is another version:

      L = [3,1,4,1,5,2,9]
      for number in L:
          print(number)

The first program uses a variable `pos` that takes on the values 0 through 6 in order to print all numbers from the list. The second program prints the same output, but instead, _directly_ uses the numbers from the list for the loop. This makes the formulas less complicated and makes the program faster to read in one go.

Design is about the structure of your code: there are often countless solutions for a programming problem that in fact work the same. Still, it can be interesting to prefer one solution over the other. In the situation above, we would usually prefer the second variant. But that does not mean that the first variant never occurs!

Design is subjective to a certain extent. There are many choices you can make and sometimes you prefer to do something one way or the other, but it is important to keep an eye on the target! In this course, we limit ourselves to design choices that ensure that the code is as easily understandable as possible. This is often short code or simple code without complicated formulas. Below are a few rules of thumb.

- Avoid **repetitive** structures. Do you count to 10 twice in your program? Maybe you can try to limit that to one time. Or do you have very similar `if` structures in two different places?

- Remove **redundant** elements. You may have written a `for` loop that actually only goes once. Or an `else` where not much happens. You can then remove it.

- Avoid "**magic numbers**". Often in a problem, you have a number of elements with a fixed value. For example, if you’re calculating the circumference of the earth, you use the radius that you have looked up. Do not use such a constant directly in a formula, but create a variable with a name that describes the value well.

- Keep your code as **concise** as possible. By making good use of the elements of the programming language, you can write some things more briefly. For example, consider choosing a `for` or a `while` loop. **Note:** in this course you are limited to the language elements that we introduce. If you already have programming experience, this can sometimes be difficult, but even then, you can often be creative with the elements you have been given.

- **Separate** blocks of code into functions with a clear name, and complex formula's into multiple lines of code. Not only does this make things easier to find, it also enables you to easily debug specific functions or lines of code by studying inputs and outputs. Try to keep code that performs a distinct task away from code that doesn't have anything to do with this specific task. This might cause you to repeat structures, but your code becomes easier to read.

- Add layers of **abstraction**. If your code starts to get a bit long, you can often give pieces of code their own place; a new function. Even if you only use a function once, it can be useful to create one. Such a function has its own name, and if you read through the code quickly, you don't even have to read the entire contents of the function to understand it.
