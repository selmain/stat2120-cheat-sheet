- [STAT 2120 Python Cheat Sheet](#stat-2120-python-cheat-sheet)
  - [Common Functions](#common-functions)
    - [Reading in datasets](#reading-in-datasets)
      - [CSV (.csv)](#csv-csv)
      - [Excel (.xls/.xlsx/etc.)](#excel-xlsxlsxetc)
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
 `==` | Equal ($=$) |
 `!=` | Not Equal ($\neq$)|
 `<` | Less than ($<$) |
 `>` | Greater than ($>$) |
 `<=` | Less than or equal ($\leq$) |
 `>=` | Greater than or equal ($\geq$) |

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

