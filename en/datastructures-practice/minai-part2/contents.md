# OPTIONAL: more data structures

The goal of this practice page is to get even more familiar with the Python datastructures `dictionary` and `set`.

Create a file called `datastructures_minai2.py` and implement the functions below.

### 1. Unify

The first function is `unify(dict1, dict2)`. It combines two dictionaries. It should return a dictionary that contain all items (key-value pairs) from both dictionaries. If a key occurs in both input dictionaries, unify the corresponding lists. The value lists of the output should remain sorted and not contain any duplicates.

Example usage:

    dict1 = {"a": [1, 2, 3], "c": [4, 5, 6], "d": [6]}
    dict2 = {"a": [1, 3, 4], "b": [9], "c": [2, 4]}
    print(unify(dict1, dict2))

Expected output:

    {'d': [6], 'a': [1, 2, 3, 4], 'c': [2, 4, 5, 6], 'b': [9]}

### 2. Melt

Implement the function `melt(dict)`. It should return a list of tuples by unpacking the lists of values. There should be a tuple for each for each combination of key and value as they appear in the value lists of the input dictionary.

Example usage:

    dict1 = {"a": [1, 2, 3], "c": [4, 5, 6], "d": [6]}
    print(melt(dict1))

Expected output:

    [('a', 1), ('a', 2), ('a', 3), ('c', 4), ('c', 5), ('c', 6), ('d', 6)]

### 3. N-intersection

With sets it's relatively easy to compute the intersection between two sets (i.e., create a set with the items that are in both input sets). But it can be useful to compute the intersection between not just two, but an arbitrary number of input sets. Write a function called `n_intersection(sets)`, that takes as input a list of sets (`sets`) and returns the intersection of all of those sets.

Have a look a this example:

    ex1 = n_intersection([{5, 9, 6}, {9, 2, 6}, {6, 5, 9}])
    ex2 = n_intersection([{"kerfuffle", "hullaballoo", "ragamuffin", "flummox"},
                          {"kerfuffle", "ragamuffin", "gobbledygook", "flummox"},
                          {"hullaballoo", "ragamuffin", "gobbledygook", "flummox"},
                          {"hullaballoo", "ragamuffin", "ragamuffin", "gobbledygook", "flummox"}])
    ex3 = n_intersection([])

    print(ex1)
    print(ex2)
    print(ex3)

This should give the following output:

    {9, 6}
    {'ragamuffin', 'flummox'}
    set()

> Tip: `set()`, just means an empty set. This cannot be written as `{}` because that's already used in python for an empty dictionary.

### 4. Sentiment

Write a Python function called `sentiment_of_text(text, sentiment_of_word)` that takes a text string and a dictionary of word sentiments as input and returns the overall sentiment score of the text. The sentiment score is calculated as the sum of sentiment scores for individual words in the text using the provided `sentiment_of_word` dictionary. You may assume that words that cannot be found in the dictionary have a sentiment score of 0. You can use the `tokenize()` function of the first assignment.

This is the `sentiment_of_word` dictionary:

    sentiment_of_word = {
        "abysmal": -5, "agonizing": -4, "dreadful": -5, "grim": -3, "horrible": -5,
        "miserable": -4, "terrible": -5, "upset": -3, "unpleasant": -2, "woeful": -4,
        "horrific": -5, "disastrous": -5, "appalling": -5, "repulsive": -4, "noxious": -3,
        "atrocious": -5, "vile": -4, "wretched": -3, "deplorable": -5, "abominable": -5,
        "amazing": 5, "fantastic": 4, "joyful": 4, "excellent": 5, "delightful": 4,
        "wonderful": 5, "terrific": 4, "great": 3, "awesome": 5, "superb": 4,
        "fabulous": 4, "incredible": 5, "marvelous": 4, "phenomenal": 5, "outstanding": 4,
        "brilliant": 5, "spectacular": 4, "splendid": 3, "glorious": 4, "fantabulous": 5
    }

As you can see, negative words have negative scores and positive words have positive scores.


Example usage:

    text1 = "Wow, what an amazing day it has been! The weather is fantastic!"
    text2 = "Today has been abysmal. The weather is dreadful, and I feel miserably upset."

    print(sentiment_of_text(text1, sentiment_of_word))
    print(sentiment_of_text(text2, sentiment_of_word))

Expected output:

    9
    -13


## Test

You can verify your results with:

    checkpy datastructures_minai2
