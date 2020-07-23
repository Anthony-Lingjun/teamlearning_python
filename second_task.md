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

* 关于布尔表达式真假判断的前置知识

对于数值变量，0, 0.0 都可认为是空的，即为假。
对于容器变量，里面没元素就是空的，即为假。

* 条件判断语句

**if 语句**
```python
if expression:
    expr_true_suite
```

**if - else 语句**
```python
if expression:
    expr_true_suite
else:
    expr_false_suite
```

**if - elif - else 语句**
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

* `assert` (断言) 关键词

用于检查其后条件表达式`expression`成立与否，若为`False`，程序将崩溃并抛出`AssertionError`异常，通常用于设置检查点，仅在条件成立时才允许程序正常工作。

* 循环语句

**while 循环**
```python
while expression:
    expr_true_suite
```

**while - else 循环**
```python
while expression:
    expr_true_suite
else:
    expr_false_suite
```
`while`循环正常执行结束将会执行`else`的代码块，若是跳出循环（如`break`），则不执行。

**for 循环**
```python
for iteration_var in iterable_object:
    expr_suite

#iterable_object = 任何有序序列（str, list, tuple）、可迭代对象（dict）
#注意对dict的迭代可以调用其items(), keys(), values()方法，直接迭代使用的是键（key）
```

**for - else 循环**
```python
for iteration_var in iterable_object:
    expr_suite
else:
    expr_suite    
```
关于`for`循环与`else`的执行，与`while - else`循环一致。

* 两个常用函数

**range() 函数
```python
range(start = 0, stop, step = 1)
#该函数的作用是生成一个由start参数值开始到stop参数值为止的数字序列，步长为step参数值。
#start, step 是可选的。
#注意序列中包括start的值但不包括stop的值。
```

**enumerate() 函数
```python
enumerate(sequence, [start=0])
#sequence -- 一个序列、迭代器或其他支持迭代对象。
#start -- 下标起始位置。
#返回 enumerate(枚举) 对象。
#注意该对象直接打印输出的是地址，打印前需使用list()转换
#结果形如[(0, 'A'), (1, 'B'), (2, 'C') ...]
```

* break, continue, pass 语句

**`break`跳出当前所在层循环；
**`continue`终止本轮循环，开始下轮循环；
**`pass`空语句，放在要求有语句的地方占位，保持程序结构完整性。

* 推导式



### 练习部分
