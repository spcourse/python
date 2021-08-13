# Functions with multiple return values

## Video
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_xy3x2mjf&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_1455lt1x)

## Reference
Until now you've only seen functions that print and functions that return one value. In Python, it is possible to return any number of values by separating the values with commas. This is named _packing_; the return values do not need to be of the same type, and are grouped as if they are one output. It is possible to immediately _unpack_ the values that are returned by the function. This is done in nearly the same way as the return value was created, with comma-separated variable names:

    def test():
      return 'abc', 100, ['a', 'b', 123]

    a, b, c = test()

    print(a)
    print(b)
    print(c)

Which would give the following output:

    abc
    100
    ['a', 'b', 123]

In most cases, you will want to return two or three values. More is possible, but if you want to return a lot of values it is probably better to return a list or some other data structure.

One could also save the result of the function as a single variable, and specific elements of the result can be indexed as in a list:

    def hours_to_days(hours):
      days = floor(hours / 24)
      remainder = hours % 24

      return days, remainder

    test_result = hours_to_days(123)

    print(test_result)
    print(test_result[0])
    print(test_result[1])

Would give the following output:

    (5, 3)
    5
    3

The round brackets indicate that the values are packed together in a tuple. A tuple is a special type of "collection" in Python, but for now, it suffices to know that it behaves similarly to a list.
