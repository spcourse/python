**Exercise 1:** Please change this program by including another print statement: `print(f"The sum of all numbers from 1 to {x} = {total}")`. Include this line beneath `total = total + x`, in such a way that it starts at the same position (the same level of indentation). Run the program and try to understand what happens. Problems with indentation are a very common mistake when using loops, so it is important to see these types of 'mistakes' so you can recognize them later.

**Exercise 2:** At this moment we use the numbers from 1 to 10. Please try to adapt the program in such a way that you define a new variable once at the beginning of the program (so not in the range() function) that holds the maximum number. Use this maximum number as the maximum value for the for-loop: `for x in range(1, maximum)`.

**Exercise 3:** Make a program that has the same functionality as the example, but now use a while-loop instead of a for-loop.

**Exercise 4:** Replace the while-loop condition to ensure that it will stop if the sum of all numbers up to that point is bigger than 123. To help you, the expected output is provided:

	Value of sum_x: 0, value of x: 10
	Value of sum_x: 10, value of x: 11
	Value of sum_x: 21, value of x: 12
	Value of sum_x: 33, value of x: 13
	Value of sum_x: 46, value of x: 14
	Value of sum_x: 60, value of x: 15
	Value of sum_x: 75, value of x: 16
	Value of sum_x: 91, value of x: 17
	Value of sum_x: 108, value of x: 18
	End value of sum_x: 126, end value of x: 19

**Exercise 6:** Adapt the program in such a way that the print-statement is only executed *if* the sum of `x` and `y` is more than 6.

**Exercise 7:** Adapt the program in such a way that at the moment just before a new value is assigned to `x` (i.e. just after the loop over y is finished), the program prints: `The value of x is now ... and we have just finished the loop over y`.

The output should look as follows:

	x =  1,  y =  1
	x =  1,  y =  2
	x =  1,  y =  3
	The value of x is now 1, we have just finished the loop over y.
	x =  2,  y =  1
	x =  2,  y =  2
	x =  2,  y =  3
	The value of x is now 2, we have just finished the loop over y.
	...
	The value of x is now 5, we have just finished the loop over y.

**Exercise 8:** Adapt the program in such a way that `y` does not run from 1 to 4, but from 1 to the value of `x`.

**Exercise 9:** Adapt the program of exercise 8 to use a while-loop for the value of `y`. The for-loop for `x` stays the same.

**Exercise 10:** Adapt the original program in such a way that the loop over `y` is only executed *if* `x` is larger than 3. *Keep* the range(1,6) in the for-loop of `x` the same, using a conditional (an if-statement) as a solution.

Here's an example of what the output should be:

	x = 4, y = 1
	x = 4, y = 2
	x = 4, y = 3
	x = 5, y = 1
	x = 5, y = 2
	x = 5, y = 3

Could you get the same result by changing the range in the for-loop of `x`?
