# For-loops

In a computer program you often encounter a (small) set of instructions that you want to execute multiple times. The way to do and steer that is by using loops. On this page we discuss the format and features of for-loops.

## Loops to repeat instructions

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_fmqp79t8&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_blg5ympd)

A for-loop is used when you want to repeat a set of instructions. For example, if you want to print the numbers from 1 to 10 on the screen, you could do that with ten separate print-statements, but you could also use the following construction:

    for x in range(1, 11):
        print(f"x now has the value {x}")

This program has as output:

    x now has the value 1
    x now has the value 2
    x now has the value 3
    ...
    x now has the value 10

The loop starts by setting the value of `x` to `1` and then executing *all* instructions in the loop one by one. This is called an _iteration_. After that, `x` is assigned the value `2` and again all instructions are executed. In this simple program there is only a single instruction: `print` the value of `x`, but we can of course expand the number of instructions. *The most important notion is that the program changes the variable `x` _after_ each cycle.*

![](Loopsexplanation.png){: style="max-width:500px;"}

There are a few important things to note:

-   **Note:** Python counts *up to* the last number in the function range(): range(1,11) runs from 1 *up to and including* 10. This is a very common mistake to make when you begin programming in Python. It might feel unintuitive, but that's just the way it is.

-   In the above example we assigned the name 'x' to the variable, but we could of course have used a different name like 'number', 'i', 'counter' etc. You can use whatever you want.

-   With range you can also specify the step size. This is set to 1 by default, but if you prefer to take steps of 10 you would use the following syntax:

         for x in range (1, 100, 10):

    Please try this yourself to make sure you understand what values `x` takes in this program.

-   You can also loop backwards by defining the range the other way around and provide a negative stepsize:

        for i in range(10, 0, -1):
            print(i)

    This prints:

        10
        9
        8
        7
        6
        5
        4
        3
        2
        1
