- [STAT 2120 Python Cheat Sheet](#stat-2120-python-cheat-sheet)
  - [Common Functions](#common-functions)
    - [Reading in datasets](#reading-in-datasets)
      - [CSV (.csv)](#csv-csv)
      - [Excel (.xls/.xlsx/etc.)](#excel-xlsxlsxetc)
    - [Printing](#printing)
    - [Sorting](#sorting)
    - [Rounding](#rounding)
    - [Numerical Summaries](#numerical-summaries)
      - [Sum](#sum)
      - [Minimum](#minimum)
      - [Maximum](#maximum)
      - [Quantile](#quantile)
      - [Mean](#mean)
      - [Median](#median)
      - [Standard Deviation](#standard-deviation)
  - [Probability and Distributions](#probability-and-distributions)
    - [Binomial Distribution](#binomial-distribution)
      - [Specific Number of Successes (PMF)](#specific-number-of-successes-pmf)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf)
    - [Poisson Distribution](#poisson-distribution)
      - [Specific Number of Successes (PMF)](#specific-number-of-successes-pmf-1)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf-1)
    - [Normal Distribution](#normal-distribution)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf-2)
      - [Z score for a specified percentile (PPF)](#z-score-for-a-specified-percentile-ppf)
  - [Subsetting, Filtering, and Selecting](#subsetting-filtering-and-selecting)
    - [Selecting rows/values](#selecting-rowsvalues)
      - [One value](#one-value)
      - [Multiple values](#multiple-values)
    - [Selecting columns](#selecting-columns)
      - [One Column](#one-column)
      - [Multiple columns](#multiple-columns)
    - [Selecting rows and columns](#selecting-rows-and-columns)
      - [Using column names (loc)](#using-column-names-loc)
      - [Using column index (iloc)](#using-column-index-iloc)
    - [Selecting using a criteria](#selecting-using-a-criteria)
  - [Plotting](#plotting)
    - [Bar graph](#bar-graph)
      - [Frequency (Counts)](#frequency-counts)
      - [Proportions](#proportions)
    - [Box plot](#box-plot)
    - [Histogram](#histogram)
    - [Scatterplot](#scatterplot)
      - [With regression line](#with-regression-line)
    - [Residual Plot](#residual-plot)
    - [Labels and Axis](#labels-and-axis)
      - [Title](#title)
      - [X-axis/Y-axis label](#x-axisy-axis-label)
      - [Axis cutoffs](#axis-cutoffs)

# STAT 2120 Python Cheat Sheet

*Disclaimer: Variables `data` or `dataset` refer to your own list or dataframe containing the data you wish to analyse, not some external package or function.*

## Common Functions

### Reading in datasets
#### CSV (.csv)
```python
pd.read_csv(r"filepath")
```
#### Excel (.xls/.xlsx/etc.)
```python
pd.read_excel(r"filepath")
```

Replace `filepath` with the filepath to the dataset. 

### Printing
```python
print("text")
```

**Tip**: You will often print statements with non-text variables mixed in with the text in this course. In order to simplify the task, try f-strings:

```python
answer = 41
# The f-string way
print(f"The answer is {answer}")
# The regular way
print("The answer is " + str(answer))
```

### Sorting
```python
data.sort_values(by = 'column')
```
Values can be sorted by multiple columns (provide a list). If you wish to sort in the descending order, include the optional `ascending = False` argument.

### Rounding
```python
round(value, 3)
```
The second argument is the amount of decimal digits. 

### Numerical Summaries

#### Sum
```python
np.sum(data)
```
#### Minimum
```python
np.min(data)
```
#### Maximum
```python
np.max(data)
```
#### Quantile
```python
np.quantile(data, .25)
```
The second argument is the quantile you wish to calculate (between 0 and 1). Example: 25th quantile is .25, etc.
#### Mean
```python
np.mean(data)
```
#### Median
```python
np.median(data)
```
#### Standard Deviation
```python
np.std(data)
```
You may also specify degrees of freedom with the `ddof` argument. 


## Probability and Distributions

### Binomial Distribution
#### Specific Number of Successes (PMF)
```python
stats.binom.pmf(k, n, p)
```
* **k**: Number of successes
* **n**: Number of trials
* **p**: Probability of success
#### Cumulative Probability (CDF)
```python
stats.binom.cdf(k, n, p)
```
* **k**: Upper limit (*P(X less than or equal k)*)
* **n**: Number of trials
* **p**: Probability of success

### Poisson Distribution
#### Specific Number of Successes (PMF)
```python
stats.poisson.pmf(k, mu)
```
* **k**: Number of successes
* **mu**: Mean number of successes
#### Cumulative Probability (CDF)
```python
stats.poisson.cdf(k, mu)
```
* **k**: Upper limit (*P(X less than or equal k)*)
* **mu**: Mean number of successes

### Normal Distribution
#### Cumulative Probability (CDF)
```python
stats.norm.cdf(z)
```
* **z**: Upper bound for z-score (*P(Z less than or equal z)*)
#### Z score for a specified percentile (PPF)
```python
stats.norm.pmf(percentile)
```
* **percentile**: Percentile (0-1). Useful for finding confidence intervals (e.g. Upper limit of a 95% CI is .975)


## Subsetting, Filtering, and Selecting

### Selecting rows/values
> Python indexing starts at 0, not 1. If you wish to select the first value of a list/dataset, use 0, etc. 
#### One value
```python
data[5]
```

#### Multiple values
```python
data[[0,1,2,3,4]]
```

or 

```python
data[0:5]
```
The lower limit is inclusive, the upper limit is **not** inclusive.

You may leave either the lower bound or the upper bound blank in order to select from the start/through the end.

### Selecting columns

#### One Column
```python
data['Column']
```

or

```python
data.Column
```

#### Multiple columns
You may also select multiple columns at once with a list:

```python
data[['Column1', 'Column2']]
```

### Selecting rows and columns
> The format for subsetting in datasets is `[rows, columns]`. 

You may use any of the previously seen techniques to subset multiple rows/columns.

#### Using column names (loc)
```python
data.loc[0:5, 'Column']
```
> `loc` indexes are inclusive. In this case, this would include rows 1 through 6, not 1 through 5.

#### Using column index (iloc)
```python
data.iloc[0:5, 1]
```

### Selecting using a criteria
```python
data[data.Column == 5]
```

The following operators can be used to set the criteria for both categorical and numerical variables:

Operator | Usage | 
---------|----------|
 `==` | Equal|
 `!=` | Not Equal|
 `<` | Less than |
 `>` | Greater than|
 `<=` | Less than or equal|
 `>=` | Greater than or equal|

 You may also have multiple conditions with `and` and `or` operators.

The `or` operator is a logical OR. If two or more conditions are met, `or` will still select them. 

## Plotting

For all of the examples below, replace `dataset`, `x_column`, `y_column`, `column` etc. with your own variables.

### Bar graph
#### Frequency (Counts)
```python
sns.countplot(data = dataset, x = 'x_column')
```
#### Proportions
```python
sns.barplot(data = dataset, x = 'x_column', y = 'y_column')
```

### Box plot
```python
sns.boxplot(data = dataset, y = 'y_column')
```

### Histogram
```python
sns.distplot(dataset.Column)
```

### Scatterplot
```python
sns.scatterplot(data = dataset, x = 'x_column', y = 'y_column')
```
#### With regression line
```python
sns.regplot(data = dataset, x = 'x_column', y = 'y_column')
```
### Residual Plot
```python
sns.residplot(data = dataset, x = 'x_column', y = 'residuals')
```

### Labels and Axis
#### Title
```python
plt.title('Title')
```
#### X-axis/Y-axis label
X-axis:
```python
plt.xlabel('x axis')
```
Y-axis:
```python
plt.ylabel('y axis')
```
#### Axis cutoffs
X-axis:
```python
plt.xlim(0, 100)
```
Y-axis:
```python
plt.ylim(0,100)
```
Replace the values with your own lower/upper limits.

