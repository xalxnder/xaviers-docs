Pandas is a python data analysis tool.  The two fundamental data structures in pandas are series and dataframes.


# Series
[`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series") is a one-dimensional labeled array capable of holding any data type (integers, strings, floating point numbers, Python objects, etc.). The axis labels are collectively referred to as the **index**. The basic method to create a [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series") is to call: Here, `data` can be many different things. dict, ndarray, a scalar value (like 5)

The passed **index** is a list of axis labels. Thus, this separates into a few cases depending on what **data is**. This example the data is ndarray

```python
>>> s = pd.Series(np.random.randn(5), index=["a", "b", "c", "d", "e"])
>>> s
a   -0.815774
b   -0.369123
c   -0.290913
d   -1.284814
e    2.119353
```

#### Dictionary
```python
>>> d = {"b": 1, "a": 0, "c": 2}
>>> pd.Series(d)
b    1
a    0
c    2
```
# Dataframes
[`DataFrame`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame") is a 2-dimensional labeled data structure with columns of potentially different types. You can think of it like a spreadsheet or SQL table, or a dict of Series objects. It is generally the most commonly used pandas object. Along with the data, you can optionally pass **index** (row labels) and **columns** (column labels) arguments. If you pass an index and / or columns, you are guaranteeing the index and / or columns of the resulting DataFrame. Thus, a dict of Series plus a specific index will discard all data not matching up to the passed index.  Like Series, DataFrame accepts many different kinds of input:
-   Dict of 1D ndarrays, lists, dicts, or [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series")
-   2-D numpy.ndarray
-   [Structured or record](https://numpy.org/doc/stable/user/basics.rec.html) ndarray
-   A [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series")
-   Another [`DataFrame`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame")

 It may be helpful to think of the Pandas DataFrame as a dictionary of columns, or Pandas Series, with many additional features.
```python
>>> data = {
...     'name': ['Xavier', 'Ann', 'Jana', 'Yi', 'Robin', 'Amal', 'Nori'],
...     'city': ['Mexico City', 'Toronto', 'Prague', 'Shanghai',
...              'Manchester', 'Cairo', 'Osaka'],
...     'age': [41, 28, 33, 34, 38, 31, 37],
...     'py-score': [88.0, 79.0, 81.0, 80.0, 68.0, 61.0, 84.0]
... }
>>> row_labels = [101, 102, 103, 104, 105, 106, 107]
>>> df = pd.DataFrame(data=data, index=row_labels)
>>> df
       name         city  age  py-score
101  Xavier  Mexico City   41      88.0
102     Ann      Toronto   28      79.0
103    Jana       Prague   33      81.0
104      Yi     Shanghai   34      80.0
105   Robin   Manchester   38      68.0
106    Amal        Cairo   31      61.0
107    Nori        Osaka   37      84.0
```


Another example:
```python

```