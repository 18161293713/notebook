### 目标

- [x] 了解pandas库的DataFrame和Series数据结构
- [x] DataFrame、Series的处理
- [x] DataFrame中索引
### 基本概念
Series：单一的列数据结构

DataFrame：table数据结构其中包含一个或多个Series数据结构
#### DataFrame结构如下：
| ~~index~~| Series1 | Series2 |Series3|
|:---| ---- | ----    |----|
| 0  |  value1|  value2|value3|
| 1  |  value1|  value2|value3|
| 2  |  value1|  value2|value3|
> index列是自动生成索引，非传入值，可以用‘reindex’函数自由排列
#### 以上table代码
```python
import pandas as pd 

Series1 = pd.Series(['value1', 'value1', 'value1'])
Series2 = pd.Series(['value2', 'value2', 'value2'])
Series3 = pd.Series(['value3', 'value3', 'value3'])

pd.DataFrame({'Series1':Series1, 'Series2':Series2, 'Series3':Series3})
```
### 数据处理
#### 获取DataFrame前几个数据
```python
pd.DataFrame(['Series1':Series1, 'Series2':Series2, 'Series3':Series3,]).head(2)
```
| ~~index~~| Series1 | Series2 |Series3|
|:---| ---- | ----    |----|
| 0  |  value1|  value2|value3|
| 1  |  value1|  value2|value3|
#### 加载CSV数据
```python
df = pd.read_csv('***.csv', header=0)
df.describe()
```
>  如有中文，最好加上encoding='gbk'
#### 获取后几行数据
```python
df.tail(5)
```
#### 获取DataFrame行数
```python
len(df)
```

#### 访问数据
可以使用熟悉的Python dict/list指令访问DataFrame数据
```python
df = pd.DataFrame({'Series1':Series1, 'Series2':Series2, 'Series3':Series3})
print(type(df['Seriers1']))
df['Seriers1']
```
| ~~index~~| ~~Series1~~ |
|:---| ---- |
| 0  |  value1|
| 1  |  value1|
| 2  |  value1|
```python
print(type(df['Seriers1'][1]))
df['Seriers1'][1]
```
value1
```python
print(type(df[0:2]))
df[0:2]
```
| ~~index~~| Series1 | Series2 |Series3|
|:---| ---- | ----    |----|
| 0  |  value1|  value2|value3|
| 1  |  value1|  value2|value3|

### 索引
Series、DataFrame对象定义了index属性，因此每个Series和DataFrame都有一个标识符值
> 默认情况下pandas回赋可以反映数据源数据顺序的索引值，索引值创建后是稳定的，不会因为数据的重排序而改变。
```python
df.index
df.reindex([x,x,x,x])
```