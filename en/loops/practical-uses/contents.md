# Practical example with loops

Loops are one of the core building blocks for any algorithm. Let's look at a couple of typical algorithmic examples with loops.

## Computing things using loops

In the first example we only had a single instruction in the loop itself, 'print the value of `x` on the screen', but you could have multiple instructions for every value that `x` takes.

In the next example we add the value of `x` to another variable that we have set to zero at the beginning of the program. At the end of the program this variable contains the sum of the values from 1 to 10. Once we have that, it is easy to get the sum of numbers from 1 to 712643 by changing just one line.

As soon as all instructions have been executed for the highest value the variable `x` will get from the `range` function, the loop is 'finished' and the program continues with all instructions after the for-loop. In this case we have the program print the value of the sum of all numbers. Please pay close attention to the indentation/position of the last line.

    total = 0
    for x in range(1, 11):
        print(f"x now has the value {x}")
        total = total + x

    print(f"The sum of all numbers from 1 to 10 = {total}")


## Filtering using loops

Filtering with range:
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_75nvzt1x&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_sku134bf)

Within the set of instructions you can also use conditionals. For example, if you want the loop to go from 1 to 20, but only want to print the numbers that are larger than 15 or divisible by three, you could use the following code:

    for number in range(1, 20):
        if number > 15:
		   print(f"This number is bigger than 15: {number}")
        if number % 3 == 0:
		   print(f"This number is exactly divisible by 3: {number}")

We have already mentioned that you can decide on the name of the variable. And as you see, in the above example we have changed the name of our variable `x` to `number`.

## Loops in loops

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_p676hj49&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_laz26qqc)

In the examples we have looked at so far, we have only printed things and saved some variables. Nothing too complex. This is not always the case and loops are often used in more complex constructions.

It is also possible to make loops within loops, so-called 'nested loops'. If you, for example, want to vary a specific variable `y` from 1 to 3 for every value the variable `x` takes on (for example, when `x` is the student number and `y` is the mark for three different assignments during an exam) you can use the following construction:

    for x in range(1, 6):
       for y in range(1, 4):
           print(f"x = {x}, y = {y}")

This program has as output:

    x = 1,  y = 1
    x = 1,  y = 2
    x = 1,  y = 3
    x = 2,  y = 1
    ...
    x = 5,  y = 2
    x = 5,  y = 3

## Common mistakes

In this final video you can see some common mistakes when using while loops:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_m54o3nlw&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_8kxrifk5)
