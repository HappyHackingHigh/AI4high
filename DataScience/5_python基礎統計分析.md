# 5_python基礎統計分析
```
基礎統計分析：
探索性資料分析 Explore Data Analytics
探索性資料分析是資料分析的一個步驟，透過敘述統計、圖表分析等方式來了解資料
（例如：最大、最小值、平均值、標準差、離群值等），找出假設和可能的特徵值。
```
# 延伸閱讀
```
使用 Python 資料分析和視覺化上市櫃公司薪資公開資料
https://blog.techbridge.cc/2019/07/26/how-to-use-taiwan-salary-data-to-do-python-data-analytics-and-data-visualization/
```
#
```
"""
資料來源：
08_Numeric and Statistical Methods.ipynb

# Configuring pandas
"""
### 下載資料
```
!wget https://raw.githubusercontent.com/PacktPublishing/Learning-Pandas-Second-Edition/master/data/sp500.csv
!wget https://raw.githubusercontent.com/PacktPublishing/Learning-Pandas-Second-Edition/master/data/omh.csv
```

```
# -*- coding: utf-8 -*-
import numpy as np
import pandas as pd

# used for dates
import datetime
from datetime import datetime, date

# Set formattign options
pd.set_option('display.notebook_repr_html', False)
pd.set_option('display.max_columns', 7)
pd.set_option('display.max_rows', 10)
pd.set_option('display.width', 60)

# bring in matplotlib for graphics
import matplotlib.pyplot as plt
# %matplotlib inline

# read in the data and print the first five rows
# use the Symbol column as the index, and 
# only read in columns in positions 0, 2, 3, 7
sp500 = pd.read_csv("sp500.csv", 
                    index_col='Symbol', 
                    usecols=[0, 2, 3, 7])

# one month of stock history data
omh = pd.read_csv("omh.csv")
```
# 8.2 對pandas物件執行算術運算
```
DataFrame or Series的簡單運算

```
### DataFrame or Series的簡單運算
```
# set the seed to allow replicatable results
np.random.seed(123456)
# create the DataFrame
df = pd.DataFrame(np.random.randn(5, 4), 
                  columns=['A', 'B', 'C', 'D'])
df

# multiply everything by 2
df * 2

# get first row 
s = df.iloc[0] 

# subtract first row from every row of the DataFrame
diff = df - s 
diff

# subtract DataFrame from Series
diff2 = s - df
diff2

# B, C
s2 = s[1:3]
# add E
s2['E'] = 0
# see how alignment is applied in math
df + s2

# get rows 1 through three, and only B, C columns
subframe = df[1:4][['B', 'C']]
# we have extracted a little square in the middle of df
subframe

# demonstrate the alignment of the subtraction
df - subframe

# get the A column
a_col = df['A']
df.sub(a_col, axis=0)
```
### Counts of values
```
s = pd.Series(['a', 'a', 'b', 'c', np.NaN])
# number of occurrences of each unique value
s.count()
```
### Unique and number of unique values
```
# return a list of unique items
s.unique()

s.nunique()

s.nunique(dropna=False)
```
### get summary stats on non-numeric data
```
s.value_counts(dropna=False)
```
### Minimum and maximums
```
# location of min price for both stocks
omh[['MSFT', 'AAPL']].min()

# and location of the max
omh[['MSFT', 'AAPL']].max()

# location of min price for both stocks
omh[['MSFT', 'AAPL']].idxmin()

# and location of the max
omh[['MSFT', 'AAPL']].idxmax()
```
### Smallest and Largest Values
```
# get the 4 smallest values
omh.nsmallest(4, ['MSFT'])['MSFT']

# get the 4 largest values
omh.nlargest(4, ['MSFT'])['MSFT']

# nsmallest on a Series
omh.MSFT.nsmallest(4)
```
### Accumulations
```
# calculate a cumulative product
pd.Series([1, 2, 3, 4]).cumprod()

# calculate a cumulative sum
pd.Series([1, 2, 3, 4]).cumsum()

# 8.3 描述統計學descriptive statistics
```

```

### get summary statistics for the stock data
```
omh.describe()
```
### just the stats for MSFT
```
omh.MSFT.describe()
```
### only the mean for MSFT
```
omh.MSFT.describe()['mean']
```
### get summary stats on non-numeric data
```
s = pd.Series(['a', 'a', 'b', 'c', np.NaN])
s.describe()
```
# 8.3.2.集中趨勢:

### Mean平均值
```
# the mean of all the columns in omh
omh.mean()

# calc the mean of the values in each row
omh.mean(axis=1)[:5]
```
### Median中位數
```
# calc the median of the values in each column
omh.median()
```
### Mode眾數
```
# find the mode of this Series
s = pd.Series([1, 2, 3, 3, 5])
s.mode()

# there can be more than one mode
s = pd.Series([1, 2, 3, 3, 5, 1])
s.mode()
```
# 8.3.3.離散趨勢

### Variance變異數
```
# calc the variance of the values in each column
omh.var()

# Standard Deviation標準差

# standard deviation
omh.std()
```
### Covarianc共變數
```
# covariance of MSFT vs AAPL
omh.MSFT.cov(omh.AAPL)
```
