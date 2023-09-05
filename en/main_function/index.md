# Main function

In python it is considered good practice to define a `main()` function as a starting point for executing you code. For example:

    def main():
        text = "For sale: baby shoes, never worn."
        number_of_words = count_words(text)
        print(f"There are {number_of_words} words in this text")

    # some function
    def count_words(string):
        words = string.split()
        n_words = len(words)
        return n_words

    if __name__ == '__main__':
        main()

You see that in this case **all** the code is neatly wrapped in functions. The code on line 2 - 4, that you'd normally just put in the main body of the python file, is now all delegated to the function called `main()`. To understand why and how, have a look at the video below.

<!-- ## Use main() for better design -->

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_o7li93ev&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_6sec38d5)

The condition, `if __name__ == '__main__':`, might look somewhat mysterious. For now, you don't have to fully understand it. This condition becomes more relevant once you start creating bigger python projects that are spread out over multiple files.

If you already know how to create multi-file python projects, you can have a look here: [if name is main](/python/en/name_is_main)

<!-- ## If name is main?

This part is extra background information but con
In order to understand the mysterious condition `if __name__ == '__main__':` you need to know how importing external files in python works. If this is the case, have a look at the following video.

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_xw7hb3hd&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_cubflf3h) -->
