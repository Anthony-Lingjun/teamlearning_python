# Task02：条件循环结构

## 简介

**理论部分**

- 掌握基本的条件，循环语句的使用。
- 掌握assert断言break,continue，pass，等语句的使用。
- 熟悉推导式的用法。

**练习部分**

- 课后思考题
- 龟兔赛跑游戏

## 笔记及练习

### 理论部分

#### 关于布尔表达式真假判断的前置知识

对于数值变量，0, 0.0 都可认为是空的，即为假。
对于容器变量，里面没元素就是空的，即为假。

#### 条件判断语句

* if 语句
```python
if expression:
    expr_true_suite
```

* if - else 语句
```python
if expression:
    expr_true_suite
else:
    expr_false_suite
```

* if - elif - else 语句
```python
if expression1:
    expr1_true_suite
elif expression2:
    expr2_true_suite
    .
    .
elif expressionN:
    exprN_true_suite
else:
    expr_false_suite
```

#### `assert` (断言) 关键词

用于检查其后条件表达式`expression`成立与否，若为`False`，程序将崩溃并抛出`AssertionError`异常，通常用于设置检查点，仅在条件成立时才允许程序正常工作。

#### 循环语句

* while 循环
```python
while expression:
    expr_true_suite
```

* while - else 循环
```python
while expression:
    expr_true_suite
else:
    expr_false_suite
```
`while`循环正常执行结束将会执行`else`的代码块，若是跳出循环（如`break`），则不执行。

* for 循环
```python
for iteration_var in iterable_object:
    expr_suite

#iterable_object = 任何有序序列（str, list, tuple）、可迭代对象（dict）
#注意对dict的迭代可以调用其items(), keys(), values()方法，直接迭代使用的是键（key）
```

* for - else 循环
```python
for iteration_var in iterable_object:
    expr_suite
else:
    expr_suite    
```
关于`for`循环与`else`的执行，与`while - else`循环一致。

#### 两个常用函数

* range() 函数
```python
range(start = 0, stop, step = 1)
#该函数的作用是生成一个由start参数值开始到stop参数值为止的数字序列，步长为step参数值。
#start, step 是可选的。
#注意序列中包括start的值但不包括stop的值。
```

* enumerate() 函数
```python
enumerate(sequence, [start=0])
#sequence -- 一个序列、迭代器或其他支持迭代对象。
#start -- 下标起始位置。
#返回 enumerate(枚举) 对象。
#注意该对象直接打印输出的是地址，打印前需使用list()转换
#结果形如[(0, 'A'), (1, 'B'), (2, 'C') ...]
```

#### break, continue, pass 语句

* `break`跳出当前所在层循环；

* `continue`终止本轮循环，开始下轮循环；

* `pass`空语句，放在要求有语句的地方占位，保持程序结构完整性。

#### 推导式

* 列表推导式
```python
[ expr for value in collection [if condition] ]

#example:
a = [(i, j) for i in range(0, 3) if i < 1 for j in range(0, 3) if j > 1]
#注意这样是以一种类似乘法分配律的方式生成，即[(0, 0), (0, 1), (0, 2), (1, 0), (1, 1),...]
```

* 元组推导式
```python
( expr for value in collection [if condition] )

#example:
a = (x for x in range(10))
print(a)# <generator object <genexpr> at 0x0000025BE511CC48>
print(next(a))  # 0
print(next(a))  # 1
print(tuple(a))# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

* 字典推导式
```python
{ key_expr: value_expr for value in collection [if condition] }

#example:
b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)# {0: True, 3: False, 6: True, 9: False}
```

* 集合推导式
```python
{ expr for value in collection [if condition] }
```

---

### 练习部分

#### 1、编写一个Python程序来查找那些既可以被7整除又可以被5整除的数字，介于1500和2700之间。

```python
# your code here
   
   
   
```

#### 2、龟兔赛跑游戏

题目描述：

话说这个世界上有各种各样的兔子和乌龟，但是研究发现，所有的兔子和乌龟都有一个共同的特点——喜欢赛跑。于是世界上各个角落都不断在发生着乌龟和兔子的比赛，小华对此很感兴趣，于是决定研究不同兔  子和乌龟的赛跑。他发现，兔子虽然跑比乌龟快，但它们有众所周知的毛病——骄傲且懒惰，于是在与乌龟的比赛中，一旦任一秒结束后兔子发现自己领先t米或以  上，它们就会停下来休息s秒。对于不同的兔子，t，s的数值是不同的，但是所有的乌龟却是一致——它们不到终点决不停止。 

然而有些比赛相当漫长，全程观看会耗费大量时间，而小华发现只要在每场比赛开始后记录下兔子和乌龟的数据——兔子的速度v1（表示每秒兔子能跑v1  米），乌龟的速度v2，以及兔子对应的t，s值，以及赛道的长度l——就能预测出比赛的结果。但是小华很懒，不想通过手工计算推测出比赛的结果，于是他找 到了你——清华大学计算机系的高才生——请求帮助，请你写一个程序，对于输入的一场比赛的数据v1，v2，t，s，l，预测该场比赛的结果。

输入:

输入只有一行，包含用空格隔开的五个正整数v1，v2，t，s，l，其中(v1,v2< =100;t< =300;s< =10;l< =10000且为v1,v2的公倍数) 

输出:

输出包含两行，第一行输出比赛结果——一个大写字母“T”或“R”或“D”，分别表示乌龟获胜，兔子获胜，或者两者同时到达终点。 
  
第二行输出一个正整数，表示获胜者（或者双方同时）到达终点所耗费的时间（秒数）。 

------

样例输入：

10  5  5  2  20 

样例输出

D<br>
4

```python
# your code here
   

   
```
   
   
