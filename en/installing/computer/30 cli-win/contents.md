# Step 3: Command Line Interface

As a programmer, you will be using a command line interface (also often called terminal or shell) frequently. Through your terminal, you will be able to start and interact with programs, view outcomes of code you've written, and otherwise interact with your computer.

To get the right environment you will want to download and install Git Bash using the [instructions from this website](https://www.stanleyulili.com/git/how-to-install-git-bash-on-windows/). **After installation, you will be able to open a terminal by clicking the windows button in the lower left corner, and typing "bash" then pressing enter.**

Navigating through your computer using the command line will be a vital skill. Watch the video below to get more familiar with command line commands. The video is a guide to the Mac OS terminal, but Git Bash is able to use almost all the same commands and always shows you the complete path to your current directory. _You should ignore or skip any mentions of `nano`, as we will be using the much more user-friendly Pulsar to edit our files._

![embed](https://www.youtube.com/embed/aKRYQsKR46I)

> `open "<PATH>"` is not a valid command in Windows. You can instead use `explorer "<PATH>"` as a command. This will open the file path with Windows default associated programs.

### Quick installation test

To test whether each of our steps has been done correctly, we will write a small program named "hello". Open Pulsar and create a new file named `hello.py`. In this program, place the following code:

    print('Hello, world!')

Save your program in a folder that is easily accessible (we recommend you create a folder that will contain all your code from here on out) and open a terminal.

Using your terminal, navigate to the folder containing the file `hello.py`. Remember, use `cd` to change directory, `pwd` to print your current directory, and `ls` to verify that `hello.py` is in the folder you are currently in. Then, run the following command:

    python hello.py

If everything was done correctly, your command line will now show the text `Hello, world!`. Congratulations on writing and executing your first program!

### Init shell

During our courses, we will use some other Python libraries. We will download and install all these libraries through `conda` and place them in their own "environment". This makes sure that everything will work for all the exercises in the coming courses.

First, open a terminal and run the following command:

    conda init bash

This will instruct your terminal to prepare your terminal for running `conda` commands. **Close the terminal, and open a new one.** This will restart your terminal and makes sure that everything is initiated correctly.

To verify that the installation has worked, you can check whether your terminal shows something like `(base)` in front of every line in the terminal.
