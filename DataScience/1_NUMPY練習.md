# NumPy
```
https://zh.wikipedia.org/wiki/NumPy
NumPy是Python語言的一個擴充程式庫。
支援高階大量的維度陣列與矩陣運算，
此外也針對陣列運算提供大量的數學函式函式庫。

NumPy的前身Numeric最早是由Jim Hugunin與其它協作者共同開發，
2005年，Travis Oliphant在Numeric中結合了另一個同性質的程式庫Numarray的特色，
並加入了其它擴充功能而開發了NumPy。

NumPy為開放原始碼並且由許多協作者共同維護開發。

Numpy 底層以 C 和 Fortran 語言實作，所以能快速操作多重維度的陣列。
```
### 官方網址

![NumPy User Guide使用手冊](https://docs.scipy.org/doc/numpy/user/index.html)
NumPy Reference參考手冊   https://docs.scipy.org/doc/numpy/reference/index.html
```
### 參考資料:
```
https://blog.techbridge.cc/2017/07/28/data-science-101-numpy-tutorial/
http://www.runoob.com/numpy/numpy-tutorial.html
```
### 起手式
```
# 引入 numpy 模組
import numpy as np
```
# 1.Numpy ndarray資料結構及其屬性

Numpy 資料結構 == ndarray == N-dimensional array

```
https://docs.scipy.org/doc/numpy/reference/arrays.ndarray.html
```

## 創建陣列1
```
np1 = np.array([1, 2, 3])
np2 = np.array([3, 4, 5])
```
# ndarray 的關鍵屬性
```
# ndarray 的關鍵屬性是維度（ndim）、形狀（shape）和數值類型（dtype）

# 顯示ndarray 的關鍵屬性

np1 = np.array([1, 2, 3])
print(np1.ndim, np1.shape, np1.dtype) 
# 1 (3,) int64 => 一維陣列, 三個元素, 資料型別


# 創建陣列3*4全為 0 的陣列
# 創建陣列3*3全為 1 的陣列
```
## 使用numpy.arange() 創建陣列
```
numpy.arange(start, stop, step, dtype)
```
```
x = np.arange(5)  
print (x) ##答案為何?
```
```
x = np.arange(5, dtype =  float)  
print (x) ##答案為何?
```
## 使用numpy.linspace創建等差數列
```
#  numpy.linspace 函數用於創建一個一維陣列，陣列是一個等差數列構成的
#  np.linspace(start, stop, 
#       num=50, endpoint=True, retstep=False, dtype=None)

a = np.linspace(1,10,10)
print(a)

a = np.linspace(1,1,10)
print(a)

a = np.linspace(10, 20, 5, endpoint = False)  
print(a)

a = np.linspace(10, 20, 5)  
print(a)

a = np.linspace(10, 20, 5, endpoint = True)  
print(a)
```

## 使用numpy.logspace 函數創建一個等比數列。
```
# np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)

a = np.logspace(0,9,10,base=2)
print (a)
```

# 2.單一陣列運算

## 2.1.reshape函數==>改變函數
```
# 將底下np3改成2*3及3*2陣列
np3 = np.array([1, 2, 3, 4, 5, 6])
np3.dtype##答案為何?

np4 = np3.reshape([2, 3])
print(np4.ndim, np4.shape, np4.dtype) ##答案為何?
np4.dtype##答案為何?
```
## 2.2.改變陣列型別（bool、int、float、string）的運算
```
np5 = np3.astype('int64')
np3.dtype  ##答案為何?
```
## 2.3.陣列索引與切片運算
```
np13 = np.array([1, 2, 3, 4, 5, 6])
print(np13[2])  ##答案為何?

np23 = np13.reshape([2, 3])
print(np23[1, 0]) ##答案為何?

np3 = np.array([1, 2, 3, 4, 5, 6])
print(np3 > 3) ##答案為何?
print(np3[np3 > 3]) ##答案為何?

# 陣列的切片運算:
np10 = np.arange(10)
s = slice(2,7,2)   # 從索引 2 開始到索引 7 停止，間隔為2
print (np10[s]) ##答案為何?

np10 = np.arange(10)  
np11 = np10 [2:7:2]   # 從索引 2 開始到索引 7 停止，間隔為 2
print(np11) ##答案為何?

np10 = np.arange(10)  
np12 = np10 [2::2]  
print(np12) ##答案為何?
```
```
import numpy as np
 
a = np.array([[1,2,3],[3,4,5],[4,5,6]])  
print (a[...,1])   ##答案為何?
print (a[1,...])   ##答案為何?
print (a[...,1:])   ##答案為何?
```

# 依據axis的運算
```
np3 = np.array([1, 2, 3, 4, 5, 6])
np3 = np3.reshape([2, 3])
print(np3.sum(axis=1)) ##答案為何?
print(np3.sum(axis=0)) ##答案為何?
```
