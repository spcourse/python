# Functions with multiple return values

Until now you've only seen functions that print and functions that return one value. In Python, it is possible to return multiple values by separating the values with commas. These return values do not need to be of the same type, and are grouped as if they are one output. It is possible to immediately _unpack_ the values that are returned by the function. This is done in much the same way as it was created, with comma separated variable names:

    def test():
      return 'abc', 100, ['a', 'b', 123]

    a, b, c = test()

    print(a)
    print(b)
    print(c)

Which would give the following output:

    abc
    100
    ['a', 'b', 123]

One could also save the result of the function as a single variable, and specific elements of the result can be indexed as in a list:

    test_result = test()

    print(test_result)
    print(test_result[0])
    print(test_result[1])
    print(test_result[2])

Would give the following output:

    ('abc', 100, ['a', 'b', 123])
    abc
    100
    ['a', 'b', 123]

The round brackets indicating that the values are packed together in a tuple. A tuple is a special type of "collection" in Python, but for now it suffices to know that it behaves similar to a list of which the contents cannot be altered.
