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
    * ***Observation***: The JSON dictionary contains a meta key which likely refers to metadata (data about the data). Metadata is often maintained with the data and can be a good source of additional information.
  EDA with JSON, File Size, Unix Commands, File Contents
  1. The above **metadata** tells us a lot about the columns in the data including column names, potential data anomalies, and a basic statistic.
  2. Because of its non-tabular structure, JSON makes it easier (than CSV) to create **self-documenting** data, meaning that information about the data is stored in the same file as the data.
  3. Self-documenting data can be helpful since it maintains its own description and these descriptions are more likely to be updated as data changes.

### 5.1.2 Primary and Foreign keys
use the ``.merge`` as the ``pandas`` method for joining multiple ``DataFrame``s together through the usage of key;
The ***primary key*** is the column or set of columns in a table that uniquely determine the values of the remaining columns. 
The ***foreign key*** is the column or set of columns in a table that reference primary keys in other tables.

### 5.1.3 Variable Types
***Quantitative variables*** describe some numeric quantity or amount. We can divide quantitative data further into:

  * **Continuous quantitative variables**: numeric data that can be measured on a continuous scale to arbitrary precision.
  * **Discrete quantitative** variables: numeric data that can only take on a finite set of possible values. 

***Qualitative variables***, also known as ***categorical variables***, describe data that isn’t measuring some quantity or amount. The sub-categories of categorical data are:
  * **Ordinal qualitative variables**: categories with ordered levels. 
  * **Nominal qualitative variables**: categories with no specific order. 
## 5.2 Granularity, Scope, and Temporality
### 5.2.1 Granularity
The granularity of a dataset is what a single row represents. 
1. Fine-grained data contains a high level of detail
2. Coarse-grained data is encoded such that single row represents a large indivdual unit

### 5.2.2 Scope
The scope of a dataset is the subset of the population covered by the data.

### 5.2.3 Temporality
The temporality of a dataset describes the periodicity over which the data was collected as well as when the data was most recently collected or updated.

## 5.3 Faithfulness
### Missing Data/Default Values: Solutions
1. **Drop records** with missing values
   * Probably most common
   * **Caution**: check for biases induced by dropped values
     * Missing or corrupt records might be related to something of interest
2. **Keep as ***NaN*****
3. **Imputation/Interpolation**: Inferring missing values
   * **Average Imputation**: replace with an average value 
     * Often use closet related subgroup mean.
   * **Hot deck imputation**: replace with a random value
   * **Regression imputation**: replace with a prediceed value, using some model
   * **Multiple imputation**: replace with multiple random values.
   * 

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
The following table includes a number of string operations supported by Python and ``pandas``. The Python functions operate on a single string, while their equivalent in ``pandas`` are **vectorized** — they operate on a ``Series`` of string data.
[difference](https://ds100.org/course-notes/regex/regex.html#python-string-methods)

1. Python’s built-in functions limit us to extract data one record at a time,
   * This can be resolved using the **map** function or **pandas** **Series** methods.
2. The code is quite verbose.
   * This is a larger issue that is trickier to solve
### 6.2.1 Canonicalization
to manage the message into a normal form.
### 6.2.2 Extraction
Extraction explores the idea of obtaining useful information from text data. 

## 6.3 RegEx Basics

A **regular expression("RegEx")** is a sequence of characters that specifies a search pattern. They are written to extract specific information from text. Regular expressions are essentially part of a smaller programming language embedded in Python, made available through the ``re`` module. As such, they have a stand-alone syntax and methods for various capabilities.

### 6.3.1 Basics RegEx Syntax
[basic operations](https://ds100.org/course-notes/regex/regex.html#basics-regex-syntax)
## 6.4 RegEx Expanded
[complex regular expression](https://ds100.org/course-notes/regex/regex.html#regex-expanded)
## 6.5 Convenient RegEx
[more convenient regular expressions](https://ds100.org/course-notes/regex/regex.html#convenient-regex)
### 6.5.1 Greediness
``<div>.*?</div>``
## 6.6 Regex in Python and Pandas(RegEx Groups)
### 6.6.1 Canonicalization
``re.sub(pattern, rep1, text)``
Notice the ``r`` preceding the regular expression pattern; this specifies the regular expression is a raw string. Raw strings do not recognize escape sequences. This makes them useful for regular expressions, which often contain literal ``\`` characters.
### 6.6.2 Extraction
the ``re`` module provides capability to extract relevant text from a string:
``re.findall(pattern, text)``. This function returns a list of all matches to ``pattern``.
### 6.6.3 Regular Expression Capture Groups
Earlier we used parentheses ``(`` ``)`` to specify the highest order of operation in regular expressions. However, they have another meaning; parentheses are often used to represent **capture groups**. Capture groups are essentially, a set of smaller regular expressions that match multiple substrings in text data.
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

# Lecture7 Visualization I
[note](https://ds100.org/course-notes/visualization_1/visualization_1.html)
***Learning Outcomes***
* Understand the theories behind effective visualizations and start to generate plots of our own with ``matplotlib`` and ``seaborn``.
* Analyze histograms and identify the skewness, potential outliers, and the mode
* Use ``boxplot`` and ``violinplot`` to compare two distributions.

## 7.1 Visualizations in Data 8 and Data 100 (so far)
## 7.2 Goals of Visualization
Visualizations are useful for a number of reasons. In Data 100, we consider two areas in particular:
1. To broaden your understanding of the data. Summarizing trends visually before in-depth analysis is a key part of exploratory data analysis. Creating these graphs is a lightweight, iterative and flexible process that helps us investigate relationships between variables.
2. To communicate results/conclusions to others. These visualizations are highly editorial, selective, and fine-tuned to achieve a communications goal, so be thoughtful and careful about its clarity, accessibility, and necessary context.
## 7.3 An Overview of Distributions
Distributions must satisfy two properties:
1. The total frequency of all categories must sum to 100%
2. Total count should sum to the total number of datapoints if we’re using raw counts.
## 7.4 Variable Types Should Inform Plot Choice
Different plots are more or less suited for displaying particular types of variables:
* Variables
    * Quantitive
       * Continuous
       * Discrete
    * Qualitative
       * Ordinal
       * Nominal 
## 7.5 Qualitative Variables: Bar Plots
* Plotting in Pandas
* Plotting in Matplotlib
* Plotting in Seabron

## 7.6 Distributions of Quantitative Variables
What is Continuous Quantitive Variables? 先天的连续性；后天的定义；
To visualize the distribution of a continuous variable, we use:
* Histogram
* Box plot
* Violin plot

### Box Plots and Violin Plots
Using information about **quartiles**
A quartile represents a 25% portion of the data. We say that:

* The first quartile (Q1) represents the 25th percentile – 25% of the data is smaller than or equal to the first quartile.
* The second quartile (Q2) represents the 50th percentile, also known as the median – 50% of the data is smaller than or equal to the second quartile.
* The third quartile (Q3) represents the 75th percentile – 75% of the data is smaller than or equal to the third quartile.
  
Interquartile range(IQR) = third quaritile - first quaritile


# Lecture8 Visualization II
[note](https://ds100.org/course-notes/visualization_2/visualization_2.html)

***Learning Outcomes***
* Understanding KDE for plotting distributions and estimating density curves.
* Using transformations to analyze the relationship between two variables.
* Evaluating the quality of a visualization based on visualization theory concepts.
