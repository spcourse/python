# $$\Sigma$$ over a list

 You saw before that $$\Sigma_{i=a}^b$$ maps directly onto `for i in range(a, b + 1)`. 
 
 You have now written `sum_list.py`, which sums the elements of a list. Your solution probably looked something like this:

    total = 0
    for x in numbers:
        total = total + x

This is still very closely related to $$\Sigma$$ (but now the thing you are summing over is a list, not a range of integers. In sum notation you would write it something like this:

$$
\textrm{total} = \Sigma_{i=1}^{n} a_i
$$

where $$a$$ is a collection (e.g. the list `numbers`) and $$n$$ is its length. The subscript $$a_i$$ means *"the element of $$a$$ at position $$i$$"*. So $$a_0$$ is the first element, $$a_1$$ is the second, and so on.

## The index version

If you follow the same translation as last week, you would write:

    total = 0
    for i in range(0, len(numbers)):
        total = total + numbers[i]

This is a perfectly correct translation of $$\Sigma_{i=1}^{n} a_i$$. Not only that in Python we start at `0`, not at $$1$$ (as mathematicians tend to do).

But, because looping over a list by index is so common, Python lets you skip the index entirely:

    total = 0
    for x in numbers:
        total = total + x

Here `x` takes on each value in `numbers` directly, without you having to write `numbers[i]`. Both versions compute exactly the same thing. The second is shorter and easier to read, which is why you will use it *most* of the time.
