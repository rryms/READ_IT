just_learn_it, and have a quickly review
**the offical reading**[Computational and Inferential Thinking](https://inferentialthinking.com/chapters/intro)

[TOC]

## Lec07 Charts
**Visualizing Relationships Between Numerical Attributes**
In Data Science we use visualization 
1. **For others** - to communicate our findings
2. **For ourselves** – to understand our data, see patterns, and discover relationships 

### Attribute Types
anlysis the items composed the chart

All values in a column of a table should be both the same type and be comparable to each other in some way
* Numerical — Each value is from a numerical scale
  * Numerical measurements are ordered
  * Differences are meaningful
* Categorical — Each value is from a fixed inventory
  * May or may not have an ordering
  * Categories are the same or different

#### Plotting Two Numerical Attribute
**Line plot**: plot
**Scatter plot**:scatter
***Line vs Scatter Plot***
* **t.plot(x_label, y_label)**
* **t.scatter(x_label, y_label)**

### Visualizing the Relationship Between Cateorical and Numerical Variables

**Line plot**:bar
**Scatter plot**:barh
table.barh(the label of the categories, the label of the frequencies)

### Visualization Fundamentals
The Visual Display of Quantitative Information 


## Lec8 Histograms

### Terminology
* **Individual**: entity whose attributes are recorded (row)
* **Variable**: an attribute (column)
  * can be **numerical** or **categorical**
  * has a set of values
    * real numbers, colors, strings
  * each **individual** has **exactly one value**
  * has a **distribution**: 
    * For each different value of the variable, the frequency of individuals that have that value
* **A Distribution**
--- Each individual is in exactly one category. Percents add to 100.

### Categorical Distributions,Numeriacl Distributions

#### Use ***Bar Charts*** for ***Categorical*** Distribution
To display all the values of the variable along with all their frequencies 
* Bar chart 
  * One bar for each category
  * You can choose the order of the bars
  * Length of bar is the percent (or count) of individuals in that category
  * Bar widths should all be the same.
  * Space between bars (not connected)

#### Grouping Numerical Values: Binning
Binning is counting the number of numerical values that lie within ranges, called bins.
* Bins are defined by their lower bounds (inclusive)
* The upper bound is the lower bound of the next bin

### Drawing Histograms
***Histogram***
* Displays the distribution of a numerical variable
* One bar corresponding to each bin
* Uses the area principle:
  * The **area** of each bar is the **percent** of individuals in the corresponding bin

#### Density
***Histogram Axes***
* By default, **hist** uses a scale (**normed=True**) that ensures the area of the chart sums to 100%
* The **area** of each bar is a percentage of the whole
* The horizontal axis is a number line (e.g. years), and the bins sizes don’t have to be equal to each other
* The vertical axis is a rate (e.g., percent per year)
* The height measures the percent of data in the bin **relative to the amount of space in the bin**.
* Height measures crowdedness, or **density**.
* Units: percent per unit on the horizontal axis
#### Bar Chart or Histogram
* Bar Chart
  * Distribution of categorical variable
  * Bars have arbitrary (but equal) widths and spacings; in any order
  * height (or length) and area of bars proportional to the percent of individuals
* Histogram
  * Distribution of numerical variable
  * Horizontal axis is numerical: drawn to scale, no gaps, bins can be unequal
  * Area of bars proportional to the percent of individuals; height measures density
