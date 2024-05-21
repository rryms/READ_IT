A quickly look before lecture
A quickly review after lecture
写一下大体印象就可，本子上写lec上的内容
[the reference book](https://learningds.org/intro.html)
[TOC]

# Lecture1
fuck, the lecture already has a excellent conclusion, read it and review it.
[Note](https://ds100.org/course-notes/intro_lec/introduction.html)

# Lecture2
[Note](https://ds100.org/course-notes/pandas_1/pandas_1.html#dataframe-attributes-index-columns-and-shape)
introduction of the API---pandas
conduct about the DataFrames, Series

# Lecture3
[Note](https://ds100.org/course-notes/pandas_2/pandas_2.html)
* Continue building familiarity with ***pandas*** syntax
* Extract data from a ***DataFrame*** using conditional selection
* Recognize situations where aggragation is useful and identify the correct technique for performing an aggregation.

# Lecture4
[Note](https://ds100.org/course-notes/pandas_3/pandas_3.html)
* Perform advanced aggregation using ``groupby()``
* Use the ``pd.pivot_table`` method to construct a pivot table
* Perform simple merges between DataFrames using ``pd.merge()``

# Lecture5
[Note](https://ds100.org/course-notes/eda/eda.html#structure)
* Recognize common file formats
* Categorize data by its variabele type
* Build awareness of issues with data faithfulness and develop targeted solutions
  
**Date clean**,aka,data wrangling,is the process of transforming raw data to facilitate subsequent analysis. It is often used to address issues like:
* Unclear structure or formatting
* Missing or corrupted values
* Unit conversions

**Exploratory Data Analysis(EDA)**,is the process of understanding a new dataset. It is an open-ended, informal analysis that involves familiarizing ourselves with the variables present in the data, discovering potential hypotheses, and identifying possible issues with the data. This last point can often motivate further data cleaning to address any problems with the dataset’s format; because of this, EDA and data cleaning are often thought of as an “infinite loop,” with each process driving the other.

## 5.1 Structure
### 5.1.1 File Formats
* **CSVs**,which stand for Comma-Separated Values,
  which are a common tabular data format.Each row, or record, in the data is delimited by a newline ``\n``. Each column, or field, in the data is delimited by a comma ``,`` (hence comma-separated!).
* **TSV**(Tab-Separated Values).
  In a TSV, records are still delimited by a newline ``\n``, while fields are delimited by ``\t`` tab character.
* **JOSN**(JavaScript Object Notation), files behave similarly to Python dictionaries
  EDA with JSON, File Size, Unix Commands, File Contents
  1. The above **metadata** tells us a lot about the columns in the data including column names, potential data anomalies, and a basic statistic.
  2. Because of its non-tabular structure, JSON makes it easier (than CSV) to create **self-documenting** data, meaning that information about the data is stored in the same file as the data.
  3. Self-documenting data can be helpful since it maintains its own description and these descriptions are more likely to be updated as data changes.

### 5.1.2 Primary and Foreign keys
### 5.1.3 Variable Types

## 5.2 Granularity, Scope, and Temporality
## 5.3 Faithfulness
## Demos
## Summary
### 5.6.1 Dealing with Missing Values
There are a few options we can take to deal with missing data:
* Drop missing records
* Keep NaN missing values
* Impute using an interpolated column
### 5.6.2 EDA and Data Wrangling
There are several ways to approach EDA and Data Wrangling:

* Examine the data and **metadata**: what is the date, size, organization, and structure of the data?
* Examine each **field/attribute/dimension** individually.
* Examine pairs of related dimensions (e.g. breaking down grades by major).
* Along the way, we can:
  * **Visualize** or summarize the data.
  * **Validate assumptions** about data and its collection process. Pay particular attention to when the data was collected.
  * Identify and **address anomalies**.
  * Apply data transformations and corrections (we’ll cover this in the upcoming lecture).
  * **Record everything you do!** Developing in Jupyter Notebook promotes reproducibility of your own work!



# Lecture6 Regular Expressions
* Understand Python string manipulation, ``pandas`` ``Series`` methods
* Parse and create regex, with a reference table
* Use vocbulary(closeure, metaccharacters, groups, etc.) to describe regex metacharacters

## 6.1 Why Work with Text?
discuss the necessary tools to manipulate text: Python string manipulation and regular expressions.
There are two main reasons for working with text.

1. Canonicalization: Convert data that has multiple formats into a standard form.
   1. By manipulating text, we can join tables with mismatched string labels.
2. Extract information into a new feature.
   1. For example, we can extract date and time features from text

## 6.2 Python String Methods
### 6.2.1 Canonicalization
### 6.2.2 Extraction
## 6.3 RegEx Basics
A **regular expression("RegEx")** is a sequence of characters that specifies a search pattern. They are written to extract specific information from text. Regular expressions are essentially part of a smaller programming language embedded in Python, made available through the ``re`` module. As such, they have a stand-alone syntax and methods for various capabilities.

### 6.3.1 Basics RegEx Syntax

## 6.4 RegEx Expanded
## 6.5 Convenient RegEx
### 6.5.1 Greediness
## 6.6 Regex in Python and Pandas(RegEx Groups)
### 6.6.1 Canonicalization
### 6.6.2 Extraction
### 6.6.3 Regular Expression Capture Groups
## 6.7 Limitations of Regular Expressions
Writing regular expression is like writing a program.
   * Need  to know the syntax well.
   * Can be easier to write than to read.
   * Can be difficult to debug.

Regular expressions are terrible at certain types of problems:

   * For parsing a hierarchical structure, such as JSON, use the ``json.load()`` parser, not RegEx!
   * Complex features (e.g. valid email address).
   * Counting (same number of instances of a and b). (impossible)
   * Complex properties (palindromes, balanced parentheses). (impossible)

Ultimately, the goal is not to memorize all regular expressions. Rather, the aim is to:

   * Understand what RegEx is capable of.
   * Parse and create RegEx, with a reference table
   * Use vocabulary (metacharacter, escape character, groups, etc.) to describe regex metacharacters
   * Differentiate between (), [], {}
   * Design your own character classes with , , […-…], ^, etc.
   * Use ``python`` and ``pandas`` RegEx methods.