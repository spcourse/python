# Python on your own computer

To be able to program on your own computer you will need a couple different programs:

1. **Miniconda**, a version of Python that is easy to install.

2. **Atom**, an *editor* to write code in. This is, in a way, just a text writing program, but specifically meant for programming code. For example, it highlights particular parts of your code in specific colors, so you can more easily distinguish which part of your code does what.

3. A *command line interface* from which we will provide you with methods to start and interact with your programs. macOS comes with one!

Stuck during any part of the process? Consult one of the teachers or a teaching assistant!

### Step 1: Miniconda

This package can be downloaded from the [Anaconda website](https://docs.conda.io/en/latest/miniconda.html). If you're using a newer Mac with M1 or M2 chip you'll need [this](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.pkg) version, otherwise the Intel x86 version can be found [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg).
_Not sure? Open the Apple menu and choose "About This Mac" to check you processor type._

As soon as the download is finished execute the downloaded file. Follow the installation instructions of the program. You do not have to alter any of the options.

The installation might take a while.

![](../wait2.gif){:style="max-width:25%"}

### Step 2: Atom

This package can be downloaded from the [Atom website](https://github.com/atom/atom/releases/tag/v1.60.0). Download the file named `atom-mac.zip`. After downloading you should be able to run it.

### Step 3: Command Line Interface

As a programmer, you will be using a command line interface (also often called terminal or shell) frequently. Through your terminal, you will be able to start and interact with programs, view outcomes of code you've written, and otherwise interact with your computer.

On Mac, the terminal is included in the Operating System, and comes pre-installed. You will be able to open a terminal by clicking on Spotlight (the small magnifying glass) in the upper right corner of your screen or pressing `cmd + space`, and typing "Terminal" then pressing enter. No further actions are required for this step

Navigating through your computer using the command line will be a vital skill. Watch the video below to get more familiar with command line commands. _You should ignore or skip any mentions of `nano`, as we will be using the much more user-friendly Atom to edit our files._

![embed](https://www.youtube.com/embed/aKRYQsKR46I)

### Quick installation test

To test whether each of our steps has been done correctly, we will write a small program named "hello". Open Atom and create a new file named `hello.py`. In this program, place the following code:

    print('Hello, world!')

Save your program in a folder that is easily accessible (we recommend you create a folder that will contain all your code from here on out) and open a terminal.

Using your terminal, navigate to the folder containing the file `hello.py`. Remember, use `cd` to change directory, `pwd` to print your current directory, and `ls` to verify that `hello.py` is in the folder you are currently in. Then, run the following command:

    python hello.py

If everything was done correctly, your command line will now show the text `Hello, world!`. Congratulations on writing and executing your first program!

### Install other Python libraries

During our courses, we will use some other Python libraries. We will download and install all these libraries through `conda` and place them in their own "environment". This makes sure that everything will work for all the exercises in the coming courses.

**At this point, it is very important to know what type of shell your computer uses. If you are using a Mac, you use either `bash`, or `zsh`. You can check by running `echo $0` in your terminal; if your computer uses `bash`, replace any future mention of `zsh` with `bash`.**

First, open a terminal and run the following command (and replace `zsh` with `bash` if needed):

    conda init zsh

This will instruct your terminal to prepare your terminal for running `conda` commands. Close the terminal, and open a new one. This will restart your terminal and makes sure that everything is initiated correctly.

To verify that the installation has worked, you can check whether your terminal shows something like `(base)` in front of every line in the terminal.

Now, with your new terminal, run the following commands:

    curl https://raw.githubusercontent.com/spcourse/sp1-python/main/en/installing/computer/environment.env > environment.yml
    conda install -n base conda-libmamba-solver
    conda env create -f environment.yml --solver libmamba
    rm environment.yml

This downloads a formatted description of what libraries to download and install, then installs the libraries, and subsequently removes the description (as we no longer need it).

From here on out when you open a terminal we can use the following command to enter the environment, and enable the use of all the libraries we installed:

    conda activate progLab

If everything worked correctly, you will now see that your terminal shows `(progLab)`.

**Important:** If you want to use all of the libraries you've just installed and `import` them in your own code, you will have to have *this* environment active. We recommend you *always* have this environment active when working on assignments.

To make sure that the environment we just installed is started _every time_ we start a new terminal, we can run some commands.

To make sure that the `progLab` environment is activated every time that we start a terminal, we can run the following command (replace `zsh` with `bash` if needed):

    echo 'conda activate progLab' >> ~/.zshrc

Now restart your terminal, and check whether it starts into the `progLab` environment. If not, please contact one of the TA's or teachers of this course.

### Checking `checkpy` and downloading tests

To help you verify whether a program functions in compliance with the specifications of an assignment, we have written a program of our own called **checkpy**. This program was installed in our environment in the previous steps. In addition to `checkpy` we also need the tests that correspond to the assignments that you'll have to make. These tests can be downloaded by executing the following command in the terminal:

    checkpy -d uva-sp/sp1

To test whether your installation of `checkpy` was successful you can test `hello.py`, which we have written earlier in these installation instructions. Navigate to the folder that holds `hello.py` and execute the following command:

    checkpy hello

Do you only see happy smileys? That means you've done a-okay, and that you've met our requirements for the assignment! Should there still be some sad smileys, no worries! Carefully examine your code and verify it with each of the specifications. And don't forget you can always send us an email if you're stuck.
