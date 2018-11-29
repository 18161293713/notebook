[廖雪峰Python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)
## 数据类型和变量
```
// 在python数据类型写法跟数学上的写法一致
整数：1，100，23，-1，-928
浮点数：2.3，0.23，-9.1，-0.123
字符串："hello"，'hello'，"I'm ok"  // 字符串以""或者''括起来，单引号在双引号内时其也就是一个字符，当其在转义字符\后也是一个字符
布尔值：true/false
空：None
```
> Python允许r' '表示' '内部的字符串默认不转义

> 变量在程序中就是用一个变量名表示，变量名必须是大小写英文、数字和_的组合，且不能用数字开头

> 常量就是不能变的变量，比如常用的数学常数π就是一个常量。在Python中，通常用全部大写的变量名表示常量

## Python的字符串
```
// Python提供了ord()函数获取字符的整数表示，chr()函数把编码转换为对应的字符
ord('A') ==> 65
ord('中') ==> 20013
chr(66) ==> 'B'
chr(25991) ==> '文'

// bytes类型的数据用带b前缀的单引号或双引号表示
x = b'ABC'  // bytes的每个字符都只占用一个字节

// 以Unicode表示的str通过encode()方法可以编码为指定的bytes，无法显示为ASCII字符的字节，用\x##显示
'ABC'.encode('ascii') ==> b'ABC'
'中文'.encode('utf-8') ==> b'\xe4\xb8\xad\xe6\x96\x87' // 含中文字符串必须用utf-8，否则会报错

// 反过来，如果我们从网络或磁盘上读取了字节流，那么读到的数据就是bytes。要把bytes变为str，就需要用decode()方法
b'ABC'.decode('ascii') ==> 'ABC'
b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8', errors='ignore') ==> '中文'  // errors='ignore'忽略错误的字节

// 获取str长度用len()函数,如果是bytes则计算字节数
len('asd') ==> 3
len('你好') ==> 3

// 第一行注释是为了告诉Linux/OS X系统，这是一个Python可执行程序，Windows系统会忽略这个注释；
// 第二行注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

// 格式化方用 % 实现
'Hello, %s' % 'world' ==> 'Hello, world'
```

## list和tuple
### list
> list是一种有序的集合，可以随时添加和删除其中的元素。
```
// 新建一个list
list = ['a','b',10,999]
// 输出list
list ==> ['a','b',10,999]
// 获取list长度
len(list) ==> 4
// 根据索引访问元素
list[3] ==> 999  //取最后一个元素也可以这样 list[-1]
// list末尾添加元素
list.append('c') ==> ['a','b',10,999,'c']
// list索引添加元素
list.insert(1, 'd') ==> ['a','d','b',10,999,'c']
// list删除末尾元素
list.pop() ==> 'c'
// list索引删除元素
list.pop(2) ==> ['a','d',10,999]
// list索引替换元素
list[1] = 2 ==> ['a',2,10,999]
```
### tuple
> 另一种有序列表叫元组：tuple。tuple和list非常类似，但是==tuple一旦初始化就不能修改==。
```
// 新建tuple
tuple = (1,2,3)
// 只有1个元素的tuple定义时必须加一个逗号,
tuple = (1,)
```

## 条件判断
```
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```
> elif是else if缩写
## 循环
```
// for循环，遍历列表每个元素
for <对象> in <对象列表>
    print(<对象>)
    
// while循环，条件满足一致执行    
while <条件判断>
    <执行>
```
> break语句可以提前退出循环

> continue语句跳过当前循环直接开始下一次循环

## dict和set
### dict
> Python内置了字典：dict的支持，dict全称dictionary，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度。
```
// 新建一个dict
dict = {'a':1,'b':2,'c':3}
// 获取a的值
dict['a'] ==> 1
// 添加键值
dict['d'] = 4 ==> {'a':1,'b':2,'c':3,'d':4}
// 改变键的值
dict['d'] = 'alter' ==> {'a':1,'b':2,'c':3,'d':'alter'}
// 判断是否存在key
'd' in dict ==> true // 方法一
dict.get('f') ==> None // 方法二，dict.get('f',-1) 当f不存在返回-1
// 删除key
dict.pop('d') ==> {'a':1,'b':2,'c':3}
```
### set
> set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。
```
// 要创建一个set，需要提供一个list作为输入集合
s = set([1, 2, 3]) ==> {1, 2, 3}
// 添加
s.add(4) ==> {1, 2, 3, 4}
// 删除
s.remove(4) ==> {1, 2, 3}
```
# 函数
## 调用函数
> Python内置了很多有用的函数，我们可以直接调用。要调用一个函数，需要知道函数的名称和参数。
```
// 数据类型转换
int('123') ==> 123
int(12.34) ==> 12
float('12.34') ==> 12.34
str(1.23) ==> '1.23'
str(100) ==> '100'
bool(1) ==> True
bool('') ==> False
```
## 定义函数
> 在Python中，定义一个函数要使用def语句，依次写出函数名、括号、括号中的参数和冒号:，然后，在缩进块中编写函数体，函数的返回值用return语句返回。
```
// 定义一个函数
def my_abs(x):
    if x >= 0:
        return x   // 没有return语句，函数执行完毕后也会返回结果，只是结果为None。return None可以简写为return
    else:
        return -x
        
// 空函数 如果想定义一个什么事也不做的空函数，可以用pass语句：
def nop():
    pass 

// 返回多个值
def move(x, y, step, angle=0):   // angel=0 默认参数值
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
    
// 可变参数
def calc(*numbers):  // *number 表示一个tuple数组，可以有多个元素
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
    
// 关键字参数
def person(name, age, **extra)  // **extra可以是多个 key=value 的形式参数
```
## 递归函数
> 如果一个函数在内部调用自身本身，这个函数就是递归函数。
```
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)  // 未直接返回递归函数本身，会存在内存溢出异常
    
// 尾递归优化
def fact(n):
    return fact_iter(n, 1)

def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product)  // 返回递归函数本身，尾递归
```
> 尾递归是指，在函数返回的时候，调用自身本身，并且，return语句不能包含表达式。这样，编译器或者解释器就可以把尾递归做优化，使递归本身无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。

# 高级特性
## 切片
> 切片是指取数组指定索引范围的操作，用循环十分繁琐，因此，Python提供了切片（Slice）操作符，能大大简化这种操作。
```
// 定义一个list
listX = ['A','B','C','D','E','F']
// 取前3个元素 
listX[0:3] ==> ['A','B','C']  // 从索引0开始取(包括0) 到索引3但不包括索引3
// 取第2个元素
listX[1:2] ==> ['B']
```
## 迭代
> 在python迭代不仅仅只能作用于list duple这些数据类型，其也可以作用于dict，str等这些类
```
// 迭代语法
for item in items
    print(item)
    
// 判断对象是否可迭代
form collections import Iterable 
isinstance('abc', Iterable) ==> true  // 字符串能迭代
isinstance(12345, Iterable) ==> false   // 整数不能迭代
```

## 列表生成式
> 列表生成式即List Comprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。
```
// 生成1-10的list
list(range(1,11)) ==> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

// 生成[1x1, 2x2, 3x3, ..., 10x10]  ---返回x*x；x的值是循环range(1,11)生成list中的值
[x * x for x in range(1, 11)]  ==> [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

// for循环后面还可以加上if判断，这样我们就可以筛选出仅偶数的平方：
[x * x for x in range(1, 11) if x % 2 == 0] ==> [4, 16, 36, 64, 100]

// 还可以使用两层循环，可以生成全排列：
[m + n for m in 'ABC' for n in 'XYZ'] ==> ['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
```

## 生成器
> 生成器generator：是一种列表元素可以通过某种算法不断计算出来，这样就在生成大列表时可以节约大量内存
```
// 创建一个generator，有很多种方法。第一种方法很简单，只要把一个列表生成式的[]改成()，就创建了一个generator
L = [x * x for x in range(10)] ==> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]     // 一个list
g = (x * x for x in range(10)) ==> <generator object <genexpr> at 0x1022ef630>  // 一个generator

// 打印generator元素，需要用next()获取下一个返回值
next(g) ==> 0
next(g) ==> 1
next(g) ==> 4

// for循环取 generator元素
for n in g：
    print(n)  ==> 依次输出 0，1，4，9...81
    
// 定义generator的另一种方法。如果一个函数定义中包含yield关键字，那么这个函数就不再是一个普通函数，而是一个generator
// generator的函数，在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
f = fib(6) ==> <generator object fib at 0x104feaaa0>
```
## 高阶函数
### map
> map()函数接收两个参数，一个是函数，一个是Iterable，map将传入的函数依次作用到序列的每个元素，并把结果作为新的Iterator返回。
```
// map()传入的第一个参数是f，即函数对象本身。由于结果r是一个Iterator，Iterator是惰性序列，因此通过list()函数让它把整个序列都计算出来并返回一个list。
def f(x):
    return x * x

r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
list(r) ==> [1, 4, 9, 16, 25, 36, 49, 64, 81]
```
### reduce
> reduce把一个函数作用在一个序列[x1, x2, x3, ...]上，这个函数必须接收两个参数，reduce把结果继续和序列的下一个元素做累积计算回。
```
from functools import reduce
def add(x, y):
    return x + y

reduce(add, [1, 3, 5, 7, 9]) ==> 25
```
### filter
> filter()函数用于过滤序列。和map()类似，filter()也接收一个函数和一个序列。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。
```
// 删除list中偶数
def is_odd(n):
    return n % 2 == 1

list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15])) ==> [1, 5, 9, 15]
```
### sorted
> sorted()排序算法，可以对list进行排序，默认按照从小到大排序；sorted()函数也是一个高阶函数，它还可以接收一个key函数来实现自定义的排序
```
// 按绝对值大小排序
sorted([36, 5, -12, 9, -21], key=abs) ==> [5, 9, -12, -21, 36]
```
## 装饰器
> 函数也是一个对象，其有一个__name__属性，表示该函数的名称
```
abs.__name__ ==> 'abs'
```
> 装饰器(decorator)：在代码运行期间动态增加功能(类似于java中的切面实现的功能)，本质上，decorator就是一个返回函数的高阶函数。
```
// 定义扩展功能函数--函数执行前先打印时间
def log(func):
    @functools.wraps(func)  // 不改变函数的名称，让传入函数还是返回自己名称而不是'wrapper'
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper
// 通过@语法置于函数定义处
@log
def hello():
    print('hello world') ==> 会先执行log() 在执行hello()

// 如果decorator本身需要传入参数，那就需要编写一个返回decorator的高阶函数，写出来会更复杂
def log(text):
    def decorator(func):
        @functools.wraps(func)  // 不改变函数的名称，让传入函数还是返回自己名称而不是'wrapper'
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator
// 调用
@log('execute')
def now():
    print('2015-3-25')
```

## 作用域
> 类似_xxx和__xxx这样的函数或变量就是非公开的（private），不应该被直接引用，比如_abc，__abc等