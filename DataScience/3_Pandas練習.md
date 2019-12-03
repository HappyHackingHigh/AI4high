#
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

```
```

```
```

```
```

```
```

```
```

```
