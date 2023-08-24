## Keyword arguments

In Python, keyword arguments can be used to pass arguments to a function using their parameter names. This can make functions with many input paramaters a lot easier to use when only few of these parameters are changed. It also makes your code more readable, and helps avoid errors, since it also allows you to change the order of the parameters.

Here's an example:

    def print_info(name, age, city):
        print(f'{name} is {age} years old and lives in {city}.')

In this function, we have three parameters: `name`, `age`, and `city`. If we call the function and pass arguments by position, we need to make sure that we pass them in the correct order:

    print_info('Alice', 30, 'New York')

Which will output:

    Alice is 30 years old and lives in New York.

If we swap the order of the arguments, we might get unexpected results:

    print_info('New York', 30, 'Alice')

This will output:

    New York is 30 years old and lives in Alice.

Instead of passing the arguments by position, we can pass them using their parameter names:

    print_info(name='Alice', age=30, city='New York')
    print_info(city='New York', age=30, name='Alice')

Which will, despite the order being different, both produce the same output as before:

    Alice is 30 years old and lives in New York.
    Alice is 30 years old and lives in New York.

This also works when you have a function that has *default arguments*, and comes in especially handy when you want to change only one specific argument to some value that is not its default. The following function has 3 default arguments and calculates the volume of a beam:

    def calculate_volume(height=1, width=1, depth=1):
        return height * width * depth

By default, the function calculates the volume of a beam with a `height`, `width`, and `depth` of length 1 (a cube). If we would like to change just the `depth` of the beam to the value `3` *without* using *keyword arguments*, we would need to do the following:

    print(calculate_volume(1, 1, 3))

However, if we use keyword arguments, the following is also possible:

    print(calculate_volume(depth=3))

By not providing values for the `height` and `width` arguments, they assume their default values of `1`, while the value for `depth` is specifically set to `3`.

> Keyword arguments are often used when writing code that makes use of big libraries like Pandas or Numpy. These type of libraries have functions that have a lot of parameters, of which you often only want to use a few. By using keyword arguments, we do not have to manually assign a value to all different parameters of the function.
