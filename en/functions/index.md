# Functions

## Video: functions
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_5l6vbblu&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_clhk47gk)

## Video: functions with multiple parameters
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_03dms4u5&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_uhohnubo)

## Reference
A *function* is a piece of code that is assigned a name, so you can reuse it multiple times throughout your code. A function you've used before for instance is `len()`, to calculate the length of a list. But also think of functions such as `arange()`, `plot()` and others.

You can also define functions yourself. If, for example, you've written a piece of code to plot your data, you wouldn't want to copy all that code each time you acquire new data.

Functions are an important aspect of learning how to code. The start of a function is denoted by the word `def`, which is followed by the function name (which you can choose for yourself), and subsequently the parentheses `()` which may or may not contain any parameters. Closed finally by a colon `:`. Check out the example:

    def print_greeting():
        print("Hello")

Note that much like with `if`-statements and `for`-loops, all code that is indented is part of the function's **code block**. Thus, you can terminate a function by simply *unindenting* any following code that you write.

This is a function that `print`s the string `Hello` to the terminal. If you add the aforementioned *definition* to a Python file, your computer will know that a function with the name `print_greeting()` exists. But the function hasn't yet been *executed*! You have to do so manually, by explicitly *calling* the function. This is how:

    print_greeting()

<!-- TODO deze was er ook nog, nog nodig?
## Examples of declaring functions

![embed](https://vimeo.com/album/5380760/embed)
 -->

## Details

Read more about functions here: [Think Python](http://greenteapress.com/thinkpython2/html/thinkpython2004.html)

## Style and design

Using functions improves the readability of your code. With a well-chosen name for each function you can easily gain an overview of what the code is meant to do as a whole. It allows you to first quickly read all function names of a program before having to try and comprehend the functional code.

Functions can also be expedient when you repeatedly have to use a more or less identical piece of code. Oftentimes when you catch yourself copy-pasting parts of your own code, you'd better spend this time trying to find a way to efficiently reuse the code your copying by defining a function!

<!-- TODO Ik heb dit nu toegevoegd, is dat OK? -->

## Programming Basics book

To further aid you in practicing with functions, we have created an [excerpt of the Programming Basics book on functions](book_en.pdf).

The idea in the book is that every sub-chapter consists of two pages; one page with exercises, and one page with an in-depth explanation. We advise you to open the book in a two-page view. If you already have some experience with calculations in programming languages, be sure to do the last few exercises of every page. Otherwise, make exercises until you think you can do it without making _any_ mistakes. Check if your answer is indeed correct! All answers to the exercises are in the back of the book.

## Details

If you want, you can read more in-depth about functions here: [Think Python](http://greenteapress.com/thinkpython2/html/thinkpython2004.html)
