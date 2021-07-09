# Dictionaries

Dictionaries are one of the fundamental data structures of Python, and
just like lists, they can be used to store several elements together in
one variable. Unlike lists, dictionaries store *mappings* from a key to a
value.

## Basic operations

Watch this video to learn about dictionaries:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_80k74cvx&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_zmx8rsom)

And read more about how to use dictionaries: [basic operations](basic-operations/)

## Speed

Learn more about the speed of dictionaries in this video:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_mjatxx9k&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_t24tqi37)


That lookup times for dictionaries are an $$O(1)$$ operation is a *strange and counter-intuitive* fact, and why this is true is well
beyond the scope of this text, but it should give you an idea of the power of
dictionaries and why they are used so often: Checking if a key is present in a
dictionary or retrieving the value stored with that key are both **constant
time** $$O(1)$$ operations, irrespective of the number of elements
stored in that dictionary.

As a result, dictionaries are mostly used for these look-up operations, but
sometime you'll also want to loop over the elements in your dictionary.
Dictionaries support many of the same operations that lists do. For instance,
you can use `len` to ask how many pairs there are in the dictionary

    >>> len(basket)
    4

We can also use `for` loops with dictionaries, like so

    >>> for fruit in basket:
    ...   print(fruit)
    ...
    apple
    orange
    strawberry
    banana

This will only loop over the keys of the dictionary, but we could just use the
square brackets to retrieve the values as well

    >>> for fruit in basket:
    ...   print(fruit, basket[fruit])
    ...
    apple 6
    orange 2
    strawberry 10
    banana 6

We can even use the `items` function to easily loop over both

    >>> for fruit, amount in basket.items():
    ...   print(fruit, amount)
    ...
    apple 6
    orange 2
    strawberry 10
    banana 6

This concludes this introduction to dictionaries.

Next up, we'll cover another data structure called *tuples*.
