# Functions with multiple return values

Until now you've only seen functions that print and functions that return one value. In Python, it is possible to return any number of values by separating the values with commas. This is named _packing_; the return values do not need to be of the same type, and are grouped as if they are one output. It is possible to immediately _unpack_ the values that are returned by the function. This is done in much the same way as the return value was created, with comma-separated variable names:

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

In most cases, you will want to return two or three values. More is possible, but if you want to return a lot of values it is probably better to return a list or some other data structure.

One could also save the result of the function as a single variable, and specific elements of the result can be indexed as in a list:

    def hours_to_days(hours):
      days = floor(hours / 24)
      remainder = hours % 24

      return days, remainder

    test_result = hours_to_days(123)

    print(test_result)
    print(test_result[0])
    print(test_result[1])

Would give the following output:

    (5, 3)
    5
    3

The round brackets indicating that the values are packed together in a tuple. A tuple is a special type of "collection" in Python, but for now, it suffices to know that it behaves similar to a list.
