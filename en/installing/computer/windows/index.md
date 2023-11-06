# Python on your own computer

To be able to program on your own computer you will need a couple different programs:

1. **Miniconda**, a version of Python that is easy to install.

2. **Pulsar**, an *editor* to write code in. This is, in a way, just a text writing program, but specifically meant for programming code. For example, it highlights particular parts of your code in specific colors, so you can more easily distinguish which part of your code does what.

3. A *command line interface* from which we will provide you with methods to start and interact with your programs. macOS comes with one!

Stuck during any part of the process? Consult one of the teachers or a teaching assistant!

### Step 1: Miniconda

This package can be downloaded from the [Anaconda website](https://docs.conda.io/en/latest/miniconda.html). [The Windows 64-bit version can be found here.](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe)

As soon as the download is finished execute the downloaded file. Follow the installation instructions and choose to install for "Just Me" where you can.

**Tick all four boxes in the "advanced installation options"! Especially the "Add Miniconda3 to my PATH environment variable" is important. If you did not tick this box, you have to reinstall Miniconda!** Keep in mind that this menu can look slightly different for everyone.

![Tick the box: "Add to PATH" when installing Miniconda](../anaconda_vinkje.gif)

The installation might take a while.

![](../wait2.gif){:style="max-width:25%"}

### Step 2: Pulsar

This program can be downloaded from the [Pulsar website](https://pulsar-edit.dev/download.html#regular-releases). Select your operating system and download the installer. Once again you will have to execute the downloaded file. This time though, you do not have to alter any settings during the installation process.

### Step 3: Command Line Interface

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

### Install other Python libraries

During our courses, we will use some other Python libraries. We will download and install all these libraries through `conda` and place them in their own "environment". This makes sure that everything will work for all the exercises in the coming courses.

First, open a terminal and run the following command:

    conda init bash

This will instruct your terminal to prepare your terminal for running `conda` commands. **Close the terminal, and open a new one.** This will restart your terminal and makes sure that everything is initiated correctly.

To verify that the installation has worked, you can check whether your terminal shows something like `(base)` in front of every line in the terminal.

Now, with your new terminal, run the commands below. (**Don't copy all four lines at once into your terminal, but enter them one line at a time.**)

    curl https://raw.githubusercontent.com/spcourse/sp1-python/main/en/installing/computer/environment.env > environment.yml
    conda install -n base conda-libmamba-solver
    conda config --set solver libmamba
    conda env create -f environment.yml
    rm environment.yml

This downloads a formatted description of what libraries to download and install, then installs the libraries, and subsequently removes the description (as we no longer need it).

From here on out when you open a terminal we can use the following command to enter the environment, and enable the use of all the libraries we installed:

    conda activate progLab  

If everything worked correctly, you will now see that your terminal shows `(progLab)`.

**Important:** If you want to use all of the libraries you've just installed and `import` them in your own code, you will have to have *this* environment active. We recommend you *always* have this environment active when working on assignments.

To make sure that the environment we just installed is started _every time_ we start a new terminal, we can run some commands.

To make sure that the `progLab` environment is activated every time that we start a terminal, we can run the following command:

    echo 'conda activate progLab' >> ~/.bash_profile

We now need to perform two more commands, that will ensure that Python and sqlite function as intended on Windows:

    echo "alias python='winpty python'" >> ~/.bash_profile
    echo "alias sqlite3='winpty sqlite3'" >> ~/.bash_profile
    echo "alias checkpy='winpty checkpy'" >> ~/.bash_profile


Now restart your terminal, and check whether it starts into the `progLab` environment. If not, please contact one of the TA's or teachers of this course.

### Checking `checkpy` and downloading tests

To help you verify whether a program functions in compliance with the specifications of an assignment, we have written a program of our own called **checkpy**. This program was installed in our environment in the previous steps. In addition to `checkpy` we also need the tests that correspond to the assignments that you'll have to make. These tests can be downloaded by executing the following command in the terminal:

    checkpy -d spcourse/tests

To test whether your installation of `checkpy` was successful you can test `hello.py`, which we have written earlier in these installation instructions. Navigate to the folder that holds `hello.py` and execute the following command:

    checkpy hello

Do you only see happy smileys? That means you've done a-okay, and that you've met our requirements for the assignment! Should there still be some sad smileys, no worries! Carefully examine your code and verify it with each of the specifications. And don't forget you can always send us an email if you're stuck.
