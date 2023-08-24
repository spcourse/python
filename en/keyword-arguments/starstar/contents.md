## Passing a dictionary of keyword arguments with `**`

In addition to positional and keyword arguments, Python also allows us to use the so-called `**kwargs` notation to pass a number of keyword arguments to a function as a dictionary.

    def print_info(name, age, city):
        print(f'{name} is {age} years old and lives in {city}.')

    info_kwargs = {
      'name': 'Alice',
      'age': 30,
      'city': 'New York',
    }

The `print_info` function that we defined above has three arguments: `name`, `age`, and `city`. We have also defined the dictionary `info_kwargs`, that contains the names of these three arguments and the values we would like to assign to them. We can call the `print_info` function and pass the `info_kwargs` dictionary using the `**` operator:

    print_info(**info_kwargs)

This is called _unpacking_ and is equivalent to calling the function with three separate keyword arguments:

    print_info(name='Alice', age=30, city='New York')

This is especially useful when a function has a lot of arguments, we want to call the function many times with a set of different arguments, or when we want to pass arguments with values that are stored in a dictionary.

The advantage of using `**kwargs` in this way is that we can pass a large number of keyword arguments to a function without having to type them all out separately. This can make our code more readable, but also makes it very easy to change just one value at the time.

    for alice_age in range(30, 50):
        info_kwargs['age'] = alice_age
        print_info(**info_kwargs)

> If we have a function that takes a large number of keyword arguments, we might store those arguments in a configuration file or database, and then load them into a dictionary and pass them to the function using `**kwargs`.

### Unpacking arguments

Another useful feature in Python is positional argument unpacking. This allows you to expand an iterable (such as a list or tuple) into separate arguments when calling a function. This is done by placing an asterisk (`*`) before the iterable argument in the function call.

    def fun(arg1, arg2, arg3):
        print(arg1)
        print(arg2)
        print(arg3)

    args = [1, 2, 3]
    fun(*args)

In the example above, the `args` variable is a list of three elements. When `fun()` is called with `*args`, our list is unpacked and its elements are passed as separate positional arguments to the function. This is equivalent to calling `fun(1, 2, 3)`.

You can also use positional argument unpacking with a mix of regular arguments and iterable arguments:

    args = [2, 3]
    my_function(1, *args)

`fun()` still takes three arguments, but we only pass one argument directly, and then use `*args` to unpack the remaining arguments from our list.

> Note that the total number of values passed to the function must still be the same as the number of positional arguments in the function definition!
