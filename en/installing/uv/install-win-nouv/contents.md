* Auto-generated table of contents for this page
{:toc}

# Fallback: Python without uv (Windows)

> **This page is not part of the course material.** It is not linked from any schedule. It exists for teachers and teaching assistants to use with a student for whom the normal setup cannot be made to work. Hand out the link only when you need it.

## When to use this

Use this page as a last resort, when `uv` itself is the problem: it will not install, the download is blocked, or the `uv`-managed Python refuses to run on the student's machine.

This is the smallest possible setup: one Python, one `pip install`, nothing else. No `uv`, no virtual environment, no activation, no PowerShell profile — and therefore no execution policy problem either, which makes this page useful for a machine locked down by Group Policy as well.


## What you give up

Be aware of this before you hand out the link, and tell the student:

- **No isolation.** Packages are installed into one Python for the whole user account. Another course, another project, or a stray `pip install` can break this setup, and the only reliable repair is reinstalling Python.
- **No `(uv-sp)` prompt.** Every check in the course material that says the prompt should start with `(uv-sp)` does not apply to this student.

Plan to move the student to the normal setup when whatever blocked `uv` is resolved.

## Install Python

Download the latest Windows installer from <a href="https://www.python.org/downloads/" target="_blank" rel="noopener">python.org/downloads</a> and run it.

On the first screen of the installer, **tick "Add python.exe to PATH"** before pressing Install. This is the step people miss, and it is the cause of most of the trouble that follows.

Then **close and reopen PowerShell** and check:

~~~powershell
python --version
~~~

This should print the version you just installed.

> If instead the Microsoft Store opens, or you get a message about Python not being found, the PATH checkbox was missed. Run the installer again, choose **Modify**, and make sure the option is on. Do not install Python from the Microsoft Store.

## Install the packages for this course

~~~powershell
cd $HOME\Programming\SP
python -m pip install -r requirements.txt
~~~

Use `python -m pip` rather than `pip`. It installs into the same Python you just checked with `python --version`, which removes a whole class of confusing failures.

## Check that everything works

~~~powershell
python --version
python -c "import matplotlib; print('matplotlib works')"
Get-Command checkpy
~~~

You should see the version you installed, the message `matplotlib works`, and a path to `checkpy.exe` inside the Python `Scripts` folder.

> If `checkpy` is not found but the install reported success, the `Scripts` folder is not on the PATH. It sits next to `python.exe`; the installer normally adds it along with the PATH checkbox above.

## Working on the course

1. Open PowerShell.
2. `cd $HOME\Programming\SP\module1`
3. `python hello.py`

There is nothing to activate.
