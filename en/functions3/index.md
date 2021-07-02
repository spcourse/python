# Functions with multiple return values

Until now you've only seen functions that print and functions that return one value. In Python, it is possible to return multiple values by separating the values with commas. These values do not need to be of the same type, and are grouped as one output named a tuple:

    def test():
      return 'abc', 100, ['a', 'b', 123]

    print(test())

The output of the code would be:

    ('abc', 100, ['a', 'b', 123])

The round brackets indicating that the values are packed together in a tuple. A tuple is a special type of "collection" in Python, but for now it suffices to know that it behaves similar to a list of which the contents cannot be altered.

One could save the result of the function as a variable, and specific elements of the result can be indexed as in a list:

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

Similarly, it is possible to immediately _unpack_ the tuple that is returned by the function. This is done in much the same way as it was created, with comma separated variable names:

    a, b, c = test()

    print(a)
    print(b)
    print(c)

Which would give the following output:

    abc
    100
    ['a', 'b', 123]
