# Reading, writing, and finding files; file Input/Output (I/O)

The following code will open a file and print every line:

    with open('some_file.txt', 'r') as f:
        for line in f:
            print(line, end='')

This will `open` `'some_file.txt'` in read mode (`'r'`), and assign it to the variable named `f`. Then, a for loop loops over every `line` in the file by finding the line endings indicated by `'\n'`. This `'\n'` is included in the variable `line`. The function print always adds a newline (another `\n`) when printing, unless we pass it `end=''`, which will make it add an empty string at the end. Let's say our file is set up as follows:

    'This is the first line of the file.\n Second line of the file.\n'

Then our program would output:

    This is the first line of the file.
    Second line of the file.

Throughout coming exercises and in future projects you will come across many situations where you need to read data from a file. In this writeup we will introduce you to some of the basics of reading, writing, and finding files using Python.

> All information that is in a box like the one this text is in, is advanced information which you can read if you want to know more about the methods.

## Opening a file

Let's start with the basics:

    f = open('some_file.txt', 'r')

`open()` returns a file object (in this case, we name it `f`), and is most commonly used with two arguments: `open(filename, mode)`. The first argument is a string containing the path to the file (including the filename). The second argument, `mode`, is another string containing a few characters describing what you will do with the file. `mode` can be `'r'` when the file will only be read, `'w'` for only writing (an existing file with the same name will be overwritten). It is also possible to open a file for both reading and writing with `'rw'`.

> Normally, files are opened in text mode, that means, you read and write strings from and to the file. Adding `'b'` to the `mode` opens the file in binary mode: now the data is read and written in the form of bytes objects. This mode should be used for all files that don’t contain text. It is also possible to open the file for appending (writing) at the end of the file: `'a'`.

_The rest of the examples assume that there is some variable `f` that holds an opened file object._

## File encodings

When using `open()`, it is possible to pass an optional parameter named `encoding`. This parameter can be set to one of the various text-encoding codecs that is available in Python. These codes define how the bits and bytes in the file should be interpreted as strings.

    f = open('some_file.txt', 'r', encoding='utf-8', errors='replace')

> Most data files use `utf-8`, and if the codec is not defined for your dataset, it is probably `utf-8`. More supported codecs are listed [here](https://docs.python.org/3/library/codecs.html#standard-encodings), but an easier way to deal with codec errors is to set the optional parameter `errors='replace'`. This replaces any unknown characters with the character of a question mark.

## Reading from a file

There are multiple ways to read a file's contents. None of the methods that are described here are wrong, but they all have their own advantages and disadvantages. It is up to you to select the appropriate method.

### Reading the whole file

To read an entire file's contents at once, call `f.read()`.

    text = f.read()
    print(text)

  Output:

    This is the first line of the file.
    Second line of the file.

> `f.read()` has an optional argument named `size` that can be used to read specific quantities of data from the file. When it is omitted, or negative, the entire contents of the file will be returned. This is not advisable for large files, as it will try to allocate memory for the entire file at once, which may not be available. The method is, however, very useful when you want to read a specific amount of data from a file. If the end of the file is reached, `f.read()` returns an empty string: `''`.

### Reading line by line

There are two methods of reading a file line by line. The first is `f.readline()`, which reads a single line from a file:

    line1 = f.readline()
    print(line1)
    line2 = f.readline()
    print(line2)

Output:

    This is the first line of the file.

    Second line of the file.


`f.readline()` stops when it finds a newline character `'\n'`, _which is included at the end of the string it returns_. An empty string is returned when the end of the file has been reached, while blank lines are represented by a string containing a newline: `'\n'`.

The second method of reading a file line by line is looping over the file object:

    for line in f:
        print(line)

Output:

    This is the first line of the file.

    Second line of the file.

Functionally, this is the same as calling `f.readline()` until an empty string is returned, but it results in slightly cleaner code.

> If you want to read all the lines of a file into a list of strings, you can also use `list(f)` or `f.readlines()`. Keep in mind that for large files this would require a lot of memory.

## Writing to files

Writing to files is fairly simple:

    some_string = 'something!'
    f.write(some_string)

 Use `f.write(some_string)` to write the content of `some_string` to the file. The method returns the _number of characters_ that were written to a file. Keep in mind that `f.write()` only accepts strings, so you might need to convert your variables to strings before writing them.

## Closing files

It’s important to remember that it’s your responsibility to close the file. _In most cases_, upon termination of an application or script, a file will be closed eventually. However, there is no guarantee when exactly that will happen, and until the file is closed it will keep using your computers resources.

You can use the `close()` method for this:

    f.close()

Keep in mind that once you close a file, you cannot interact with it anymore. So do this after all the reading and writing is doen. You'll typically wind up with a structure like this when reading files:


    # open file
    f = open('some_file.txt', 'r', encoding='utf-8', errors='replace')

    # do something with the content of the file
    for line in f:
        ...

    # close file
    f.close()

## The `with` keyword

The problem with the above construction is that if your program suddenly crashes before you reach the `f.close()` line, your file will not be properly closed. This can be avoided using the `with` keyword in stead of using `open()` and `close()` as described above:

    with open('some_file.txt', 'r') as f:
        data = f.read()

The advantage of using `with` is that the file is **automatically** properly closed, even if an exception is raised or an error occurs at some point.

<!-- ## CSV files

The Comma Separated Values (CSV) format and variations of it are some of the most common formats for scientific data. There is no standard method of generating files in this format, and as such it can be quite annoying to process CSV files. Let's say we have `example.csv` containing some names, identifiers, and age of a group of people:

    Name, Identifier, Age
    Pete, 1234, 34
    Magnus, 5232, 32
    Sharma, 0923, 48

CSV files typically start with a header naming each of the columns, but they don't have to. Sometimes there is extra information above the header, which you will have to skip over before starting to read the file.

Python's `csv`-module implements functions that are able to read and write most variations of data that is in CSV format. CSV files can be opened as any normal file, and then processed through `csv.reader()` as follows:

    >>> import csv
    >>> with open('example.csv', 'r') as csvfile:
    ...     rdr = csv.reader(csvfile)
    ...
    ...     # Every row is a list of strings, loop over each row
    ...     for row in rdr:
    ...         # Join all strings from the entire row into one big string, and print it
    ...         print(', '.join(row))
    Name, Identifier, Age
    Pete, 1234, 34
    Magnus, 5232, 32
    Carl, 0923, 24

Here, `row` is a list that contains every element that was originally separated by commas, essentially functioning the same as `string.split()`.

The `csv`-module has more functionalities than just this simple reader, but for now it is everything you will need. -->
