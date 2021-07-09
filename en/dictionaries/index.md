# Dictionaries

Dictionaries are one of the fundamental data structures of Python, and
just like lists, they can be used to store several elements together in
one variable. Unlike lists, dictionaries store *mappings* from a key to a
value.

## 1. Basic operations

### Video
Watch this video to learn about dictionaries:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_80k74cvx&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_zmx8rsom)

### Reading
And read more about how to use dictionaries: [basic operations](/python/en/dictionaries/basic-operations/)

### Practice

Test your understanding with the following practice exercises. Use your usual code editor and create a file called `dictionaries.py`.

#### Exercise 1
Similar to the video, create a dictionary called `my_class` with students and grades. Use the names Ralph, Diana, Jordi, and Michele with their respective grades: 4, 8, 7, and 5.

#### Exercise 2
Add a student Gretel to the above dictionary with a grade of 9. Print the dictionary `my_class` to check if Gretel is indeed added to the dictionary.

#### Exercise 3
Write a piece of code that asks the user to input a name and looks in the dictionary `my_class` if the student exists. Print the message "[name] is a student in this class." or "[name] is not a student in this class, and had the grade: [grade]", depending on whether or not the student is in the dictionary `my_class`. Example usage

	python dictionaries.py
	Enter a name: Jordi
	Jordi is a student in this class, and has the grade: 7.

Use the `in` operator for this exercise. Do not use `get()`.

#### Exercise 4
Use the following list of students:

	students = ["Michele", "Diana", "Maria", "Ralph", "Jacobus"]

Write a loop that looks up each student from the lists in `my_class` and prints "[name]: [grade]" on a new line for each student. If the student doesn't exists in `my_class` it should print the text "n/a" for the grade. Expected output:

	Michele: 5
	Diana: 8
	Maria: n/a
	Ralph: 4
	Jacobus: n/a

Use `get()` for this. Do not use `in` and do not use an `if`-statement.

## 2. Speed

### Video
Learn more about the speed of dictionaries in this video:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_mjatxx9k&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_t24tqi37)

### Reading
And read more about the computational complexity dictionaries: [complexity](/python/en/dictionaries/complexity/)

### Practice



#### Exercise 1


This concludes this introduction to dictionaries.

Next up, we'll cover another data structure called *tuples*.
