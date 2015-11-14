# Introduction to Regular Expressions

Author: Anne Sonnenschein 
Created: 11/13/2015

This tutorial is designed to give a brief introduction to regular expressions. Several exercises were modified from Practical Computing for Biologists by Haddock and Dunn.

## Overview

Regular expressions (or regex) are a language for search and replace. They allow search for wild-cards: characters that can match more than one string. This can be especially useful for text editing, or converting large files from one format to another. Regular expressions are enabled in some text editors, and many programming languages (notably Python and Perl). In Unix they are implemented in tools such as grep and sed. The syntax is generally common across platforms.

In this tutorial, you will learn syntax for simple regular expressions, and how to implement them in text editors, python and perl.


## Regex using text editors
For this part of the activity you will need a text editor with regular expressions enabled. For the exercise at the end, you will need either Python or Perl.

TextWrangler (Mac) 
http://www.barebones.com/products/textwrangler/download.html

Notepad++ (Windows) 
https://notepad-plus-plus.org/download/v6.8.6.html

### Getting started
The first piece of data we will use is this list of species:

``` 1. Drosophila melanogaster
2. Drosophila simulans
3. Drosophila sechellia
4. Anopheles gambiae
5. Aedes aegypti
6. Tribolium castaneum
7. Apis mellifera ``` 

Copy this list into your text editor.

If you are using TextWrangler, select Find from the Search menu, and check the option "Grep".

If you are using Notepad++, select Replace... from the Search menu, and check the option "Regular expressions".

The first thing we will do is look at which parts of the list correspond to 'wildcards' 
### Wildcards
###### Basic wildcards
\w : indicates letters, numbers and underscores
\d : indicates digits from 0-9
\D : indicates any character **except** digits
\t : indicates tab
\s : indicates white space or new line character
\S : indicates any character **except** white space
\r: indicates carriage return
\n: indicates line-feed
.: indicates any character or white space

Using the 'search' option, but without replacing, look at what you get when you search \w. This search term should match with each individual letter and number, but not the white spaces or punctuation.

Look at the results when you search \d, \r, \n, or \r\n.

Depending on the operating system and/or text editor, new lines may be indicated by \r, \n, or \r\n.

Let's remove the numbers. Enter \d for search, and leave replace blank.

Now your list should look like:

``` . Drosophila melanogaster
. Drosophila simulans
. Drosophila sechellia
. Anopheles gambiae
. Aedes aegypti
. Tribolium castaneum
. Apis mellifera ```


Now lets get rid of the dots. See what happens if you search . and leave replace empty.

That was fun! Now type command-z (mac) or ctrl-z (windows) to restore your text.

When regular expressions are enabled, . matches any character. When you want to search a character that matches a wildcard/special character, preface it with a backslach. If the special character **is** a backslash, your escape will be a second backslash (e.g. \\)

To remove the periods, search \. and replace with blank.

Now your list should look like:

 ``` Drosophila melanogaster
 Drosophila simulans
 Drosophila sechellia
 Anopheles gambiae
 Aedes aegypti
 Tribolium castaneum
 Apis mellifera ```

There's still an extra blank space before the genus names. What wild card will you search for to remove it?


What went wrong?

\s matches to white space, or new-lines. To get around this, search \r\n\s, and replace with \r\n. Manually fix the first line.

Now figure out how to move all the elements of the list onto one line, separated by commas.

### Quantifiers

Adding a + to a wild card allows it to match multiple occurrences of that card in succession.

If you want to match multiple word-characters in a row, you will search \w+

Multiple-digit numbers can be found with \d+

If you want to preserve a wild-card character that you're searching, bracket it with parentheses.

Let's change the 'Genus species' nomenclature to 'G. species'.

Search (\w)\w+ and replace with \1.

Now your list should look like
``` D. melanogaster, D. simulans, D. sechellia, A. gambiae, A. aegypti, T. castaneum, A. mellifera ```

### Invisible characters

It can be difficult to tell \r from \r\n, or tab characters from white space. You can see these 'invisible characters' by adjusting the settings in your text editor.

##### Adjust settings in TextWrangler:
Select View -> Text Display -> Show Invisibles

##### Adjust settings in notepad ++:
View -> Show Symbol -> Show All Characters

### Text editor exercises

#### Exercise 1
Open the file "twenty_seven_club.txt"

There's a superstition about musicians dying at age twenty-seven, that became well known after the deaths of well-known singers like Kurt Cobain and Amy Winehouse. This list (taken from wikipedia) contains a full list of musicians who died at the age of twenty-seven.

Notice how words are separated by white space, and categories are separated by tabs. 

Replace the full date in the second column with just the year, using the following commands:

Search: (\w+)\t\w+\s\d+,\s
Replace: \1\t

Now figure out how to remove all information on each line after the year (cause of death, age, etc.)

#### Exercise 2

Open the gff file "example.gff". gffs are flat text files containing genomic features, that can be opened in any text editor. 

The first few lines are headers. The informative lines all look like:

```chr2L	macs	peak_call	214988	216272	6.38	.	.	Summit=826;Tags=82;pval=159.43;fdr=6.38 ```

Bedgraphs are another file format frequently for genomic data. This line in bedgraph format would include the chromosome, coordinates, and score (summit). It would look like:

```chr2L	214988	216272	826 ```

Change the information in this file from gff format to bedgraph format.




## Regex using Python

```python
# python code
import this
``` 

## Regex using Perl

### Programming exercises

![XKCD link](https://imgs.xkcd.com/comics/regular_expressions.png)
** from https://xkcd.com/208/

#### References
Haddock and Dunn, 2011. Practical Computing for Biologists, chapter 2


