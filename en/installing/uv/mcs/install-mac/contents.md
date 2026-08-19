# Installing Python and uv (macOS and Linux)

* Auto-generated table of contents for this page
{:toc}

On this page you install Python and `uv` on your own computer, and set up the environment you will use for this course. Work through it from top to bottom.

This guide covers macOS and Linux. The two are almost identical for our purposes; where they differ, you will find a remark.

`uv` is a Python package and environment manager. It replaces several older tools you may see in other guides, such as:

- `pip` (for installing packages)
- `venv` (for creating virtual environments)
- separate Python installers

## Installing uv

Open a terminal and run:

~~~bash
curl -LsSf https://astral.sh/uv/install.sh | sh
~~~

After installation, **close and reopen your terminal**. Then check that it works:

~~~bash
uv --version
~~~

This should print a version number. There could be errors! In that case ask your teacher.

## Installing Python

`uv` does not only manage packages, it can also install Python itself. You need a recent version:

~~~bash
uv python install 3.14
~~~

You can check which Python versions are available on your system with:

~~~bash
uv python list
~~~

Sometimes this lists a few older versions as well. That is fine. In the next step you specify which one this course uses.

## Creating the environment

A **virtual environment** is a Python setup that belongs to one course or project, instead of to your whole computer. It keeps the packages for this course separate, so that installing something here cannot break something else.

For this course you create one environment called `uv-sp`:

~~~bash
mkdir -p ~/.venvs
uv venv --seed --python 3.14 ~/.venvs/uv-sp
~~~

Explaining the commands:

- `mkdir -p ~/.venvs` creates the directory where environments can be stored
- `uv venv` creates the virtual environment
- `--seed` makes sure `pip` is available inside it
- `--python 3.14` specifies which version of Python to use
- `~/.venvs/uv-sp` is the location where the environment is stored

When you type `ls` you cannot see the `.venvs` directory (the `.` makes it hidden), but you can see it with `ls -a`. That said, you do not need to look inside `~/.venvs/uv-sp`. It is managed by `uv`. Do not edit, rename or move it.

## Activating the environment

Before you can use the environment, it has to be **activated**. Activating means: for this terminal window, `python` refers to the Python of `uv-sp`, and to the packages installed in it.

You can do that by typing (after opening a terminal):

~~~bash
source ~/.venvs/uv-sp/bin/activate
~~~

Your prompt should now start with `(uv-sp)`:

~~~text
(uv-sp) username@macbook ~ %
~~~

That prefix is how you can always tell the environment is active.

Note that you need to type this command *every time you open a terminal*.

### Automating activation (very optional!)

You can configure your shell to automatically activate the environment every time you open a terminal. **This part is very optional**, and only recommended if you do not use Python for other projects at this moment.

First, find out which shell you use:

~~~bash
echo $SHELL
~~~

If the answer ends in `zsh` (the default on macOS), run:

~~~bash
echo 'source ~/.venvs/uv-sp/bin/activate' >> ~/.zshrc
~~~

If the answer ends in `bash` (common on Linux), run:

~~~bash
echo 'source ~/.venvs/uv-sp/bin/activate' >> ~/.bashrc
~~~

This adds one line to your shell's startup file, which is read every time you open a terminal.

Now **close and reopen your terminal**. Your prompt should now start with `(uv-sp)`.

## Installing the packages for this course

Download the `requirements.txt` file here: [requirements.txt](../downloads/requirements.txt)

This file lists the packages you need for this course. Save it in your course folder, so that you have `~/Programming/MCS/requirements.txt`.

Make sure you still have the uv environment activated (`(uv-sp)` in your prompt). Then install everything it lists:

~~~bash
cd ~/Programming/MCS
uv pip install -r requirements.txt
checkpy -d spcourse/tests
~~~

## Check that everything works

With `(uv-sp)` in your prompt, run:

~~~bash
python --version
python -c "import matplotlib; print('matplotlib works')"
which checkpy
~~~

You should see:
- version 3.14,
- the message `matplotlib works`, 
- and a path ending in `uv-sp/bin/checkpy`.

## Working on the course from now on

Every time you work on the course:

1. Open a terminal. 
2. Run `source ~/.venvs/uv-sp/bin/activate` (if needed).
3. Go to the folder you are working in, for example `cd ~/Programming/MCS/module1`.
4. Run your program with `python`, for example `python hello.py`.

That's it. If you have any questions, do not hesitate to talk to the teachers or other students.

## Final step: install Zed

You now know how to use the terminal, and you have installed uv/Python. But now we still need an editor for writing code. For this course we will use Zed, a lightweight editor that is relatively easy to use.

Go to the [Zed download page](https://zed.dev/download) and download Zed for **macOS (Apple Silicon)**.

Almost every Mac sold since 2021 has an Apple Silicon chip (M1, M2, M3, M4, ...). Only if your Mac is from 2020 or earlier could it still have an Intel processor. In that case you need the Intel download instead.

If you are not sure, ask your terminal:

~~~bash
uname -m
~~~

`arm64` means Apple Silicon. `x86_64` means Intel.

> On Linux, use the install command shown on the Zed download page instead.

Use the installer to install Zed on your computer.
