# From $$\Sigma$$ to `for`

You have written `sum.py`before. It adds up all integers from `a` to `b`. The algorithm you wrote probably looks something like this:

    total = 0
    for i in range(a, b + 1):
        total = total + i

This pattern (start at zero, loop over a range of numbers, add something each step) is very common programming. And it is closely related the mathematical **summation** $$\Sigma$$ (sigma).

## The $$\Sigma$$ notation

In mathematics you write the exact same computation as: 

$$
\textrm{total} = \Sigma_{i=a}^b i
$$


The three parts of the notation map directly onto your Python code:

- **`i=a`** below the $$\Sigma$$ is the start: `range(a, ...)`
- **`b`** above the $$\Sigma$$ is the end: `range(..., b + 1)` (note the `+1`, because `range` excludes the last value)
- **`i`** to the right of the $$\Sigma$$ is the expression added each step: `total = total + i`

The $$\Sigma$$ symbol itself represents the pattern: start a running total at zero and keep adding.

## The expression can be anything

The expression to the right of the $$\Sigma$$ can be any formula involving `i`. For example, the sum of all squares from $$1$$ to $$n$$:

$$
\textrm{total} = \Sigma_{i=1}^n i^2
$$

Translates directly to:

    total = 0
    for i in range(1, n + 1):
        total = total + i**2

## The general pattern

So, whenever you see a $$\Sigma$$ in a formula, you can translate it to:

    total = 0
    for i in range(start, end + 1):
        total = total + <expression involving i>

This translation so it is very useful to keep in mind as comes up constantly in physics and in machine learning (and during this course).
