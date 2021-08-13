# Functions as arguments

## Video
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_ypcaq3sp&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_1f4425kz)


## Reference
It can be useful to provide a function as an argument to another function. This can be a little confusing
at first. Take a look at the following example code:

	def add(a, b):
		return a + b

	def mult(a, b):
		return a * b

	def repeat(my_function, x, y, z):
		total = my_function(x, y)
		total = my_function(total, z)
		return total

	added = repeat(add, 4, 3, 2)
	print(added)

	multiplied = repeat(mult, 4, 3, 2)
	print(multiplied)

The output will be:

	9
	24


Here the function `repeat()` is used for two different purposes. In the first call it adds all numbers together. In the second call they are multiplied.

The difference of behavior in the two cases is accomplished by having the parameter `my_function` which is applied twice in the `repeat`. When calling `repeat` we specify what we want `my_function` to be. In the first case that is the function `add`, in the second case this is the function `mult`.

The provided example function only uses the functions `add` and `mult`, but
**any** Python function you would define to combine two numbers would work
together with this `repeat()`. Test out the example above and observe
the two different printed results. Try to define your own
combination function and use it together with `repeat()`.

The example here is a little artificial, but it does provide a complete
template for how to use functions as arguments.
