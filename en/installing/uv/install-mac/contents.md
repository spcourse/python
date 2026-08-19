---
layout: welkom-tutorial
title: Python setup with uv (macOS and Linux)
tutorial_questions:
  setup:
    question: "What did your course provide?"
    description: "If you don't know what we're asking, check the course page or ask your teacher."
    choices:
      nothing: "Nothing (no config file)"
      requirements: "A requirements.txt file"
      pyproject: "A pyproject.toml file"
---

* Auto-generated table of contents for this page
{:toc}

# Python setup with `uv` (macOS and Linux)

This guide shows how to:

- install `uv` and a recent Python version
- create a programming folder and subfolders for your courses
- manage Python packages required for each course
- how to run your Python programs

There are other ways to manage Python! But in this tutorial, we try to provide a consistent experience that is useful in a university setting.

> This guide assumes you can already open a terminal and move between folders with `cd`. If that is new to you, first work through the command line tutorial.

This guide covers macOS and Linux. The two are almost identical for our purposes; where they differ, you will find a remark.

## Installing uv and Python

`uv` is a Python package and environment manager. It replaces several older tools you may see in other guides, such as:

- `pip` (for installing packages)
- `venv` (for creating virtual environments)
- separate Python installers

Instead of learning multiple tools, you use **one tool (uv) for everything**. This has advantages, but also disadvantages. For now it keeps learning simple, and you can expand your knowledge later.

### Install uv now

Open a terminal and run the following command:

~~~bash
curl -LsSf https://astral.sh/uv/install.sh | sh
~~~

After installation, close and reopen your terminal.

Check that it works:

~~~bash
uv --version
~~~

There could be errors! In that case ask your teacher.

### Install a Python version with `uv`

The first step when using `uv` is to install Python itself. You will need a recent version of Python, and `uv` makes it very easy to get that.

For example, to install Python 3.14:

~~~bash
uv python install 3.14
~~~

You can check which Python versions are available on your system with:

~~~bash
uv python list
~~~

Sometimes this will list a few older versions, as well. That is fine: in a later step, you will configure to use Python 3.14 during your course work.

## Creating folders for all your courses

You will now need to decide where your course files are going to be saved on your computer. Probably you have already created a place for university work, for example in your `Documents` directory. You may or may not have organized it, for example by making a folder for each separate course.

Your first task is to create a directory where all your **programming-related course** files are going to be. This is not necessarily the same directory as where other university work is stored. You will have multiple programming courses, and maybe a few projects, so it's good to make a dedicated directory for that.

> In the next section, we will suggest the best options. It's fine if you make a different decision. However, do **not** save your work in Downloads, on the Desktop, or inside other "easy to access" folders. Such directories are not backed up, which will be very sad when your computer crashes and you lose all of it.

### Installing Nextcloud

Ideally, your work is automatically backed up. Unfortunately, saving Python projects in iCloud is a bit of a problem. Hence, you will install Nextcloud, as provided by the University of Amsterdam. It will take care of automatic backup.

1. Install <a href="https://nextcloud.com/install/#desktop-files" target="_blank" rel="noopener">Nextcloud</a>, a tiny program that synchronizes files from your computer to the cloud (only files in a specific directory).

2. When asked, press **Login** and enter the SurfDrive address:

        https://surfdrive.surf.nl

3. Login using your UvA credentials.

4. You will now have a folder called `Nextcloud`.

5. Go to the Nextcloud settings using the **...** button:

    ![](dotdotdot.png)

6. Choose **Edit ignored files**:

    ![](dotmenu.png)

7. Add `.venv` (don't forget the dot!) and check the **Allow deletion** marker:

    ![](ignorevenv.png)

### Good locations for your work

Choosing the right location matters because you do not want to lose your work and you want it to be easy to find.

> **Do not save your Python work on iCloud.** You should have installed Nextcloud in the previous step.

Put a `Programming` folder inside your `Nextcloud` folder:

- example: `~/Nextcloud/Programming`

### Creating a subfolder for one course or project

Let's say that you are using `~/Nextcloud/Programming` as your programming folder. Now it's time to create a course-specific subfolder.

`mkdir` means "make directory" (create a folder).

~~~bash
mkdir -p ~/Nextcloud/Programming/my-course
cd ~/Nextcloud/Programming/my-course
~~~

Replace `my-course` with the actual name of your course.

Use simple names without spaces (for example: `python101`, not `python 101`). If you do use spaces, working with that directory becomes very annoying in the shell.

Good examples:

- `python101`
- `intro-programming`
- `datascience-course`

## Create a virtual environment for the course

Now that you have a directory for the course, you should make a virtual environment inside it. A **virtual environment** contains a Python setup just for this course or project.

Why this matters:

- it keeps packages for this course separate from other courses
- it avoids conflicts between different projects
- it makes it easier to reproduce the same setup later

We distinguish a few options:

1. Your teacher may not provide any configuration. In that case, you make an "empty" virtual environment for the course and you can install any packages you need.

2. Your teacher provides a `requirements.txt` file with a list of packages that are needed (often along with some other required files).

3. Your teacher provides a `pyproject.toml`, again with a list of packages that are needed. This works a little bit differently.

In the next sections we provide instructions for each of these cases.

### Installing an empty virtual environment [nothing]

> Follow these instructions only if you have no `requirements.txt` and no `pyproject.toml` from the course! If you have either of those, skip to the next steps.

From **inside** the course folder, run:

~~~bash
uv venv --python 3.14
~~~

Here, we have added the option `--python 3.14` to specify the version that we just installed. This is useful in case there are multiple Python versions on your computer (and there probably are).

The command creates a `.venv` folder in the course directory. Although it's important to keep it, no need to look at it: the `.venv` folder is managed automatically by `uv`. Therefore:

- do not edit files inside it manually
- do not rename or move it
- do not delete it unless you want to recreate the environment

### Installing with `requirements.txt` [requirements]

From **inside** the course folder, run:

~~~bash
uv venv --python 3.14
~~~

Here, we have added the option `--python 3.14` to specify the version that we just installed. This is useful in case there are multiple Python versions on your computer (and there probably are).

Then run:

~~~bash
uv pip install -r requirements.txt
~~~

This will read the requirements file and install all packages that are mentioned in it.

Note that you now have a `.venv` folder in the course directory. Although it's important to keep it, no need to look at it: the `.venv` folder is managed automatically by `uv`. Therefore:

- do not edit files inside it manually
- do not rename or move it
- do not delete it unless you want to recreate the environment

### Installing with `pyproject.toml` [pyproject]

You may have received a `zip` file for the course or just a single `pyproject.toml`. This file contains a list of the required packages. It can be used to automatically create a virtual environment.

Make sure that you have extracted the files from the zip into an appropriate course folder, or you have placed the downloaded `pyproject.toml`. Then it's just two steps:

~~~bash
cd ~/Nextcloud/Programming/course-with-project
uv sync
~~~

The `sync` command will create the virtual environment for you, and install additional packages.

Note that you now have a `.venv` folder in the course directory. Although it must be there, no need to look at it: the `.venv` folder is managed automatically by `uv`. Therefore:

- do not edit files inside it manually
- do not rename or move it
- do not delete it unless you want to recreate the environment

### Before you continue: confirm that the environment exists

After setting up the virtual environment, you should now have a folder structure like this:

~~~text
programming/
└── my-course/
    └── .venv/
~~~

Later, your Python files can also live in `my-course`, for example:

~~~text
programming/
└── my-course/
    ├── .venv/
    ├── hello.py
    └── week1.py
~~~

## Running Python programs

Now that everything is installed, you can get into the routine of running your self-written Python programs.

#### Once again: work from inside the course folder

Each time you work on a course, you connect your shell to the course directory (folder). Only then will it pick up on the packages you installed.

So when working on the course you always start with:

1. open a terminal
2. go to your course folder (`cd`)
3. if needed, go to a subfolder
4. run commands from there

And recall, to go to your course folder, use:

~~~bash
cd ~/Nextcloud/Programming/my-course
~~~

## Run commands with `uv run`

When you are inside the course folder, use `uv run` to execute Python and tools.

> This means you do **not** need to activate the virtual environment manually. We mention this because some students may have some experience in using virtual environments. Generally, these have been "activated" for use in the shell. But with `uv run`, we can avoid that for now. Try it!

`uv run` makes sure that:

- the correct Python version for this course is used
- the packages installed in this course's environment are used
- you do not accidentally use system-wide (global) Python or packages

So that's why you always use the following workflow:

- go to the course folder
- if needed, go to a subfolder that's inside the course folder
- run commands with `uv run`

Example pattern:

~~~bash
uv run <command>
~~~

Normally this would be a Python program that you wrote, like:

~~~bash
uv run hello.py
~~~

That's all! You can use `uv run` every time to run your programs.

## Adding packages to your course environment

A **package** is a collection of Python code written by other people that you can reuse in your own programs.

Instead of writing everything from scratch, you install packages that solve common problems.

Here are some widely used packages you may encounter:

- `requests` – used to download data from the internet (e.g. calling APIs)
- `numpy` – fast numerical computing (arrays, math operations)
- `pandas` – working with tables of data (like spreadsheets)
- `matplotlib` – creating graphs and visualizations
- `rich` – nicer formatting and colors in terminal output

You only install the packages you need for your course.

### Global vs local packages

There are two ways to install Python packages:

- **Global install**: packages are installed once and shared across your whole computer
- **Local install (virtual environment)**: packages are installed only for one course or project

Why global installs are a problem:

- different courses may need different versions of the same package
- installing or upgrading a package can break other projects

Why local installs are better:

- each course has its own setup
- no conflicts between projects
- easier to manage and debug

In this guide, you always install packages **locally inside the course folder**.

### Installing packages into the virtual environment

When you need extra packages for the course, install them from **inside the course folder**.

Example:

~~~bash
cd ~/Nextcloud/Programming/my-course
uv pip install requests
~~~

This adds the package to the environment for that course.

You can add more than one package:

~~~bash
uv pip install numpy pandas matplotlib
~~~

#### Adding packages from requirements [requirements]

In case your teacher provided a `requirements.txt` they already had some packages in mind that you need. Run this command once to install the packages into your environment:

~~~bash
cd ~/Nextcloud/Programming/my-course
uv pip install -r requirements.txt
~~~

#### Adding packages to a project [pyproject]

If your course works with a `pyproject.toml` you need to add your package to the project using another command:

~~~bash
cd ~/Nextcloud/Programming/my-course
uv add rich
~~~

To understand projects with `pyproject.toml` better, read the [Projects guide](https://docs.astral.sh/uv/guides/projects/) on the **uv** website.

## Recommended workflow

For each new course:

- create a new course subfolder inside `~/Nextcloud/Programming`
- go into that subfolder and create a virtual environment with `uv venv`
- keep your course files there
- use `uv run` from inside that folder
- add packages with `uv pip install ...` when needed

### Example from start to finish

~~~bash
mkdir -p ~/Nextcloud/Programming/python101
cd ~/Nextcloud/Programming/python101
uv venv --python 3.14
uv pip install requests
uv run python
~~~

### Common mistakes to avoid

Do not:

- create projects in Downloads or other temporary folders
- install all packages globally
- mix multiple courses in one folder
- forget to move into the course folder before running commands

## Check your installation

Not sure whether everything above actually worked? Paste the command below into your terminal. It checks that `uv` is installed, that it can run a recent enough Python version, and that your `Nextcloud` folder is set up correctly (including the `.venv` exclusion).

~~~bash
curl -LsSf https://www.proglab.nl/welkom/install/uv/check.sh | bash
~~~

If anything is reported as failed or a warning, fix it and run the command again.

This is the end of the tutorial. If you have any questions, do not hesitate to talk to other students, to your teaching assistant, the teacher, or the helpdesk.
