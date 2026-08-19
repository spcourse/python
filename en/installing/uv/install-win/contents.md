* Auto-generated table of contents for this page
{:toc}

# Installing Python and uv (Windows)

On this page you install Python and `uv` on your own computer, and set up the environment you will use for this course. Work through it from top to bottom.

This guide uses **PowerShell**, the terminal that comes with Windows.

`uv` is a Python package and environment manager. It replaces several older tools you may see in other guides, such as:

- `pip` (for installing packages)
- `venv` (for creating virtual environments)
- separate Python installers

## Installing uv

Open PowerShell and run:

~~~powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
~~~

After installation, **close and reopen PowerShell**. Then check that it works:

~~~powershell
uv --version
~~~

This should print a version number. There could be errors! In that case ask your teacher.

## Installing Python

`uv` does not only manage packages, it can also install Python itself. You need a recent version:

~~~powershell
uv python install 3.14
~~~

You can check which Python versions are available on your system with:

~~~powershell
uv python list
~~~

Sometimes this lists a few older versions as well. That is fine. In the next step you specify which one this course uses.

## Allowing PowerShell to run scripts

By default, Windows refuses to run PowerShell scripts. Activating your environment is done by such a script, so you have to change this setting once.

~~~powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
~~~

Confirm with `Y` when it asks.

This only applies to your own account and does not need administrator rights. `RemoteSigned` means: scripts you have on your own computer may run, scripts downloaded from the internet may not (unless they are signed).

> If this command gives an error saying the setting is controlled by a policy, your computer is managed by an organisation and you cannot change it yourself. Ask your teacher; there is another way to do this.

## Creating the environment

A **virtual environment** is a Python setup that belongs to one course or project, instead of to your whole computer. It keeps the packages for this course separate, so that installing something here cannot break something else.

For this course you create one environment called `uv-sp`:

~~~powershell
mkdir -Force $HOME\.venvs
uv venv --seed --python 3.14 $HOME\.venvs\uv-sp
~~~

Explaining the commands:

- `mkdir -Force $HOME\.venvs` creates the directory where environments can be stored
- `uv venv` creates the virtual environment
- `--seed` makes sure `pip` is available inside it
- `--python 3.14` specifies which version of Python to use
- `$HOME\.venvs\uv-sp` is the location where the environment is stored

The `.` at the start of `.venvs` is a convention from macOS and Linux, where it makes a folder hidden. On Windows the folder is simply visible. Either way, you do not need to look inside `$HOME\.venvs\uv-sp`. It is managed by `uv`. Do not edit, rename or move it.

## Activating the environment

Before you can use the environment, it has to be **activated**. Activating means: for this PowerShell window, `python` refers to the Python of `uv-sp`, and to the packages installed in it.

You can do that by typing (after opening PowerShell):

~~~powershell
& $HOME\.venvs\uv-sp\Scripts\Activate.ps1
~~~

Your prompt should now start with `(uv-sp)`:

~~~text
(uv-sp) PS C:\Users\YourName>
~~~

That prefix is how you can always tell the environment is active.

Note that you need to type this command *every time you open PowerShell*.

### Automating activation (very optional!)

You can configure PowerShell to automatically activate the environment every time you open it. **This part is very optional**, and only recommended if you do not use Python for other projects at this moment.

PowerShell reads a file called your **profile** every time it starts. Run these two commands:

~~~powershell
if (!(Test-Path $PROFILE)) { New-Item -Path $PROFILE -ItemType File -Force }
Add-Content -Path $PROFILE -Value '& "$HOME\.venvs\uv-sp\Scripts\Activate.ps1"'
~~~

The first line creates the profile file if you do not have one yet. The second adds the activation line to it.

Now **close and reopen PowerShell**. Your prompt should now start with `(uv-sp)`.

## Installing the packages for this course

Download the `requirements.txt` file here: [requirements.txt](../downloads/requirements.txt)

This file lists the packages you need for this course. Save it in your course folder, so that you have `$HOME\Programming\SP\requirements.txt`.

Make sure you still have the uv environment activated (`(uv-sp)` in your prompt). Then install everything it lists:

~~~powershell
cd $HOME\Programming\SP
uv pip install -r requirements.txt
checkpy -d spcourse/tests
~~~

## Check that everything works

With `(uv-sp)` in your prompt, run:

~~~powershell
python --version
python -c "import matplotlib; print('matplotlib works')"
Get-Command checkpy
~~~

You should see:
- version 3.14,
- the message `matplotlib works`,
- and a path ending in `uv-sp\Scripts\checkpy.exe`.

## Working on the course from now on

Every time you work on the course:

1. Open PowerShell.
2. Run `& $HOME\.venvs\uv-sp\Scripts\Activate.ps1` (if needed).
3. Go to the folder you are working in, for example `cd $HOME\Programming\SP\module1`.
4. Run your program with `python`, for example `python hello.py`.

That's it. If you have any questions, do not hesitate to talk to the teachers or other students.

## Final step: install Zed

You now know how to use the terminal, and you have installed uv/Python. But now we still need an editor for writing code. For this course we will use Zed, a lightweight editor that is relatively easy to use.

Go to the [Zed download page](https://zed.dev/download) and download Zed for **Windows (Intel/AMD)**.

The page also offers an **ARM64** version. That is almost certainly *not* the one you want: Windows laptops with an ARM processor are still very rare. Only pick it if you know for sure that you have one.

If you are not sure, ask PowerShell:

~~~powershell
$env:PROCESSOR_ARCHITECTURE
~~~

`AMD64` means a normal Intel or AMD processor, so use the Intel/AMD download. `ARM64` means you have an ARM processor.

Use the installer to install Zed on your computer.
