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
<details markdown="1"><summary  markdown="span">Read more about dictionaries.</summary>

The difference between dictionaries and lists is that instead of using an index
to access elements, we use a key. Searching for things by their keys is the
main reason dictionaries are used so often and why they are such an efficient
data structure. In a list, if we don't know at what index something is stored
exactly, we'd have to loop over the list until we found the matching element, whereas in a dictionary, we can just search by key. More on why this is
efficient later, for now let's just see a simple example.

One way we could use a dictionary is to store the mappings in an actual
English-Spanish translation dictionary. We might have the string "Yes" and we
want to store its Spanish translation:

	KEYS            VALUES
	------------------------
	Yes         :   Si
	No          :   No
	Please      :   Por favor
	Thank you   :   Gracias

Here the English words are the keys and we can easily look up their Spanish
translation in the dictionary.

	Dictionary[Please]
	-> Por favor

The mapping here is from one element to another associated element (its
translation), which we might want to look up. This is generally how
dictionaries are used in Python. Let's take a closer look at the syntax in
Python and some more cases where we might want to use dictionaries.

### creating a dictionary

So, dictionaries are an efficient way to store pairs of variables together. As
another example, we could make a fruit basket and store the quantity we have of the different types of fruit. In our previous example we stored Spanish
translations for English words in our dictionary, and here we are going to
store counts for each type of fruit. Using dictionaries in this way, as a
mapping from elements to some count (or a score), is another very common way to use dictionaries

    >>> basket = {'apple': 4, 'banana': 7, 'orange': 2}
    >>> basket
    {'apple': 4, 'orange': 2, 'banana': 7}

Note that the order of these elements has changed! Dictionaries are unordered collections of pairs, which means we can easily find back each pair, but cannot make any assumptions about the order in which they are stored.

### accessing elements

If we want to know how many apples there are in the fruit basket, we can write

    >>> basket['apple']
    4

The left half of each pair is called the **key** and the right half is called
the **value**. So, here we used the key `'apple'` to find the value `4`. This
syntax is very similar to using square brackets to get elements from a *list*,
but instead of using the **index** to retrieve the element stored at that
place in the list, we use the **key** to retrieve the corresponding **value**
from the dictionary.

### adding items

Using this same syntax, we can add a new *key-value pair*

    >>> basket['strawberry'] = 10
    >>> basket
    {'apple': 4, 'orange': 2, 'strawberry': 10, 'banana': 7}

Or we could use this syntax to modify an existing pair. Let's say we ate one of
the bananas, then we could update the dictionary by writing

    >>> basket['banana'] -= 1
    >>> basket
    {'apple': 4, 'orange': 2, 'strawberry': 10, 'banana': 6}

Each *key* in a dictionary **must** be unique, so if we try to add a *key*
that already exists, we'll end up overwriting the corresponding *value*. So,
if we try to add another key for apples, we'll just end up replacing the old
pair

    >>> basket['apple'] = 6
    >>> basket
    {'apple': 6, 'orange': 2, 'strawberry': 10, 'banana': 6}

### pitfalls

Note that values **do not** have to be unique, as dictionaries are only a
one-way mapping, so you can only use the *keys* to retrieve the corresponding
*values*, not the other way around. Searching for a pair using the value will
produce a *KeyError*

    >>> basket[2]
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 2

because the key `2` does not exist in our basket. The value `2`, does of
course occur in our basket, stored under the key `'orange'`

    >>> basket['orange']
    2

If we try to retrieve the number of *mangoes*, which aren't in the basket at all,
we also get a *KeyError*

    >>> basket['mango']
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'mango'

### get

Sometimes when we use a key that's not in the dictionary we do not want it to throw an error. But instead return a default value (for example `0`). For this, we can use the `get()` function instead of the square brackets, and as the second argument tell the dictionary what value we want if the key is not present in the dictionary:

    >>> basket.get('mango', 0)
    0

So, now we know that our fruit basket unfortunately contains zero mangoes, but in
many situations this result is much more useful than producing an error.

Note that when an item *is* present in the dictionary `get()` will behave just the same as the square brackets:

    >>> basket.get('apple', 0)
    6
    >>> basket['apple']
    6

It is also important to realize that `get()` **does not add items to the dictionary**. After using `get()` to lookup `'mango'`, it is not added to the dictionary.

    >>> basket.get('mango', 0)
    0
    >>> basket
    {'apple': 6, 'orange': 2, 'strawberry': 10, 'banana': 6}

### in

We can also explicitly ask if a key is present in the dictionary using `in`

    >>> if 'banana' in basket:
    ...   print("We've got bananas!")
    ...
    We've got bananas!

This works exactly the same way as it does for lists. But it only looks at the *keys* of the dictionary. It will not check the *values* of a dictionary. There is one important difference between using `in` with dictionaries and using `in` with lists: With dictionaries `in` is much (!) faster. More about that later.

### looping

Dictionaries are mostly used for look-up operations, but
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

</details>

### Practice
<details markdown="1"><summary  markdown="span">Practice with dictionaries.</summary>

Test your understanding with the following practice exercises. Use your usual code editor and create a file called `dictionaries.py`. You can check (some of) your answers here: [answers](/python/en/dictionaries/answers)

**Exercise 1** Similar to the video, create a dictionary called `my_class` with students and grades. Use the names Ralph, Diana, Jordi, and Michele with their respective grades: 4, 8, 7, and 5.

**Exercise 2** Add a student Gretel to the above dictionary with a grade of 9. Print the dictionary `my_class` to check if Gretel is indeed added to the dictionary.

**Exercise 3** Write a piece of code that asks the user to input a name and looks in the dictionary `my_class` if the student exists. Print the message "[name] is a student in this class, and has the grade: [grade]." or "[name] is not a student in this class.", depending on whether or not the student is in the dictionary `my_class`. Example usage

	python dictionaries.py
	Enter a name: Jordi
	Jordi is a student in this class, and has the grade: 7.

Use the `in` operator for this exercise. Do not use `get()`.

**Exercise 4** Use the following list of students:

	students = ["Michele", "Diana", "Maria", "Ralph", "Jacobus"]

Write a loop that looks up each student from the lists in `my_class` and prints "[name]: [grade]" on a new line for each student. If the student doesn't exists in `my_class` it should print the text "n/a" for the grade. Expected output:

	Michele: 5
	Diana: 8
	Maria: n/a
	Ralph: 4
	Jacobus: n/a

Use `get()` for this. Do not use `in` and do not use an `if`-statement.

</details>

## 2. Speed

### Video
Learn more about the speed of dictionaries in this video:

![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_mjatxx9k&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_t24tqi37)

### Reading
<details markdown="1"><summary  markdown="span">Read more about computational complexity of dictionaries.</summary>

The time complexity for getting an item out of a dictionary $$O(1)$$. This means that the time the following command takes:  

    >>> basket['apple']
    6

does not depend on the size of basket. No matter if `basket` contains 10 items or 1,000,000 items, it takes roughly the same time to compute.

The same goes for other types of lookup, like the `in` operation. With dictionaries the `in` operations is $$O(1)$$. So also for the computation time of the following command it does not matter how big `basket` is:

    >>> if 'banana' in basket:
    ...   print("We've got bananas!")
    ...
    We've got bananas!

This is a big difference with list. With lists, the operation `in` is $$O(N)$$.

That lookup times for dictionaries are an $$O(1)$$ operation is a *strange and counter-intuitive* fact, and why this is true is well beyond the scope of this text, but it should give you an idea of the power of
dictionaries and why they are used so often: Checking if a key is present in a
dictionary or retrieving the value stored with that key are both **constant
time** $$O(1)$$ operations, irrespective of the number of elements
stored in that dictionary.

</details>

### Practice
<details markdown="1"><summary  markdown="span">Practice with computational complexity of dictionaries.</summary>

**Exercise 5**
Measure the dictionaries and list in a similar way as in the video, but now focus on the `in` operator. Use runs with lists and dictionaries of different sizes. Use 10, 100, 1000, and 10,000 (ad maybe 100,000 if you have a fast computer). For every run, execute the `in`-operation 100,000 times (to get reliable results). Write down the results (you can do this manually), and create a table with the runtimes that looks something like this:

	size  |  list |  dict
	10    |  0.14 |  0.09
	100   | ??.?? | ??.??
	1000  | ??.?? | ??.??
	10000 | ??.?? | ??.??

You can use the code below to get started

	from time import time
	from random import randint

    # create a list or dictionary containing n items

	# test speed
	iterations = 100000
	start = time()
	for _ in range(iterations):

		# TODO: enter code to test

	end = time()
	print(f'The time elapsed: {end-start:.2f} seconds (with {iterations} iterations)')

</details>
