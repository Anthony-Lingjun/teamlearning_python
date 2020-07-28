# Task04：列表、元组和字符串

## 目录

**理论部分**

- Python数据类型
- 列表
  - 列表的定义与创建
  - 列表操作：添加、删除、获取元素
  - 列表的常用操作符与其它方法
- 元组
  - 元组的定义与创建
  - 元组操作：更新、删除、获取元素
  - 元组的常用操作符与其它方法
- 字符串
  - 字符串的定义与形式
  - 字符串操作：切片与拼接
  - 字符串的常用方法与格式化

**练习部分**

- 列表
  - 
- 元组
  - 
- 字符串
  - 

---

## 笔记

### Python数据类型

- 简单数据类型：
  - 整型 'int'
  - 浮点型 'float'
  - 布尔型 'bool'
- 容器数据类型
  - 列表 'list'
  - 元组 'tuple'
  - 字符串 'str'
  - 字典 'dict'
  - 集合 'set'

### 列表

#### 列表的定义与创建

- 定义：**有序**集合，**无固定大小**，可保存**任意数量、任意类型**的Python对象，形式为[elem1, elem2, elem3, ...]。

- 创建：

  - 直接以`[a, b, c]`形式创建。

  - `list(range(...))`

  - 推导式创建，例如

    ```python
    x = [i for i in range(10)]
    
    x = [i**2 for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
    
    #二维数组
    x = [[0 for col in range(3)] for row in range(4)]
    ```

- 注意：

  - 列表中所保存的是对象的**指针**。

    比如`x = [a] * 4`操作中，只是创建4个指向list的引用，所以一旦`a`改变，`x`中4个`a`也会随之改变。（若`a`是不可变对象则无此情况）。

#### 列表操作：添加、删除、获取元素

- 添加：
  - `list.append(obj)` 在列表末尾添加新的对象，只接受一个参数，类型不限。
  - `list.extend(seq)` 在列表末尾追加参数序列中的的多个对象，即在原始列表末尾连接`seq`。
  - `list.insert(index, obj)` 在编号 `index` 位置插入 `obj`。

- 删除：

  - `list.remove(obj)` 基于元素值，移除`obj`在列表中的**第一个**匹配项。

  - `list.pop([index=-1])` 基于索引，移除列表中的某元素（默认最后一个元素），并且返回该元素的值。

  - 使用`del`语句可以按位置删除元素。

    ```python
    x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
    del x[0:2]
    print(x)  # ['Wednesday', 'Thursday', 'Friday']
    ```

- 获取：

  - 列表元素索引：正向由0起，反向由-1起。

  - 切片的通用写法是 `start : stop : step`，前闭后开。

  -  一些需要注意的操作

    ```python
    week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
    
    #step 设为 -1，相当于将列表反向排列。
    print(week[::-1])  
    # ['Friday', 'Thursday', 'Wednesday', 'Tuesday', 'Monday']
    
    #使用':'可复制（浅拷贝）列表中所有元素
    print(week[:])  
    # ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
    ```

#### 列表的常用操作符与其它方法

- 等号操作符`==`；连接操作符 `+`；重复操作符 `*`；成员关系操作符 `in`、`not in`

- 注意：

  - `==`要求位置与值均相同

  - 列表拼接有两种方式，用 `+`和`*`；前者首尾拼接，后者复制拼接。

  - 例

    ```python
    list1 = [123, 456]
    list2 = [456, 123]
    
    list4 = list1 + list2  # extend()
    print(list4)  # [123, 456, 456, 123]
    
    list5 = list1 * 3
    print(list5)  # [123, 456, 123, 456, 123, 456]
    
    list1 *= 3
    print(list1)  # [123, 456, 123, 456, 123, 456]
    ```

  - 前面三种方法（`append`, `extend`, `insert`）可对列表增加元素，它们没有返回值，是直接修改了原数据对象。 而将两个list相加，需要创建新的 list 对象，从而需要消耗额外的内存，特别是当 list 较大时，尽量不要使用 `+`来添加list。

- 列表的其他方法

  - `list.count(obj)` ：统计元素出现次数

  - `list.index(x[, start[, end]])` 从列表中找出某个值第一个匹配项的索引位置

  - `list.reverse()` 反向列表中元素

  - `list.sort(key=None, reverse=False)` 对原列表进行排序

    ```python
    '''
    参数key为函数对象
    该函数参数为调用sort的列表中的元素
    该函数返回值为元素排序依据
    
    参数reverse为排序规则，默认为False（升序），设为True则是降序
    
    无返回值
    '''
    
    x = [123, 456, 789, 213]
    x.sort(reverse=True)
    print(x)
    # [789, 456, 213, 123]
    
    x.sort(key=lambda a: a[0])
    print(x)
    # [(1, 3), (2, 2), (3, 4), (4, 1)]
    ```

  

---
## 练习

### 列表练习题：

#### 1、列表操作练习

列表lst 内容如下

lst = [2, 5, 6, 7, 8, 9, 2, 9, 9]

请写程序完成下列操作：

1. 在列表的末尾增加元素15
2. 在列表的中间位置插入元素20
3. 将列表[2, 5, 6]合并到lst中
4. 移除列表中索引为3的元素
5. 翻转列表里的所有元素
6. 对列表里的元素进行排序，从小到大一次，从大到小一次



#### 2、修改列表

问题描述：

lst = [1, [4, 6], True]

请将列表里所有数字修改成原来的两倍



#### 3、leetcode 852题 山脉数组的峰顶索引

如果一个数组k符合下面两个属性，则称之为山脉数组

数组的长度大于等于3

存在$i$，$i$ >0 且$i<\operatorname{len}(k)-1$， 使得$$\mathrm{k}[0]<\mathrm{k}[1]<\ldots<\mathrm{k}[\mathrm{i}-1]<\mathrm{k}[\mathrm{j}]>\mathrm{k}[\mathrm{i}+1] \ldots>\mathrm{k}[\operatorname{len}(\mathrm{k})-1]$$

这个$i$就是顶峰索引。

现在，给定一个山脉数组，求顶峰索引。

示例:

输入：[1, 3, 4, 5, 3]

输出：True

输入：[1, 2, 4, 6, 4, 5]

输出：False

```python
class Solution:
    def peakIndexInMountainArray(self, A: List[int]) -> int:
       
    # your code here
```



### 元组练习题：

#### 1、元组概念

写出下面代码的执行结果和最终结果的类型

```python
(1, 2)*2
(1, )*2
(1)*2
```

分析为什么会出现这样的结果.



#### 2、拆包过程是什么？

```python
a, b = 1, 2
```



### 字符串练习题：

#### 1、字符串函数回顾

- 怎么批量替换字符串中的元素？
- 怎么把字符串按照空格进⾏拆分？
- 怎么去除字符串⾸位的空格？



#### 2、实现isdigit函数

题目要求

实现函数isdigit， 判断字符串里是否只包含数字0~9

```python
def isdigit(string):
    """
    判断字符串只包含数字
    :param string:
    :return:
    """
    # your code here
    pass
```



#### 3、leetcode 5题 最长回文子串

给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 1000。

示例:

输入: "babad"

输出: "bab"

输入: "cbbd"

输出: "bb"

```python
class Solution:
   def longestPalindrome(self, s: str) -> str:
          
    # your code here
```

   

