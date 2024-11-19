#  try/except Statements

Errors are sometimes inevitable when writing Python programs. Files might be missing, user input might be invalid, or unexpected issues could occur. Instead of letting your program crash, you can use `try`/`except` statements to *"gracefully"* handle errors.

## Basic Example

Here’s a simple script that handles an error when dividing 10 by a number provided through user input:

    try:
        num = int(input("Enter a number: "))
        result = 10 / num
        print(f"The result is: {result}")
    except ZeroDivisionError:
        print("Error: You cannot divide by zero!")
    except ValueError:
        print("Error: Please enter valid numbers.")

The `try` statement works as follows:

- First, the code within `try` is executed.
- If no exception occurs, the code within `except` is skipped, and execution continues after the `try` statement.
- If an exception occurs during the `try` block, execution of the  `try` block stops immediately. Then, Python checks whether the exception matches any of the except blocks.
- If the exception matches a specific `except` block, the code within that block is executed, and the program continues after the `try`/`except`.
- **Note:** only the first matching except clause is triggered.

# Generic exceptions

If you don't specify the type of error after `except`, it will catch any error. This ensures that even unexpected issues are handled gracefully. However, this should be done sparingly as it can make debugging harder.

    try:
        num = int(input("Enter a number: "))
        result = 10 / num
        print(f"The result is: {result}")
    except:
        print("An unknown error occurred.")

It's often better to use a combination of specific exceptions and a generic exception that saves the `Exception` that occurred as a variable:

  try:
      num = int(input("Enter a number: "))
      result = 10 / num
      print(f"The result is: {result}")
  except ZeroDivisionError:
      print("Error: Cannot divide by zero!")
  except ValueError:
      print("Error: Invalid input. Please enter a valid number.")
  except Exception as e:
      print(f"An unexpected error occurred: {e}")

In this case, any unexpected errors will print the `Exception` object `e` that contains details about what went wrong.

# Finally

Sometimes, you need to perform some code no matter what happens in the `try` block. Use a `finally` block for this:

    try:
        num = int(input("Enter a number: "))
        result = 10 / num
        print(f"The result is: {result}")
    except ZeroDivisionError:
        print("Error: Cannot divide by zero!")
    except ValueError:
        print("Error: Invalid input. Please enter a valid number.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")
    finally:
        print("Thanks for using our calculator!")

Which will make sure that your program will always print `"Thanks for using our calculator!"`, no matter if the code functions as intended or has an unexpected error.
