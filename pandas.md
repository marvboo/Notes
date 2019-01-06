# Pandas simple examples

<br>

#### References:

[http://pandas.pydata.org/pandas-docs/stable/api.html](http://pandas.pydata.org/pandas-docs/stable/api.html)

<br>

----

####  [Creating a dataframe](#creating)
####  [View data](#view)
####  [Add/drop columns](#columns1)
####  [Rename columns](#columns2)
####  [Indexing](#index)
####  [Replace data](#replace)
####  [Add rows](#rows)
####  [Reindex](#reindexing)
####  [Sort](#sorting)
####  [Stats, rolling, one-hot encoding](#stats)
####  [Missing data / NaN](#nan)
####  [Duplicates](#dupes)
####  [Strings](#stringsexample)
####  [Applymap](#applymapexample)
####  [Dates](#datesexample)
####  [CSV](#csvexample)


----

hint: shift-tab inside function parens to get signature



```python
import pandas as pd
import numpy as np
```

<br>
<br>
<br>
<br>

----


#### <a id='creating'>Creating a dataframe</a>



```python
"""
create a dataframe from numpy array
"""

df = pd.DataFrame( np.random.rand(5,3)*20,
                   columns = list('ABC'),
                   dtype=int
                 )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>5</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15</td>
      <td>15</td>
      <td>18</td>
    </tr>
    <tr>
      <th>2</th>
      <td>19</td>
      <td>0</td>
      <td>17</td>
    </tr>
    <tr>
      <th>3</th>
      <td>13</td>
      <td>16</td>
      <td>18</td>
    </tr>
    <tr>
      <th>4</th>
      <td>16</td>
      <td>3</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
"""
create a dataframe from dict
"""
dataDict = { 'C': np.random.rand(4),
             'A': [2014, 2015, 2016, 2017],
             'B': [6,5,4,3]
           }
df = pd.DataFrame( dataDict, columns=list('ABC') )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.885506</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>5</td>
      <td>0.667120</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.954928</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.900649</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----

#### <a id='view'>View data</a>



```python
# default is 5 rows
df.head(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.885506</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>5</td>
      <td>0.667120</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.954928</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.900649</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2015.500000</td>
      <td>4.500000</td>
      <td>0.852051</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.290994</td>
      <td>1.290994</td>
      <td>0.126839</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2014.000000</td>
      <td>3.000000</td>
      <td>0.667120</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2014.750000</td>
      <td>3.750000</td>
      <td>0.830909</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2015.500000</td>
      <td>4.500000</td>
      <td>0.893077</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2016.250000</td>
      <td>5.250000</td>
      <td>0.914218</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2017.000000</td>
      <td>6.000000</td>
      <td>0.954928</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='columns1'>Add/drop columns</a>



```python
"""
Add columns (using Series, numpy, list comprehension)
"""
df['D'] = pd.Series([5.4, 2.3, 87.6, 19.2])
df['E'] = np.where(df['A']>=2016, 'ge2016', 'lt2016')
df['F'] = [row-1 for row in df['B']]

df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.885506</td>
      <td>5.4</td>
      <td>lt2016</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>5</td>
      <td>0.667120</td>
      <td>2.3</td>
      <td>lt2016</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.954928</td>
      <td>87.6</td>
      <td>ge2016</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.900649</td>
      <td>19.2</td>
      <td>ge2016</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
"""
Drop (delete) a column

axis=0 for rows
axis=1 for columns

note the reassignment since inplace is False by default
"""
df = df.drop('F', axis=1)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.885506</td>
      <td>5.4</td>
      <td>lt2016</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>5</td>
      <td>0.667120</td>
      <td>2.3</td>
      <td>lt2016</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.954928</td>
      <td>87.6</td>
      <td>ge2016</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.900649</td>
      <td>19.2</td>
      <td>ge2016</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[list('ACE')]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>C</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>0.885506</td>
      <td>lt2016</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>0.667120</td>
      <td>lt2016</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>0.954928</td>
      <td>ge2016</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>0.900649</td>
      <td>ge2016</td>
    </tr>
  </tbody>
</table>
</div>




```python
"""
Drop (delete) columns using a list

inplace option, no need for reassignment
"""
df.drop(['B', 'E'], axis=1, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>0.885506</td>
      <td>5.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>0.667120</td>
      <td>2.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>0.954928</td>
      <td>87.6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>0.900649</td>
      <td>19.2</td>
    </tr>
  </tbody>
</table>
</div>






```python
df = pd.DataFrame( np.random.rand(5,3)*20,
                   columns = list('ABC'),
                   dtype=int
                 )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
# a new column as a function of two columns

def diff_cols(col1, col2):    
    return col1 - col2

df['col_diff'] = diff_cols(df['B'], df['C'])

df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>col_diff</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>-3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>-4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.drop('col_diff', axis=1)
```


```python
# 2 new columns as a function of one column using map

def sub_1_2(c):
    return c-1, c-2

# unzip using zip(*)
df['M1'], df['M2'] = zip(*df['C'].map(sub_1_2))

df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>M1</th>
      <th>M2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
      <td>11</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='columns2'>Rename columns</a>



```python
"""
rename column headers
"""
df.columns = list('abcde')
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
      <td>11</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns = map(str.upper, df.columns)
```


```python
df.rename(columns={'C': 'Col_C'}, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
      <td>11</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='index'>Indexing</a>



```python
"""
loc    for label-based indexing


iloc   for integer indexing       can use slicing
        df.iloc[row, col]
        df.iloc[row]   is the same as df.iloc[row, :]


        df.iloc[:, col]   to select a column
        or df[col]

"""
```


```python
df.loc[:,['A', 'B']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[:, :2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[1:]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>14</td>
      <td>12</td>
      <td>11</td>
      <td>10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Col_C']
```




    0     3
    1    10
    2    12
    3    17
    4    18
    Name: Col_C, dtype: int32




```python
df[ ~df.index.isin([1,2]) ]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[(df.index < 1) | (df.index > 2) ]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df['A'] > 2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[~(df['A'] == 2)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[(df['A'] != 2)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>Col_C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16</td>
      <td>6</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>18</td>
      <td>10</td>
      <td>9</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>14</td>
      <td>17</td>
      <td>16</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>14</td>
      <td>18</td>
      <td>17</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>






```python
df = pd.DataFrame( np.random.rand(5,3)*20,
                   columns = list('ABC'),
                   dtype=int
                 )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>13</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>16</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>3</td>
      <td>13</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11</td>
      <td>8</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Where a value exists in a column
df['B'].where(df['B'] > 10)
```




    0    13.0
    1    16.0
    2     NaN
    3     NaN
    4     NaN
    Name: B, dtype: float64




```python
# Select rows with a value, using Series.map
df[df['C'].map(lambda colC: 13 == colC )]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>16</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>3</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
# for strings
df[df['C'].map(lambda colC: str(13) in str(colC) )]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>16</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>3</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
check_list = [0, 8]

# rows where column has certain values
df[df.A.isin(check_list)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>13</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>16</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>3</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[~df.A.isin(check_list)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11</td>
      <td>8</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
Bgt7 = df['B'] > 7
Clt10 = df['C'] < 10

df[Bgt7 & Clt10]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>13</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>






<br>
<br>
<br>
<br>

----

#### <a id='replace'>Replace data</a>



```python
"""
replace all occurences
"""

df.replace( [0, 11] , np.nan, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>13</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>16</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8.0</td>
      <td>3</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>8</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>8</td>
      <td>18.0</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='nan'>Missing data / NaN</a>



```python
df = pd.DataFrame( np.random.rand(5,3)*20,
                   columns = list('ABC'),
                   dtype=int
                 )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>18</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>7</td>
      <td>14</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>2</td>
      <td>15</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>19</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.replace( [3,] , np.nan, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>18</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>7</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>18</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5.0</td>
      <td>2</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>19</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.dropna(inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>7</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5.0</td>
      <td>2</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>19</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['missing'] = np.nan
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>missing</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>7</td>
      <td>14.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5.0</td>
      <td>2</td>
      <td>15.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>19</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# only drop column if all values are NaN
df.dropna(axis=1, how='all', inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>7</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5.0</td>
      <td>2</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>19</td>
      <td>4.0</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='rows'>Add rows</a>

#### <a id='reindexing'>Reindex</a>



```python
dataDict = { 'C': np.random.rand(4),
             'A': [2014, 2015, 2016, 2017],
             'B': [6,5,4,3]
           }
df = pd.DataFrame( dataDict, columns=list('ABC') )
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>5</td>
      <td>0.464464</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df[(df['A'] != 2015)]
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[1, :] = [2015, 7, 0.57]
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014.0</td>
      <td>6.0</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016.0</td>
      <td>4.0</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017.0</td>
      <td>3.0</td>
      <td>0.475800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015.0</td>
      <td>7.0</td>
      <td>0.570000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['A'] = df['A'].astype(int)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.0</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4.0</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.0</td>
      <td>0.475800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.0</td>
      <td>0.570000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.reindex(range(len(df)))
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.0</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.0</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>4.0</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.0</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[2, 1] = np.nan
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.0</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.0</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>NaN</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.0</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["B"].fillna(df["B"].mean(), inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.000000</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>5.333333</td>
      <td>0.341597</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.000000</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[2, 2] = np.nan
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.000000</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016</td>
      <td>5.333333</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.000000</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df['C'].notnull()]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014</td>
      <td>6.0</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7.0</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017</td>
      <td>3.0</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




<br>
<br>
<br>
<br>

----

#### <a id='dupes'>Duplicates</a>



```python
df = df.append(  df.iloc[1] , ignore_index=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014.0</td>
      <td>6.000000</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015.0</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016.0</td>
      <td>5.333333</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017.0</td>
      <td>3.000000</td>
      <td>0.475800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015.0</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.duplicated()
```




    0    False
    1    False
    2    False
    3    False
    4     True
    dtype: bool




```python
# keeping the 1st by default
df.drop_duplicates()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014.0</td>
      <td>6.000000</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015.0</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016.0</td>
      <td>5.333333</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017.0</td>
      <td>3.000000</td>
      <td>0.475800</td>
    </tr>
  </tbody>
</table>
</div>




```python
# only consider dupes in the B column, keep the last obs
df.drop_duplicates(['B'], keep='last')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014.0</td>
      <td>6.000000</td>
      <td>0.312876</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016.0</td>
      <td>5.333333</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017.0</td>
      <td>3.000000</td>
      <td>0.475800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015.0</td>
      <td>7.000000</td>
      <td>0.570000</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----


#### <a id='sorting'>Sort</a>



```python
df = pd.DataFrame( np.random.rand(5,3)*20,
                   columns = list('ABC'),
                   dtype=int
                 )
df.sort_values(by='C', ascending=0)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
    </tr>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# sort by A, then B in ascending order (for the same value in A)
df.sort_values(by=['A', 'B'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----


#### <a id='stats'>Stats</a>



```python
"""
dataframe stats functions

rank
sum
cumsum
mean
median
min
max
idxmax  (index of max)
var
std
skew
kurt
count (if not NaN)
corr
cov
describe

"""
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['C'].idxmin()
```




    0




```python
df.idxmin()
```




    A    0
    B    3
    C    0
    dtype: int64




```python
# rolling average window length of 2
df['A'].rolling(window=2).mean()
```




    0     NaN
    1    10.0
    2    10.5
    3     9.5
    4    13.0
    Name: A, dtype: float64




```python
df['A'].rolling(window=2).sum()
```




    0     NaN
    1    20.0
    2    21.0
    3    19.0
    4    26.0
    Name: A, dtype: float64




```python
"""
one hot encoding
"""
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
oneHot = pd.get_dummies(df['C'])
oneHot
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2</th>
      <th>4</th>
      <th>9</th>
      <th>13</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.join(oneHot)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>2</th>
      <th>4</th>
      <th>9</th>
      <th>13</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# same as the join above
pd.concat([df, oneHot], axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>2</th>
      <th>4</th>
      <th>9</th>
      <th>13</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>7</td>
      <td>2</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>17</td>
      <td>4</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>17</td>
      <td>9</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11</td>
      <td>4</td>
      <td>13</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15</td>
      <td>5</td>
      <td>9</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----


#### <a id='stringsexample'>Strings</a>



```python
data = {'stringCol': [ '2017-05-15 Monday',
                      '2017-05-16 Tuesday',
                      '2017-05-17 Wednesday',
                      '2017-05-18 Thursday',
                      '2017-05-19 Friday',         
       ]}
df = pd.DataFrame(data, columns = ['stringCol'])
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['stringCol'].str.contains('....-..-..', regex=True)
```




    0    True
    1    True
    2    True
    3    True
    4    True
    Name: stringCol, dtype: bool




```python
# series extract expand=True returns a dataframe
df['date'] = df['stringCol'].str.extract('(....-..-..)', expand=True)
```


```python
# regex match 1 or more words starting with a capital letter
#  http://regexr.com/ has a nice cheatsheet

df['day'] = df['stringCol'].str.extract('([A-Z]\w{0,})', expand=True)
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
      <td>2017-05-15</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
      <td>2017-05-16</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
      <td>2017-05-17</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
      <td>2017-05-18</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
      <td>2017-05-19</td>
      <td>Friday</td>
    </tr>
  </tbody>
</table>
</div>






```python
import string

df['lc'] = np.random.choice(list(string.ascii_lowercase), len(df))
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
      <th>lc</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
      <td>2017-05-15</td>
      <td>Monday</td>
      <td>b</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
      <td>2017-05-16</td>
      <td>Tuesday</td>
      <td>u</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
      <td>2017-05-17</td>
      <td>Wednesday</td>
      <td>r</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
      <td>2017-05-18</td>
      <td>Thursday</td>
      <td>s</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
      <td>2017-05-19</td>
      <td>Friday</td>
      <td>f</td>
    </tr>
  </tbody>
</table>
</div>




```python
# not using the ord() encoding here
lowercase2int = dict(zip(list(string.ascii_lowercase),range(len(string.ascii_lowercase))))
lowercase2int
```




    {'a': 0,
     'b': 1,
     'c': 2,
     'd': 3,
     'e': 4,
     'f': 5,
     'g': 6,
     'h': 7,
     'i': 8,
     'j': 9,
     'k': 10,
     'l': 11,
     'm': 12,
     'n': 13,
     'o': 14,
     'p': 15,
     'q': 16,
     'r': 17,
     's': 18,
     't': 19,
     'u': 20,
     'v': 21,
     'w': 22,
     'x': 23,
     'y': 24,
     'z': 25}




```python
# replace using dict lookup

df['lcInt'] = df['lc'].replace(lowercase2int)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
      <th>lc</th>
      <th>lcInt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
      <td>2017-05-15</td>
      <td>Monday</td>
      <td>b</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
      <td>2017-05-16</td>
      <td>Tuesday</td>
      <td>u</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
      <td>2017-05-17</td>
      <td>Wednesday</td>
      <td>r</td>
      <td>17</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
      <td>2017-05-18</td>
      <td>Thursday</td>
      <td>s</td>
      <td>18</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
      <td>2017-05-19</td>
      <td>Friday</td>
      <td>f</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# apply a function along dataframe axis (here to column 'lc')

toUpper = lambda x: x.upper()

df['lc'].apply(toUpper)
```




    0    B
    1    U
    2    R
    3    S
    4    F
    Name: lc, dtype: object




```python
# map function to each element of a series
df['lc'].map(toUpper)
```




    0    B
    1    U
    2    R
    3    S
    4    F
    Name: lc, dtype: object



<br>
<br>
<br>
<br>

----


#### <a id='applymapexample'>Applymap</a>



```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
      <th>lc</th>
      <th>lcInt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
      <td>2017-05-15</td>
      <td>Monday</td>
      <td>b</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
      <td>2017-05-16</td>
      <td>Tuesday</td>
      <td>u</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
      <td>2017-05-17</td>
      <td>Wednesday</td>
      <td>r</td>
      <td>17</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
      <td>2017-05-18</td>
      <td>Thursday</td>
      <td>s</td>
      <td>18</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
      <td>2017-05-19</td>
      <td>Friday</td>
      <td>f</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# applymap() applies a function to every element in the whole dataframe.

df.applymap(type)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
      <th>lc</th>
      <th>lcInt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'long'&gt;</td>
    </tr>
    <tr>
      <th>1</th>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'long'&gt;</td>
    </tr>
    <tr>
      <th>2</th>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'long'&gt;</td>
    </tr>
    <tr>
      <th>3</th>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'long'&gt;</td>
    </tr>
    <tr>
      <th>4</th>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'str'&gt;</td>
      <td>&lt;type 'long'&gt;</td>
    </tr>
  </tbody>
</table>
</div>




```python
def applySqrt(x):    
    if type(x) is str:        
        return x    
    elif x:
        return np.sqrt(x)    
    else:
        return

df.applymap(applySqrt)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>stringCol</th>
      <th>date</th>
      <th>day</th>
      <th>lc</th>
      <th>lcInt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-05-15 Monday</td>
      <td>2017-05-15</td>
      <td>Monday</td>
      <td>b</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-05-16 Tuesday</td>
      <td>2017-05-16</td>
      <td>Tuesday</td>
      <td>u</td>
      <td>4.472136</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-05-17 Wednesday</td>
      <td>2017-05-17</td>
      <td>Wednesday</td>
      <td>r</td>
      <td>4.123106</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-05-18 Thursday</td>
      <td>2017-05-18</td>
      <td>Thursday</td>
      <td>s</td>
      <td>4.242641</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-05-19 Friday</td>
      <td>2017-05-19</td>
      <td>Friday</td>
      <td>f</td>
      <td>2.236068</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----


#### <a id='datesexample'>Dates</a>



```python
df = pd.DataFrame()

df['dates'] = pd.date_range('1/1/2017', periods=5, freq='D')
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-01-05</td>
    </tr>
  </tbody>
</table>
</div>




```python
# truncate based on index
df.truncate(before=2, after=4)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-01-05</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index = df['dates']
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
    <tr>
      <th>dates</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-01</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>2017-01-02</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2017-01-03</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>2017-01-04</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>2017-01-05</th>
      <td>2017-01-05</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.truncate(before='1/3/2017', after='1/4/2017')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
    <tr>
      <th>dates</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-03</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>2017-01-04</th>
      <td>2017-01-04</td>
    </tr>
  </tbody>
</table>
</div>






```python
# dates as strings
df = pd.DataFrame()
df['dates'] = pd.date_range('1/1/2017', periods=7, freq='D').astype(str)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.applymap(type)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>1</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>2</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>3</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>4</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>5</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
    <tr>
      <th>6</th>
      <td>&lt;type 'str'&gt;</td>
    </tr>
  </tbody>
</table>
</div>




```python
# from string to datetime
df['dates'] = pd.to_datetime(df['dates'])
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.applymap(type)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>1</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>2</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>3</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>4</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>5</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
    <tr>
      <th>6</th>
      <td>&lt;class 'pandas.tslib.Timestamp'&gt;</td>
    </tr>
  </tbody>
</table>
</div>




```python
# date index

df.index = df['dates']
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
    <tr>
      <th>dates</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-01</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>2017-01-02</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2017-01-03</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>2017-01-04</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>2017-01-05</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>2017-01-06</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>2017-01-07</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>




```python
# slicing date index
df['1/3/2017':'1/7/2017']

```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
    <tr>
      <th>dates</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-03</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>2017-01-04</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>2017-01-05</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>2017-01-06</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>2017-01-07</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>



<br>
<br>
<br>
<br>

----


#### <a id='csvexample'>CSV</a>



```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
    <tr>
      <th>dates</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-01</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>2017-01-02</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2017-01-03</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>2017-01-04</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>2017-01-05</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>2017-01-06</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>2017-01-07</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>




```python
# write to csv

df.to_csv('./data/example.csv', index=False)
```


```python
# read CSV

df = pd.read_csv('./data/example.csv')
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dates</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-01-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-01-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-01-03</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2017-01-04</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2017-01-05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2017-01-06</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2017-01-07</td>
    </tr>
  </tbody>
</table>
</div>
