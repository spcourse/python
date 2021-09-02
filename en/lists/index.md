# Lists

A list in Python is a useful way of grouping data so they can be interacted with as a whole. This way, calculations can be performed on the entire collection in one go instead of on each number individually.

## What are lists?

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_nlkxjtml&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_r1d1hzq5)

### Reading

The following code creates a new list called `staff` filled with strings (names):

    staff = ["Martijn", "Ivo", "Jelle", "Maarten", "Huub", "Marianne"]

You can request a single element of a list with `[`, `]`. The following code prints "Jelle"

    my_name = staff[2]
	print(my_name)

Beware that you start counting at `0` with indexing lists. So, the following code prints "Martijn":

    my_name = staff[0]
	print(my_name)

You can also manipulate the contents of a list. The following code changes the 4th element of the list, which is at index `3`, because we start with counting at `0`.

    staff[3] = "Vera"

So, now the list `staff` is: `["Martijn", "Ivo", "Jelle", "Vera", "Huub", "Marianne"]`

You can add an element to the end of the list (i.e, extending it):

    staff.append("Tom")


## Looping over Lists

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_kwirg85k&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_emta411f)

You could loop over lists with indices, using `range()` and `len()`, like this:

    measurements_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    measurements_science_park.append(20.5)
    print("In total, we have {len(measurements_science_park)} measurements:")
    for i in range(len(measurements_science_park)):
        print(f"Measurement #{i} was {measurements_science_park[i]} degrees.")

However this is not the most convenient way to do this in Python. A more "Pythonic" way of looping over lists is like this:

    measurements_science_park = [12.7, 18.8, 24.9, 14.5, 19.0]
    measurements_science_park.append(20.5)
    for measurement in measurements_science_park:
        print(f"The measurement was {measurement} degrees.")

Both examples will print the following:

    In total, we have 5 measurements:
    Measurement #0 was 12.7 degrees.
    Measurement #1 was 18.8 degrees.
    Measurement #2 was 24.9 degrees.
    Measurement #3 was 14.5 degrees.
    Measurement #4 was 19.0 degrees.


## Use-case: filtering elements out of a list

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_kczpbtsy&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_ewvj552h)

It is common to want to filter a list. Say we have a list of numbers:

    numbers = [8, 2, 3, 15, 7, 19]

We want to create a new list with only the elements from `numbers` that are bigger than 5.

    numbers2 = [8, 15, 19]

How do we do this?

We can write a loop that checks for each element if a certain condition is met. If this is the case, it is appended to the new list. Like so:

    numbers = [8, 2, 3, 15, 7, 19]

    numbers2 = []
    for number in numbers:
        if number > 5:
            numbers2.append(number)

    print(numbers2)


This is a pattern that you see a lot: go over all elements in a list, if they meet some condition, add them to another list. We call this pattern filtering.

## For more details:

In English, read about [lists](http://greenteapress.com/thinkpython/html/thinkpython011.html) at Think Python.
