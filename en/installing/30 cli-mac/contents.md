# Step 3: Command Line Interface

As a programmer, you will be using a command line interface (also often called terminal or shell) frequently. Through your terminal, you will be able to start and interact with programs, view outcomes of code you've written, and otherwise interact with your computer.

On Mac, the terminal is included in the Operating System, and comes pre-installed. You will be able to open a terminal by clicking on Spotlight (the small magnifying glass) in the upper right corner of your screen or pressing `cmd + space`, and typing "Terminal" then pressing enter. No further actions are required for this step

Navigating through your computer using the command line will be a vital skill. Watch the video below to get more familiar with command line commands. _You should ignore or skip any mentions of `nano`, as we will be using the much more user-friendly Pulsar to edit our files._

![embed](https://www.youtube.com/embed/aKRYQsKR46I)

### Quick installation test

To test whether each of our steps has been done correctly, we will write a small program named "hello". Open Pulsar and create a new file named `hello.py`. In this program, place the following code:

    print('Hello, world!')

Save your program in a folder that is easily accessible (we recommend you create a folder that will contain all your code from here on out) and open a terminal.

Using your terminal, navigate to the folder containing the file `hello.py`. Remember, use `cd` to change directory, `pwd` to print your current directory, and `ls` to verify that `hello.py` is in the folder you are currently in. Then, run the following command:

    python hello.py

If everything was done correctly, your command line will now show the text `Hello, world!`. Congratulations on writing and executing your first program!

### Init shell

During our courses, we will use some other Python libraries. We will download and install all these libraries through `conda` and place them in their own "environment". This makes sure that everything will work for all the exercises in the coming courses.

**At this point, it is very important to know what type of shell your computer uses. If you are using a Mac, you use either `bash`, or `zsh`. You can check by running `echo $0` in your terminal; if your computer uses `bash`, replace any future mention of `zsh` with `bash`.**

First, open a terminal and run the following command (and replace `zsh` with `bash` if needed):

    conda init zsh

This will instruct your terminal to prepare your terminal for running `conda` commands. **Close the terminal, and open a new one.** This will restart your terminal and makes sure that everything is initiated correctly.

To verify that the installation has worked, you can check whether your terminal shows something like `(base)` in front of every line in the terminal.
