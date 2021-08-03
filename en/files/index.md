# Reading files and processing data

![](VanBastenKlein.jpg){:.inline}

Just like with numbers that can be expressed in the decimal, hexadecimal or binary format, data too can be represented in various formats within databases. Here we'll take a look at some data that is stored in the so-called CSV format (comma separated values): 'flat text', where each line has variables that are separated by a single comma. This happens to be the format you receive when you download your bank transactions or when you save an Excel file.

We'll learn how to read and process data with an example case: the statistics of the footballer Marco van Basten. Someone has been keeping track of how many matches he played and how many goals he scored in a [text file](http://www.nikhef.nl/~ivov/Python/Voetbal/VanBasten.txt). This is the text of the file:

    198182, Ajax, 1, 1
    198283, Ajax, 20, 9
    198384, Ajax, 26, 28
    198485, Ajax, 33, 22
    198586, Ajax, 26, 37
    198687, Ajax, 27, 31
    198788, AC Milan, 11, 3
    198889, AC Milan, 33, 19
    198990, AC Milan, 26, 19
    199091, AC Milan, 31, 11
    199192, AC Milan, 31, 25
    199293, AC Milan, 15, 13
    199394, AC Milan, 0, 0
    199495, AC Milan, 0, 0

> Note: when you open the file with Windows Notepad, all data will be shown in a single line. That does not affect your program in any way.

In the following sections we'll answer some questions using the data from the data file:

* What are the seasons in which Van Basten scored more than 20 times?
* What is the total number of goals that Van Basten scored for all clubs he played for?

We will be showing you how to read this file _without_ using Python's `csv`-module.

## Step 1: opening the file, reading the lines

Because traversing files in computer language is a standard procedure, there are a number of easy to use commands available. The `open()` command, for example, is used to gain access to a file so it can be read or written new data to. The following fragment of code opens a file and uses a `for`-loop to read lines one by one. The information in a line is saved in a variable called `line`. This short program performs no further analysis, instead it simply `print`s `line` to the screen.

    input_file = open('VanBasten.txt', 'r')
    for line in input_file:
        print(line)
    input_file.close()

The `'r'` argument in the `open()` function means 'read'. When you run this program you'll see that for example the line with the season of 1988-89 shows up on your screen as follows:

    198889, AC Milan, 33, 19

The whole line is stored as one string in the variable `line`, after which it is printed.

## Step 2: splitting of a line and save it in a list

Every line consists of different elements, or, columns. You can retrieve these elements by splitting them. You do this with the command `split()`. The parameter in this command determines where to split. We want to split at every comma (`,`), so we execute the following command: `line.split(',')`. By doing so, we get a list with the elements from that line. Subsequently, we can analyze these elements (plotting, statistics etc.).

    input_file = open('VanBasten.txt', 'r')
    for line in input_file:
        print(line)
        split_data = line.split(',')
        print(split_data)
    input_file.close()

The line with the season of 1988-89 is now split and turned into a list:

    ['198889', ' AC Milan', ' 33', ' 19\t\n']

The characters `"\t"` (tab) and `"\n"` (newline) are also visible; we don't really need to use those though. Note that even though we have split each of the elements in the line and now have a list, each of the elements is still of the type `string`. If we want to use the numbers as numbers we would need to convert the variables to `float`s or `int`s.

## Step 3: save the information in variables

In this exercise we are only interested in the season and the number of goals of that season. As you can see, this information is stored in element 0 and 2 of the list.

We can save this information in a variable:

    season = split_data[0]
    goals = split_data[2]

### Problem 1: unpacking the variables

As you might have observed, the creators of the file named the season 1988-1889 as one number: 198889. Smart of them, but we are only interested in the starting year of the season (1988).

The data is still stored in the list as a `string`. Although `198889` can be considered a number, the program still treats it as a piece of text. The year we are looking for is stored in the first 4 characters of that string. To only save this part of the string, we need the first 4 characters. We can use so-called "slicing for that:

    season = split_data[0][0:4]
    goals = split_data[2]

### Problem 2: numbers versus text

From now on it is easier to treat the data as a number, because only then we can calculate stuff with it. To ensure the data becomes numerical, we have to explicitly convert it.

    season = int(split_data[0][0:4])
    goals = int(split_data[2])

You now have all the information available in a variable. Now you can use everything you learned about Python to perform an analysis.


## Step 4: analyzing the data

We wanted to calculate the total number of goals van Basten has made for his club. In addition, we would like to know in which seasons he made more than 20 goals.


    input_file = open('VanBasten.txt', 'r')
    total_goals = 0

    for line in input_file:
        split_data = line.split(',')

        season = int(split_data[0][0:4])
        goals = int(split_data[2])

        total_goals = total_goals + goals   

        if(goals > 20):
            print(f"In {season} Van Basten scored > 20 goals, nl {goals}")

    print(f"TOTAAL: In total Van Basten scored {total_goals} clubgoals")
    input_file.close()

Always use `close()` to close the file you worked with after use.

## Exercise

Download the file with the goals statistics of van Basten and try to reproduce the results above.
