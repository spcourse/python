# Data structures

The goal of this assignment is to get more familiar with the Python `dictionary`.

Create a file called `datastructures1.py` and implement the functions below.

### 1. Lemmas

Create a function named `count_lemmas(text, lemmas)`. The function should count the occurrences of each `lemma` (base form of a word) in the given `text` and return the result as a dictionary.

> A lemma is a base form of a word that serves as a canonical representation of a set of words that have similar meanings. For example, the lemma of "run," "running," and "ran" is "run." In the given code, the lemmas parameter is a dictionary that maps the variations of a word to its lemma.

The text parameter is a string containing the text to be analyzed. The function should split (use `.split()`) the text into words; remove any punctuation marks (use `.strip()`); and convert to lowercase (`.lower()`). If the word exists in the `lemmas` dictionary, count the lemma, not the word itself.

You can use the function `tokenize(text)` below to convert the input text into a list of words:

    def tokenize(text):
        return [word.strip(" ,\n.);(!?)'").lower() for word in text.split(' ')]

Example usage:

    text = "He is, was and will be a runner. And runners ran, run and will always run. This is their nature."

    lemmas = {
        "runners": "runner",
        "ran": "run",
        "was": "be",
        "is": "be"
    }

    print(count_lemmas(text, lemmas))

Expected output:

    {'he': 1, 'be': 4, 'and': 3, 'will': 2, 'a': 1, 'runner': 2, 'run': 3, 'always': 1, 'this': 1, 'their': 1, 'nature': 1}


### 2. Grammatical categories

Create a function called `count_category(lemma_counts, category)`. This function counts the occurrences of lemmas of a specific grammatical category (for example verbs or nouns). The input is `lemma_counts`, a dictionary of lemma counts like you created in the last assignment, and `category` a set of words representing a grammatical category.

(If you didn't finish the previous assignment, no worries, the correct `lemma_counts` dictionary is provided below.)

Example usage:

    lemma_counts = {'he': 1, 'be': 4, 'and': 3, 'will': 2, 'a': 1, 'runner': 2, 'run': 3, 'always': 1, 'this': 1, 'their': 1, 'nature': 1}
    nouns = {'runner', 'nature', 'building'}
    verbs = {'walk', 'run', 'be'}
    determiners = {'the', 'a', 'this', 'their'}

    print(count_category(lemma_counts, nouns))
    print(count_category(lemma_counts, verbs))
    print(count_category(lemma_counts, determiners))

Expected output:

    3
    7
    3

### 3. Incrementing values

Create a function called `increment_counts(counts, words)`. This function updates a dictionary of word counts.

The input is `counts`, a dictionary that maps words to integers, and `words`, a list of words. For each word in `words`, increase its value by 1 if it already exists in the dictionary. If the word does not exist yet, add it to the dictionary with value 1.

You are not allowed to use `+=` or `-=` in this exercise. Refer to the ["updating existing values" section on the Dictionaries theory-page](/python/en/dictionaries/use#updating-existing-values).

Example usage:

    counts = {'apple': 2, 'banana': 1}
    words = ['banana', 'apple', 'orange']

    print(increment_counts(counts, words))

Expected output:

    {'apple': 3, 'banana': 2, 'orange': 1}

### 4. Library

We have loaded information about book genres into a dictionary called `library`. The dictionary has the titles of the books as keys and the genres as values (see usage example below). We would like to group the titles by genre. Write a function called `group_titles_by_genre(library)`, that takes the dictionary and outputs a new dictionary where each key is a genre and each value is a list of all titles that belong to the given genre.

Example usage:

    library = {"Life of Pi": "Adventure",
               "One World The Water Dancer": "Fantasy",
               "The Three Musketeers": "Adventure",
               "To Kill a Mockingbird": "Classics",
               "Circe": "Fantasy",
               "The Call of the Wild": "Adventure",
               "Little Women": "Classics"}

    grouped = group_titles_by_genre(library)
    print(grouped)

Expected output:

    {'Adventure': ['Life of Pi', 'The Three Musketeers', 'The Call of the Wild'], 'Fantasy': ['One World The Water Dancer', 'Circe'], 'Classics': ['To Kill a Mockingbird', 'Little Women']}

*Hint:* Think about how updating values in a dictionary works. When do you assign a new value to a key, and when do you modify an existing value?

## Test

You can verify your results with:

    checkpy datastructures1
