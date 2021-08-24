# Functions

## Functions
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_5l6vbblu&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_clhk47gk)


A function is a way to dramatically improve the design of your code. A function has some input, it does something with it, and then produces some output. You've already been using functions in python. For example the function `len()`:

    some_list = ['so', 'long', 'and', 'thanks', 'for', 'all', 'the', 'fish']
    x = len(some_list)
    print(x)

 The function `len()`, takes a list as input, then it counts the element, and as an output it gives the length of the list:

 - The input `some_list` is given between the parentheses: `len(some_list)`
 - The output of the function is assigned to `x` by the equals (`=`) operator: `x = len(some_list)`

The function `len()` is built in to Python, so we don't have to worry about how it works internally, as long as we know how to use it. Let's however pretend that such a function does not exist, how would we define `len` ourselves? Let's call this function `length`:

    def length(lst):
        count = 0
        for e in lst:
            count += 1
        return count

    some_list = ['so', 'long', 'and', 'thanks', 'for', 'all', 'the', 'fish']
    x = length(some_list)
    print(x)

The function `length` does the exact same as `len`. It takes a list as input, counts the elements, and returns the length of the list. A couple of things to notice:

- The start of a function is denoted by the word `def`, which is followed by the function name, which you can choose for yourself. We chose the name `length`.
- Then the parentheses `()` which may or may not contain any parameters.
- If we have parameters, we write them inside the parentheses. In this case we define the parameter `lst`.
- Don't forget the colon `:` at the end of the line.
- On the next lines we have the body of the function. Here we define the variable `count` and count the elements of the list.
- The command `return` is used to specify which value should be returned by the function. In this case we want to return the value of the variable `count`, so we write `return count`.

Keep in mind that the function stops running as soon as `return` is encountered, even if there is still code after the `return`.


## Functions with multiple parameters
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_03dms4u5&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_uhohnubo)

A function can have more than one parameter. For example if I want a function that computes the value ($y = a^2 + b$), I can define a function like this:

    def my_fun(a, b):
        y = a**2 + b
        return y

    my_val = my_fun(3, 2)
    print(my_val)

We've defined a function similar to the way we did above. The main novelty here is that the function `my_fun` accepts two parameters, `a` and `b`.

Note that the *order of the values* 3 and 2 provided when we call the function (`my_val = my_fun(3, 2)`) should correspond to the *order of the input parameters* in the definition of the function (`def my_fun(a, b):`). The call `my_val = my_fun(2, 3)` would give a different output.

## Details

Read more about functions here: [Think Python](http://greenteapress.com/thinkpython2/html/thinkpython2004.html)

## Style and design

Using functions improves the readability of your code. With a well-chosen name for each function you can easily improve the readability of your code. If a program is well designed you can often get an overview of what it does by simply looking at the function names.

Functions can also be expedient when you repeatedly have to use a more or less identical piece of code. Oftentimes when you catch yourself copy-pasting parts of your own code, you'd better spend this time trying to define a function!

## Programming Basics book

To further aid you in practicing with functions, we have created an [excerpt of the Programming Basics book on functions](book_en.pdf).

The idea in the book is that every sub-chapter consists of two pages; one page with exercises, and one page with an in-depth explanation. We advise you to open the book in a two-page view. If you already have some experience with calculations in programming languages, be sure to do the last few exercises of every page. Otherwise, make exercises until you think you can do it without making _any_ mistakes. Check if your answer is indeed correct! All answers to the exercises are in the back of the book.
