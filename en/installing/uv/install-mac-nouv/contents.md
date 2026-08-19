* Auto-generated table of contents for this page
{:toc}

# Fallback: Python without uv (macOS)

> **This page is not part of the course material.** It is not linked from any schedule. It exists for teachers and teaching assistants to use with a student for whom the normal setup cannot be made to work. Hand out the link only when you need it.

## When to use this

Use this page as a last resort, when `uv` itself is the problem: it will not install, the download is blocked, or the `uv`-managed Python refuses to run on the student's machine.

This is the smallest possible setup: one Python, one `pip install`, nothing else. No `uv`, no virtual environment, no activation, no startup file.

## What you give up

Be aware of this before you hand out the link, and tell the student:

- **No isolation.** Packages are installed into one Python for the whole user account. Another course, another project, or a stray `pip install` can break this setup, and the only reliable repair is reinstalling Python.
- **No `(uv-sp)` prompt.** Every check in the course material that says the prompt should start with `(uv-sp)` does not apply to this student.
- **The command is `python3`, not `python`,** unless you add the alias below.

Plan to move the student to the normal setup when whatever blocked `uv` is resolved.

## Install Python

Download the latest macOS installer from <a href="https://www.python.org/downloads/" target="_blank" rel="noopener">python.org/downloads</a> and run it. Accept the defaults.

Then **close and reopen Terminal** and check:

~~~bash
python3 --version
~~~

This should print the version you just installed.

> Use the installer from python.org, not Homebrew. A Homebrew Python refuses plain `pip install` (it reports an "externally managed environment"), which is exactly the thing this page is trying to avoid.

## Install the packages for this course

~~~bash
cd ~/Programming/SP
python3 -m pip install -r requirements.txt
~~~

Use `python3 -m pip` rather than `pip3`. It installs into the same Python you just checked with `python3 --version`, which removes a whole class of confusing failures.

> If this fails with a permission error, retry with `python3 -m pip install --user -r requirements.txt`. Be aware that `--user` puts `checkpy` in `~/Library/Python/3.x/bin`, which is not on the PATH by default, so you will have to add it before `checkpy` can be found.

## Optional: make `python` work

The course material says `python`, but the python.org installer only gives you `python3`. To make the course instructions read correctly:

~~~bash
echo 'alias python=python3' >> ~/.zshrc
~~~

Close and reopen Terminal. This affects what the student types in the terminal; it does not change anything for programs run by other tools.

## Check that everything works

~~~bash
python3 --version
python3 -c "import matplotlib; print('matplotlib works')"
which checkpy
~~~

You should see the version you installed, the message `matplotlib works`, and a path to `checkpy`.

## Working on the course

1. Open Terminal.
2. `cd ~/Programming/SP/module1`
3. `python3 hello.py` (or `python hello.py` if you added the alias)

There is nothing to activate.
