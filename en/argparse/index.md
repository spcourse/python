# Introduction to `argparse`

`argparse` is a module that is included with Python by default. It allows you to write scripts that accept inputs from the command line, making your programs more flexible and user-friendly.

`argparse` is designed in an Object-Oriented Programming (OOP) style, which makes it intuitive and easy to configure. It supports a wide range of features, from very basic command line arguments to more complex functionality like subcommands. On this page, we’ll provide the most basic of overviews to help you get started quickly. For more information, you can always take a look at the [`argparse` documentation](https://docs.python.org/3/library/argparse.html).

## Basic Example

Here’s a simple script that accepts a file name as a command-line argument:

    import argparse

    # Create a parser object
    parser = argparse.ArgumentParser(description="A script to demonstrate argparse")

    # Add an argument
    parser.add_argument(
        'filename',
        help="The name of the file to process"
    )

    # Parse the arguments
    args = parser.parse_args()

    # Access the argument
    print(f"The file name is: {args.filename}")

### Breaking it down

To use `argparse`, you always start in the same way:

    parser = argparse.ArgumentParser(description="Description of your program here")

This creates a parser object, which is responsible for managing your program's command-line arguments. The `description` parameter provides a short explanation of what your program does, which will be displayed when the user runs the program with the `-h` or `--help` flag.

You can add arguments to your program by doing the following:

    parser.add_argument("argument_name", help="Text that explains how to use this argument")

This line defines a new positional argument named `argument_name`. The `help` parameter is used to provide a short description of the argument, which will be displayed in the program’s help message. Of course, you can repeat `add_argument()` multiple times to add more arguments.

After you have added all arguments you would like to add to your program, you use `parse_args()` to read and process the command-line arguments:

    args = parser.parse_args()

`args` now contains an object holding all the values entered by the user of your program as attributes. In our example above, we have defined an argument named `filename`, which is now available as an attribute of `args`: `args.filename`

### Running the example

You can run the example script as follows:

    python script.py my_file.txt

Which will output:

    The file name is: my_file.txt

If you forget to provide the `filename` argument, `argparse` will display an error and show usage instructions automatically:

    python script.py

Output:

    usage: script.py [-h] filename
    script.py: error: the following arguments are required: filename

### Getting help

You can also get an overview of the automatically generated usage instructions by calling your script with the optional argument `-h`:

    python script.py -h

Output:

    usage: example.py [-h] filename

    A script to demonstrate argparse

    positional arguments:
      filename    The name of the file to process

    optional arguments:
      -h, --help  Show this help message and exit
