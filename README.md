# Sustainable-Development-Goals

Creating an interactive web application for self development goals classifier in a Jupyter Notebook, using the two libraries ipywidgets, voila and i am using **N-gram matcher** from OSDG repository.

Below is the binder link for running the web app

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/krishnakanth-G/Sustainable-Development-Goals/HEAD?urlpath=%2Fvoila%2Frender%2FSDG.ipynb)

In this web app we can upload a text file and submit it to genreate SDG's from the text. I am running the SDG notebook in binder. 
SDG_New is jupyter notebook which will accept PDF and Text files but i am not deploying it in binder.

## Required libraries:
* ipywidgets
* nltk
* voila


## Code

1) Firstly i am importing all the libraries which are required
   * ipywidgets - to create a widgtes in python
   * nltk - to do necessary preprocessing of data
   * voila - to run the note book as web app
   * json - to read json files
   * typing - standard notation for Python function and variable type annotations
   * numpy - to work with arrays
   * re - to specify a set of strings that matches it
   
2) I am using the n-gram matcher function from OSDG github to match ngrams to texts.For each document, it will do the follwing:
   * Converts document into tokens
   * Generates ngrams of size defined in ngram_size (1 to 4)
   * Crossreferences ngrams with matching ngrams 
   * The matcher function will return two indices that are index 0 which contains ngram indices and index 1 which contains frequencies list respectively
   
3) fos_names and fos_ids are from OSDG which contains the unique keywords and their corresponding ids. Then I am creating an object for n-gram matcher with fos_names as n grams, 1 to 4 as ngrams size, lowercase as true and pattern using re by defining empty space as boundaries & word in between as parameters.
