# Data structures

The goal of this assignment is to get more familiar with the Python `dictionary`.

Create a file called `datastructures_minai1.py` and implement the functions below.

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

Create a function called `count_category(lemma_counts, category)`. This function counts the occurances of lemmas of a specific grammatical category (for example verbs or nouns). The input is `lemma_counts`, a dictionary of lemma counts like you created in the last assignment, and `category` a set of words representing a grammatical category.

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

### 3. Library

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

## Test

You can verify your results with:

    checkpy datastructures_minai1
