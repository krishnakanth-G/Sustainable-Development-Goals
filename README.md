# Sustainable-Development-Goals

Creating an interactive web application for self development goals classifier in a Jupyter Notebook, using the two libraries ipywidgets and voila.

Below is the binder link for running the web app

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/krishnakanth-G/Sustainable-Development-Goals/HEAD?urlpath=%2Fvoila%2Frender%2FSDG.ipynb)

In this web app we can upload a text file and submit it to genreate SDG's from the text. I am running the **SDG.ipynb** notebook in binder. 

## Required libraries:
* ipywidgets
* nltk
* voila
* json
* typing
* numpy
* re


## Code writeup

1) Firstly i am importing all the libraries which are required
   * ipywidgets - to create a widgtes in python
   * nltk - to do necessary preprocessing of data
   * voila - to run the note book as web app
   * json - to read json files
   * typing - standard notation for Python function and variable type annotations
   * numpy - to work with arrays
   * re - to specify a set of strings that matches it
   
2) I am using the n-gram matcher class from OSDG github to match ngrams to texts.For each document, it will do the follwing:
   * Converts document into tokens
   * Generates ngrams of size defined in ngram_size (1 to 4)
   * Crossreferences ngrams with matching ngrams 
   * The matcher function will return two indices that are index 0 which contains ngram indices and index 1 which contains frequencies list respectively
   
3) fos_names and fos_ids are from OSDG which contains the unique keywords and their corresponding ids. Then I am creating an object for n-gram matcher with fos_names as n-grams, 1 to 4 as n-grams size, lowercase as true and pattern as parameters.
4) Then I wrote a function mapping_ids() which takes text as parameter. This function will take the text and send it to match function by n-gram matcher object. Then the match function will return the ngrams indices (as per fos names) and their frequencies in two lists. After getting these lists the mapping_ids function will map the ngrmas indices to fos_ids and return a dictionary of fos_ids and their corresponding frequencies.
5) Importing OSDG-mappings file from OSDG GitHub which contains the SDG's mapping to fos_ids and OSDG-fosmap file from OSDG GitHub which contains the fos id and the key word for the fos id.
6) Then I built sdg_imp(), a function that takes a dictionary as a parameter. The fos ids: frequencies will be sent as parameters, and the fos ids and mappings will be intersected to retrieve the associated sdg's. After that, I use frequencies to count the importance of the sdgs, and then I return a dictionary of sdgs, importance, and keywords in the sdg.
7) The output from the above function is given to allsdgs function to get all the sdg’s as an output in a designed manner.
8) Preprocessing is a function that uses nltk to preprocess the given text. I'm lowering the text, eliminating stop words, and combining the cleaned text back into the original.
9) Then I created an upload widget to upload the text file and a submit widget to process text and find sdg’s from it.
10) The lines below will enable some widget & voila extensions, and because I've already enabled them, I've commented them out.
	* !jupyter nbextension enable --py widgetsnbextension --sys-prefix
	* !jupyter serverextension enable voila --sys-prefix
