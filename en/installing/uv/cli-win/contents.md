* Auto-generated table of contents for this page
{:toc}

# Working with the command line (Windows)

Before you install anything, you need to be able to find your way around your own computer from a terminal. This page teaches you that. In the next part you will install Python and `uv`.

This guide uses **PowerShell**, the terminal that comes with Windows.

## Some background on files and folders

If you are new to programming, it is important to understand how files and folders work. All your documents are stored on your computer as a file. To help you organize a large number of files, you can use folders.

- A **file** is a document or piece of data, such as a Python program (the name will end in `.py`), but it could also literally be a data file (for example, ending in `.csv`) or a Word document (ending in `.docx`).

- A **folder** (also called a directory) is a container, and it can hold files. But a directory can also contain other directories. This means that you can organize your files in a hierarchical structure.

For example:

- `programming/` → a main folder
- `my-course/` → a folder inside `programming`
- `hello.py` → a file inside `my-course`

Adding two other files, the structure may look like this:

~~~text
programming/
└── my-course/
    ├── hello.py
    └── week1.py
    └── zac-data-2026.csv
~~~

The files that you will be mostly concerned with are **Python files**. You will often start with an empty (blank) file, write Python code, save the file and then **Run** it. But more on that later.

### Paths

A **path** is a complete description of where some file can be found, including the names of all the directories it is contained in. Instead of a file, a path can also point to a directory.

For example, you probably have been saving files in the `Documents` folder on your computer. Here are examples of the full path to a folder inside your documents directory:

~~~text
C:\Users\isaiah\Documents\UvA\intro
C:\Users\isaiah\OneDrive\Documents\UvA\intro
~~~

The second one applies if you use OneDrive. More on that below.

#### Home directory

The paths above start with `C:\Users\isaiah`. This is the path pointing to your "home directory". Your home directory is your personal space on the computer where your files live, separate from other people that might use the same computer.

#### Shortcuts

Because many of your files are in your home directory, there is a shortcut! Instead of the full path, you can use `$HOME`.

This means that you can use slightly shorter paths to the same location:

~~~text
$HOME\Documents\UvA\intro
$env:OneDrive\Documents\UvA\intro
~~~

> That last one can be used when you use OneDrive. In that case the directory `$HOME\Documents` may be empty, and instead your real `Documents` directory is inside the `OneDrive` directory. This is because OneDrive can only manage files inside the `OneDrive` directory. It is also possible that you have files in both places. That's something you should fix.

## Working with your computer from a shell

When you normally use your computer, you click on icons, open folders, and drag files. This is called a **graphical user interface (GUI)**.

A **shell** is a different way to interact with your computer. Instead of clicking, you type commands.

You access the shell through a program called a **terminal**.

### Opening the terminal

1. Press the Windows key
2. Type `PowerShell` or `Windows Terminal`
3. Press Enter

A window opens with text like this:

~~~text
PS C:\Users\YourName>
~~~

The `>` is the **prompt**. The prompt is the place where you type commands. It means the terminal is ready to take a command.

The shell also displays the path of the directory that it is attached to; in this case `C:\Users\YourName`.

### First steps in the terminal

You can try a few simple commands to look inside directories and see what files and directories are there.

Show a list of files in the current folder:

~~~powershell
dir
~~~

Move into your Documents folder:

~~~powershell
cd $HOME\Documents
~~~

"Moving into" here means attaching the shell to another directory. If you then issue `dir` again, you will get a listing of the files in *that* directory.

### Moving between folders

This is such an important concept that we elaborate on it once more. You have previously seen that you can move into a different directory by typing the command `cd` in the shell (change directory).

You will be doing this very often, especially when you start the terminal again. The shell will always load attached to your home directory. That is *not* where you will be saving your files! So you need to move into the right folder before doing anything.

For example, you might want to list the contents of a directory called `SP` which might be in the `Programming` directory in your home directory:

~~~powershell
cd $HOME\Programming\SP
dir
~~~

After a few `cd` commands it is easy to lose track of where you are. You can always ask the shell:

~~~powershell
pwd
~~~

`pwd` means "print working directory". It prints the full path of the directory your shell is attached to right now.

### How the shell relates to normal computer use

The shell lets you do the same things as clicking, but using text commands.

For example:

- open a folder → `cd foldername`
- list files → `dir`
- run a program → type its name

This guide uses the shell because programming tools like `uv` and `Python` are controlled with commands.

#### Why this matters

Programmers generally work in the terminal most of the time, because it helps them work better:

- Commands are precise and repeatable
- You can more easily automate tasks
- You can follow instructions exactly as written
- Most programming tools are designed for shell use

### Making a new folder

Apart from moving around, you will also need to create folders from the terminal. The command for that is `mkdir` ("make directory"):

~~~powershell
cd $HOME
mkdir Programming
~~~

This first moves you to your home directory, then creates a folder called `Programming` in your home directory.

Pro-tip: Use simple names **without spaces** (for example `python101`, not `Amazing Python 101 Course`). You have to type the name frequently, so shorter is better. And, directory names with spaces can be annoying to work with in the shell.

### More commands

You do not need these for the course yet, but it is good to know that they exist. Besides moving around and making folders, you can also work with the files themselves:

- `cp` — copy a file (short for `Copy-Item`)
- `mv` — move a file to another folder, or rename it (short for `Move-Item`)
- `rm` — delete a file (short for `Remove-Item`)

In PowerShell these short names are nicknames for longer commands. The nicknames are the same as the ones used on macOS and Linux, which is handy when you follow instructions written for those systems. The options they accept are different, though, so look up the PowerShell version when you need more than the basics.

Warning: `rm` deletes a file immediately. It does not go to the Recycle Bin, and there is no undo.
