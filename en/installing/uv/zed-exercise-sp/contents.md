* Auto-generated table of contents for this page
{:toc}

# Exercise: your first files in Zed

In this exercise you open your course folder in Zed, make two files in it, and look at them from the terminal. It is the first time you use the editor and the terminal together, which is how you will work for the rest of the course.

This exercise is the same on macOS, Linux and Windows. Only the way you write a path differs:

- macOS and Linux: `~/Programming/SP/module1`
- Windows: `$HOME\Programming\SP\module1`

## Part 1: open your project and make a file

Open Zed. Choose *Open* and select your `Programming` **folder** (so, not a specific file in that folder, but the whole `Programming` folder). Zed now treats it as your project, and the sidebar on the left shows everything inside it.

Working with one folder open like this is normal for programmers. You see all your course files at once, and you can jump between them without going through Finder or Explorer.

In the sidebar, open `SP` and then `module1`. Do right-click on `module1` and choose *New File*. Name it `test.txt` and type this as its content:

~~~text
Hello, Zed!
~~~

Save the file.

Now switch to your terminal. Navigate to the `module1` folder, and list its contents to confirm that `test.txt` is really there. You learned both of these commands earlier.

Then look at what is inside the file directly from the terminal (without opening it in the editor). You can use `cat` to print the contents of the file to your terminal:

~~~bash
cat test.txt
~~~

You should see `Hello, Zed!`.

> `cat` prints the contents of a file to your terminal. It works on all three operating systems, and it is a fast way to check a file without opening an editor.

## Part 2: your first program

Still in `module1`, create a second file in Zed, called `hi.py`. The `.py` at the end tells everyone (you, Zed and Python) that this is a Python program.

Put exactly this in it:

~~~python
print("Hi!")
~~~

Save the file. You created your first Python program! 

Let's try running it. Back in the terminal, make sure you are still in `module1` and that your prompt starts with `(uv-sp)`. Then run your program:

~~~bash
python hi.py
~~~

The terminal should answer:

~~~text
Hi!
~~~

This is the typical workflow to write and run a Python script.

## If something does not work

- `cat: no such file` or `ls` does not show `test.txt`: your terminal is probably not in the `module1` directory. Check where you are with `pwd`.
- `python: command not found`: your environment might not be active. Your prompt should start with `(uv-sp)`.
- Nothing happens when you run `hi.py`: check that you saved the file in Zed.
