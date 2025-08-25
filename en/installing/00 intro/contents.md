# Python on your own computer

To be able to program on your own computer you will need a couple different programs:

1. **Miniconda**, a version of Python that is easy to install.

2. **Pulsar**, an *editor* to write code in. This is, in a way, just a text writing program, but specifically meant for programming code. For example, it highlights particular parts of your code in specific colors, so you can more easily distinguish which part of your code does what.

3. A *command line interface* from which we will provide you with methods to start and interact with your programs. macOS comes with one!

Stuck during any part of the process? Consult one of the teachers or a teaching assistant!

## FAQ

**Can I use a different editor?**

Yes, you are allowed to use a different editor or an IDE. _However, this is not recommended if you have limited experience programming or setting up environments._ Our staff will/can not help you if you have installation problems that are caused by your choice of editor, and we expect you to be able to solve any issues yourself.

There are also some known issues with Jupyter Notebooks and IDE's that display these internally, such as Visual Studio Code. We recommend you to always run a local Jupyter Notebook server and edit your notebooks through your favorite browser.

**What if I have already installed Anaconda?**

Make sure to update `conda` to the most recent version before installing our environment. After updating, proceed with installing the environment. If so desired, you can skip the steps that activate our environment by default, but you will need to make sure you activate it every time you start a Jupyter server.

If you are unsure of how any of this works (or what we are even talking about here), we recommend you to uninstall conda, and then to follow the instructions on our webpages for installation.

**What if I've already done the installation for Scientific Programming?**

You should already have an editor and Anaconda installed and can skip steps 1, 2 and 3. There should be differences/additions in the installed environment, so you should still do steps 4 and 5.

If you have multiple environments installed, it is possible to switch between environments by using the following command in the terminal:

    conda activate <name_of_environment>
