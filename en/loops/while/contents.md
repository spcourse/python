# While-loops

While-loops work slightly different from for loops. On this pages we will show how while-loops work, how they differ from for-loops and when to use which type of loop.

## How to use while-loops.

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_vs6hg6ie&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_rstxzo8h)

The general format of a while-loop is:

    while [condition]:
        [repeated code]

The loop continues running as long as the condition is true. For example:

    i = 0
    while i < 6:
        print(i)
        i += 1

This loop continues running the code `print(i)` and `i += 1` as long as the condition `i < 6` is true. So this piece of code prints the numbers `1`, `2`, `3`, `4` and `5`.

In this case we could also use a for-loop to achieve the same. But this is not always the case:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_rzad8nlz&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_ku8x9gud)

In Python, just like in almost every other programming language, there are two different constructions to loop over a variable: the **for-loop** and the **while-loop**.

A for-loop is used when you know beforehand how often you want to repeat the set of instructions. In cases where you do not know the number of repetitions in advance and want to re-evaluate at every iteration whether you want to continue, you use the while-loop. In a while-loop, just like in the for-loop, all instructions are executed for a specific value of the variable. The difference is that each time the variable is changed, there is an evaluation whether or not to re-do the block again.

In most cases, you can use both `for` and `while` to achieve the same result. This while-loop:

    x = 0
    while x < 100:
        print(f"x now has the value {x}")
        x = x + 1

is equivalent to the following for-loop:

	    for x in range(100):
	        print(f"x now has the value {x}")

However, the following while-loop can not be easily written as a for-loop:

    i = 0
    total_sum = 0
    while total_sum < 100:
        i += 1
        total_sum += i

The reason that the for-loop is more often used is that it is a bit more compact and also more easily readable. However, this can only be done if you know beforehand how often the code needs to be executed. In other cases, like with user input, the only way to do it is to use a while-loop.
