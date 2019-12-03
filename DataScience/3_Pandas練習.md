# 使用Pandas
```
https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html
```
```
import pandas as pd
from pandas import Series, DataFrame
```
# I. Series

```
obj = pd.Series([4, 7, -5, 3])
obj
```

```
obj.values
```

```
obj.index 
```

```
obj2 = pd.Series([4, 7, -5, 3], index=['d', 'b', 'a', 'c'])
obj2
```

```
obj2['a']
obj2['d'] = 6
obj2[['c', 'a', 'd']]
```
```
obj2[obj2 > 0]
obj2 * 2

```
```
import numpy as np
np.exp(obj2)
```

### 用現有的dict來創建series：
```
sdata = {'Ohio': 35000, 'Texas': 71000, 'Oregon':16000, 'Utah': 5000}
obj3 = pd.Series(sdata)
obj3

```
# II.DataFrame

```
data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada', 'Nevada'], 
        'year': [2000, 2001, 2002, 2001, 2002, 2003], 
        'pop': [1.5, 1.7, 3.6, 2.4, 2.9, 3.2]}

frame = pd.DataFrame(data)

frame
```


```
如果指定一列的話，會自動按列排序：

pd.DataFrame(data, columns=['year', 'state', 'pop'])
```
```
https://nbviewer.jupyter.org/github/LearnXu/pydata-notebook/blob/master/Chapter-05/5.1%20Introduction%20to%20pandas%20Data%20Structures%EF%BC%88pandas%E7%9A%84%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%EF%BC%89.ipynb
```
