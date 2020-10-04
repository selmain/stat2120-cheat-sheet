- [STAT 2120 Python Cheat Sheet](#stat-2120-python-cheat-sheet)
  - [Common Functions](#common-functions)
    - [Reading in datasets](#reading-in-datasets)
      - [CSV (.csv)](#csv-csv)
      - [Excel (.xls/.xlsx/etc.)](#excel-xlsxlsxetc)
    - [Printing](#printing)
    - [Sorting](#sorting)
    - [Rounding](#rounding)
    - [Numerical Summaries](#numerical-summaries)
      - [Summary](#summary)
      - [Sum](#sum)
      - [Minimum](#minimum)
      - [Maximum](#maximum)
      - [Quantile](#quantile)
      - [Mean](#mean)
      - [Median](#median)
      - [Standard Deviation](#standard-deviation)
      - [Ceiling/Floor](#ceilingfloor)
  - [Probability and Distributions](#probability-and-distributions)
    - [Random Numbers](#random-numbers)
      - [Set Seed](#set-seed)
      - [Random Integer](#random-integer)
      - [Random Float (Real Number/Decimals)](#random-float-real-numberdecimals)
      - [Random Collection from List](#random-collection-from-list)
    - [Binomial Distribution](#binomial-distribution)
      - [Specific Number of Successes (PMF)](#specific-number-of-successes-pmf)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf)
    - [Poisson Distribution](#poisson-distribution)
      - [Specific Number of Successes (PMF)](#specific-number-of-successes-pmf-1)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf-1)
    - [Normal Distribution](#normal-distribution)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf-2)
      - [Z score for a specified cumulative probability (PPF)](#z-score-for-a-specified-cumulative-probability-ppf)
    - [T Distribution](#t-distribution)
      - [Cumulative Probability (CDF)](#cumulative-probability-cdf-3)
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
    - [Drop/Remove Value](#dropremove-value)
  - [Plotting](#plotting)
    - [Bar graph](#bar-graph)
      - [Frequency (Counts)](#frequency-counts)
      - [Proportions/Means/etc.](#proportionsmeansetc)
    - [Box plot](#box-plot)
    - [Histogram](#histogram)
    - [Scatterplot](#scatterplot)
      - [With regression line](#with-regression-line)
    - [Residual Plot](#residual-plot)
    - [Labels and Axis](#labels-and-axis)
      - [Title](#title)
      - [X-axis/Y-axis label](#x-axisy-axis-label)
      - [Axis cutoffs](#axis-cutoffs)
  - [Hypothesis Testing and Confidence Intervals](#hypothesis-testing-and-confidence-intervals)
    - [Z-tests](#z-tests)
      - [Confidence Interval](#confidence-interval)
    - [Student t-tests](#student-t-tests)
      - [Single Sample](#single-sample)
      - [Two Sample](#two-sample)
      - [Paired](#paired)
      - [Confidence Interval](#confidence-interval-1)
  - [Regression](#regression)
    - [Fit a model](#fit-a-model)
    - [Show Model](#show-model)
    - [Predict using the model](#predict-using-the-model)
    - [Linear Regression / Ordinary Least Squares](#linear-regression--ordinary-least-squares)
      - [Adding a constant](#adding-a-constant)
      - [Simple Linear Regression](#simple-linear-regression)
      - [Multiple Linear Regression](#multiple-linear-regression)
    - [Testing and Assessment](#testing-and-assessment)
      - [t-test for slope](#t-test-for-slope)
      - [(ANOVA) Global F-Test](#anova-global-f-test)
      - [R-Squared](#r-squared)
      - [Adjusted R-Squared](#adjusted-r-squared)
  - [Additional Documentation](#additional-documentation)

# STAT 2120 Python Cheat Sheet

*Disclaimer: Variables `data`, `dataset`, etc. refer to your own array or dataframe containing the data you wish to analyse, not some external package or function. Change the variable name to the variable you're interested in intearcting with.*

---

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

Replace `filepath` with the filepath to the dataset. Make sure to keep the `r` in front of the string - this is a special type of strings that will not use special characters and thus will read your entire file path literally (this prevents a lot of filepath issues).

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
Values can be sorted by multiple columns (provide an array). If you wish to sort in the descending order, include the optional `ascending = False` argument.

### Rounding
```python
round(value, 3)
```
The second argument is the amount of decimal digits. 

### Numerical Summaries

#### Summary
```python
data.describe()
```
Provides basic summaries for each column (5 number summary, mean, standard deviation))

#### Sum
```python
np.sum(data)
```
* `data`: Column or array
#### Minimum
```python
np.min(data)
```
* `data`: Column or array
#### Maximum
```python
np.max(data)
```
* `data`: Column or array
#### Quantile
```python
np.quantile(data, .25)
```
* `data`: Column or array
The second argument is the quantile you wish to calculate (between 0 and 1). Example: 25th quantile is .25, etc.
#### Mean
```python
np.mean(data)
```
* `data`: Column or array
#### Median
```python
np.median(data)
```
* `data`: Column or array
#### Standard Deviation
```python
np.std(data)
```
* `data`: Column or array

You may also specify degrees of freedom with the `ddof` argument. 
#### Ceiling/Floor
Ceiling (rounding up)
```python
np.ceil(number)
```
Floor (rounding down)
```python
np.floor(number)
```

---

## Probability and Distributions

### Random Numbers

#### Set Seed
You may wish to set a certain seed in order to have replicable results. 
```python
random.seed(seed)
```
* `seed`: Seed

Note that the seed resets after a random function runs. You will need to set the seed **after each random operation** if you wish to have the same exact results throughout the script.

This is generally not required in this course, but may be essential for group work and communication.

#### Random Integer
The following are equivalent; `randint()` is an inclusive version of `randrange`. Of course, the `+1` at the end of randint isn't required.
```python
# randrange() [non-inclusive end]
random.randrange(a, b)
# randint() [inclusive end]
random.randint(a, b+1)
```
* `a`: Start of range
* `b`: End of range

#### Random Float (Real Number/Decimals)
* `random.random()`: A random float (a number with decimals) between 0 and 1.
* `random.uniform(a, b)`: A random float (a number with decimals) between a and b (inclusive)
```python
# 0 <= x <= 1
random.random()
# a <= x <= b
random.uniform(a,b)
```

#### Random Collection from List
```python
# Single Choice
random.choice(data)
# Multiple choices (list)
random.choices(data, k=n)
```
* `data`: Sample space list
* `n`: Number of trials

### Binomial Distribution
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/binom.png)
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
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/poisson.png)
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
![credit to Matt Bognar (U. of Iowa) for Normal Dist Applet (https://homepage.divms.uiowa.edu/~mbognar/applets/normal.html)](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/normal.png)
#### Cumulative Probability (CDF)
(Red Area in the above image)
```python
stats.norm.cdf(z)
```
* **z**: Upper bound for z-score (*P(Z less than or equal z)*)
#### Z score for a specified cumulative probability (PPF)
(Blue line in the above image)
```python
stats.norm.ppf(percentile)
```
* **percentile**: Cumulative probability/percentile (0-1). Useful for finding confidence intervals and critical values (e.g. Upper limit of a 95% CI is .975)

### T Distribution
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/t_df99.png)
#### Cumulative Probability (CDF)
```python
stats.t.cdf(t)
```
* **t**: Upper bound for t-score
#### Z score for a specified percentile (PPF)
```python
stats.t.ppf(percentile, df = 3)
```
* **percentile**: Percentile (0-1). Useful for finding confidence intervals (e.g. Upper limit of a 95% CI is .975)
* **df**: Degrees of freedom (make sure to explicitly define this argument, e.g. `df = 3`)

---

## Subsetting, Filtering, and Selecting

### Selecting rows/values
> Python indexing starts at 0, not 1. If you wish to select the first value of a array/dataset, use 0, etc. 
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
You may also select multiple columns at once with an array:

```python
data[['Column1', 'Column2']]
```

### Selecting rows and columns
> In Python, the format for datatable subsets is `[rows, columns]`. 

You may use any of the previously seen techniques to subset multiple rows/columns.

#### Using column names (loc)
```python
data.loc[0:5, 'Column']
```
> `loc` indeces are inclusive. In this case, this would include rows 0 through 5, not 0 through 4.

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

The `or` operator is a logical OR. If more than one condition is met, `or` will still select the row. 

### Drop/Remove Value
```python
pd.drop(i)
```
* `i`: Index or label of the value. 

If you wish to drop more than one value, use the selection methods listed in this section.

---

## Plotting

For all of the examples below, replace `dataset`, `x_column`, `y_column`, `column` etc. with your own variables.

The images below show the default for each one using the OSU Beer BAC Study data.

### Bar graph
#### Frequency (Counts)
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/countplot.png)
```python
sns.countplot(data = dataset, x = 'x_column')
```
Useful optional arguments:
* `orient` - Orientation of the plot (`v` for vertical, `h` for horizontal)

#### Proportions/Means/etc.
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/barplot.png)
```python
sns.barplot(data = dataset, x = 'x_column', y = 'y_column')
```
Usful optional arguments:
* `order`: Order of the bars (accepts a list of column name strings)
* `estimator`: Statistical function for the bin height; `np.mean` by default
* `ci`: Confidence Interval size (0-100). Use `None` if you want to remove the CI.
* `orient`: Orientation of the plot (`v` for vertical, `h` for horizontal)

### Box plot
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/boxplot.png)
```python
sns.boxplot(data = dataset, y = 'y_column')
```
Useful optional arguments:
* **`x`: x-axis column. You may plot multiple boxplots for various levels of a categorical variable using this argument.**
* `orient`: Orientation of the plot (`v` for vertical, `h` for horizontal)
* `order`: Order of the boxplots (list of column names)

### Histogram
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/histogram.png)
```python
sns.distplot(dataset.Column)
```
Useful optional arguments:
* `bins` - # of bins
* `kde` - **Density curve (you will generally want to set this to `False`)**
* `norm_hist` - Show density instead of count / Normalize histogram (`True`/`False`)

### Scatterplot
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/scatterplot.png)
```python
sns.scatterplot(data = dataset, x = 'x_column', y = 'y_column')
```
Useful optional arguments:
* `hue`:  Point color by variable (Categorical Variable)
* `style` - Point graphic by variable (Categorical variable)

#### With regression line
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/regplot.png)
```python
sns.regplot(data = dataset, x = 'x_column', y = 'y_column')
```
Useful optional arguments:
* `ci` - Confidence interval size (0-100 or `None` for no CI)
* `scatter` - Plot scatterplot (`False` to disable the scatterplot)

### Residual Plot
![](https://raw.githubusercontent.com/selmain/stat2120-cheat-sheet/master/img/residualplot.png)
```python
sns.residplot(data = dataset, x = 'x_column', y = 'y_column')
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

---

## Hypothesis Testing and Confidence Intervals

**Disclaimer**: You will often be asked to conduct each step of testing without using external testing functions like the ones listed below. **Do not use these functions if you're asked to run these tests by hand.**

### Z-tests

See the lecture scripts for One Sample, Two Sample, One Proportion, Two Proportion, and Paired z tests.

#### Confidence Interval
```python
stats.norm.interval(cl, loc, scale)
```
* `cl`: Confidence level (1 - alpha)
* `loc`: Mean
* `scale`: Standard Deviation of the **mean**

### Student t-tests

#### Single Sample
```python
stats.ttest_1samp(data.Column, exp_mean)
```
* `data.Column`: Sample column/array you're interested in testing
* `exp_mean`: expected mean of the sample for the null hypothesis

#### Two Sample
```python
stats.ttest_ind(data.Column1, data.Column2) 
```
* `data.Column1`, `data.ample_standard_errorColumn2`: Columns/arrays for samples

Returns a t statistic and a p value for a two-tailed test.
#### Paired
```python
stats.ttest_rel(data.Column1, data.Column2)
```
* `data.Column1`, `data.Column2`: Columns/arrays for samples

Returns a t statistic and a p value for a two tailed test.
#### Confidence Interval
```python
stats.t.interval(cl, df, loc, scale)
```
* `cl`: Confidence level (1 - alpha)
* `df`: Degrees of freedom
* `loc`: Sample mean
* `scale`: Sample standard error

---

## Regression
`model` refers to the model you're trying to fit, not to a package. Change the variable name as needed.

### Fit a model
```python
model.fit()
```
Model must be an object created from earlier model creation process (e.g. `sm.OLS()` process). Make sure to save the model by assigning it to a variable.

> Tip: Run the model creation and fitting process into one line (e.g. `sm.OLS(y, X).fit()`). This eliminates any confusion that might arise from assigning each step to a variable.

### Show Model
All models fitted with the `scipy` package are saved as model objects.
To examine those models, run this method on your model object:
```python
model.summary()
```
This summary (when used on Linear Regression models) shows least square line slope estimates, 95% CI for slopes, and various testing results (ANOVA F-test, R^2/Adjusted R^2, T-test for individual slopes).

### Predict using the model
```python
model.predict(X)
```
* `X`: Predictor **column(s)**. 

### Linear Regression / Ordinary Least Squares

#### Adding a constant
```python
X = model.add_constant(X)
```
* `X`: Predictor variable(s)

#### Simple Linear Regression
```python
sm.OLS(y, X)
```
* `y`: Dependent variable column/array
* `X`: Predictor variable column. Don't forget to [add a constant](#adding-a-constant)!

#### Multiple Linear Regression
```python
sm.OLS(y, X)
```
* `y`: Dependent variable column/array
* `X`: Predictor variable **columns**. Don't forget to [add a constant](#adding-a-constant)!

The function/process is the same for SLR and MLR. However, if you're interested in MLR, `X` must contain multiple columns.

### Testing and Assessment

#### t-test for slope
See [Model Summary](#show-model)

#### (ANOVA) Global F-Test

See [Model Summary](#show-model)

#### R-Squared
```python
model.rsquared
```
Also see [Model Summary](#show-model)

#### Adjusted R-Squared
```python
model.rsquared_adj
```
Also see [Model Summary](#show-model)

---

## Additional Documentation
* NumPy: https://numpy.org/doc/
* Pandas: https://pandas.pydata.org/docs/reference/index.html#api
* Scipy (Stats): https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html
* Seaborn: https://seaborn.pydata.org/api.html
* Statsmodels: https://www.statsmodels.org/stable/api.html
* random: https://docs.python.org/3/library/random.html