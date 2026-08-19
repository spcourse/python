# Fallback: Windows without script execution

* Auto-generated table of contents for this page
{:toc}

> **This page is not part of the course material.** It is not linked from any schedule. It exists for teachers and teaching assistants to use with a student whose laptop will not allow the normal setup. Hand out the link only when you need it.

## When to use this

Use this page when a student runs

~~~powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
~~~

and gets an error saying the execution policy is controlled by a Group Policy.

That happens on machines managed by an organisation. Group Policy sits above every setting the student can change, so neither `Set-ExecutionPolicy` nor the `-ExecutionPolicy Bypass` command line option will help. No PowerShell script will run on that machine, which rules out both `Activate.ps1` and the PowerShell profile.

Everything on this page avoids scripts entirely, so the execution policy never applies.

## Setting up

Installing `uv` and Python works normally. `uv` is a program, not a script, so it was never blocked:

~~~powershell
uv python install 3.14
mkdir -Force $HOME\.venvs
uv venv --seed --python 3.14 $HOME\.venvs\uv-sp
~~~

Skip the execution policy step and the profile step from the normal instructions.

## Activating, every session

Instead of running `Activate.ps1`, the student sets the two variables that activation would have set. These are ordinary commands, not a script:

~~~powershell
$env:VIRTUAL_ENV = "$HOME\.venvs\uv-sp"
$env:PATH = "$env:VIRTUAL_ENV\Scripts;$env:PATH"
~~~

After that, `python`, `pip`, `jupyter` and `checkpy` all resolve to the environment, exactly as they would after normal activation.

The rest of the course instructions apply unchanged:

~~~powershell
cd $HOME\Programming\SP
uv pip install -r requirements.txt
~~~

## What is different for the student

- **The prompt does not show `(uv-sp)`.** Every check in the course material that says "your prompt should start with `(uv-sp)`" will fail for this student. Tell them so explicitly, or they will think the setup is broken. To verify instead, use:

    ~~~powershell
    Get-Command python
    ~~~

    The path should be inside `.venvs\uv-sp`.

- **There is no `deactivate`.** Closing the PowerShell window is how you undo it.

- **It has to be redone in every new window.** This is the real cost. The two lines cannot be automated into the profile, because the profile is itself a script. Options: have the student keep the two lines in a text file to paste, or pin them somewhere they can copy from quickly.

## Better long-term fixes

Both of these are worth pursuing rather than leaving a student pasting two lines all semester:

- Have the machine's administrator set the execution policy to `RemoteSigned`, after which the normal instructions work.
- If the laptop is the student's own but was configured by a previous owner or an old organisation, the policy may be removable through Windows settings. This needs a case-by-case look.
