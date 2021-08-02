# Practice answers

Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.

You should not have to rely on the answers to the practice exercise too much. If you cannot make the practice exercises at all without relying on these answers, you should discuss this with your teacher.

**Exercise 1**

    my_dict = {"Ralph": 4, "Diana": 8, "Jordi": 7, "Michele": 5}
    print(my_dict)

**Exercise 2**

    my_dict = {"Ralph": 4, "Diana": 8, "Jordi": 7, "Michele": 5}
    my_dict["Gretel"] = 9
    print(my_dict)

**Exercise 3**

    my_dict = {"Ralph": 4, "Diana": 8, "Jordi": 7, "Michele": 5}
    my_dict["Gretel"] = 9

    name = ""
    while name == "":
    name = input("Please enter a name: ")

    if name in my_dict:
    grade = my_dict[name]
    print(f"{name} is a student in this class, and has the grade: {grade}.")
    else:
    print(f"{name} is not a student in this class.")
