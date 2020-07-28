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
  - 列表操作练习
  - 修改列表
  - leetcode 852题
- 元组
  - 元组概念
  - 拆包过程
- 字符串
  - 字符串函数回顾
  - 实现isdigit函数
  - leetcode 5题 

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

```

列表
- 列表的定义与创建
- 列表操作：添加、删除和获取元素
- 列表的常用操作符与其它方法

```

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

#### 列表操作：添加、删除和获取元素

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
    print(x9am)  # [123, 456, 456, 123]
    
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


### 元组

```

元组
- 元组的定义与创建
- 元组操作：更新、删除、获取元素
- 元组的常用操作符与其它方法

```

#### 元组的定义与创建

- 定义：与列表类似，不同之处为元组创建后不可修改。（即不可直接向元组元素赋值）

- 创建：

  - 以`(a, b, c)`形式创建。
  - `tuple(range(...)) or tuple(推导式)`
  
- 注意：

  - 可以什么符号也没有创建元组，但是可读性不强，如`x = 1, 2, 3, 4`
  - 元组中只包含一个元素时，需要在元素后面添加逗号，如`x = (1,)`
  - 不可直接用括号进行基于推导式的创建，这样会返回生成器对象，必须加`tuple`

#### 元组操作：更新、删除和获取元素

- 更新：

  - 元组本身不可更改（immutable），因此不可对其元素直接赋值，但是若元组的元素可更改（mutable），则可以更改其元素，由此可更新元组（对元组而言，其元素未进行重新赋值）。

    ```python
    t1 = (1, 2, 3, [4, 5, 6])
    print(t1)  # (1, 2, 3, [4, 5, 6])
    
    t1[3][0] = 9
    print(t1)  # (1, 2, 3, [9, 5, 6])
    ```

- 删除和获取：

  - 可以通过切片和索引取得元素，或者截取元组的部分，拼接新的元组。

    ```python
    week = ('Monday', 'Tuesday', 'Thursday', 'Friday')
    week = week[:2] + ('Wednesday',) + week[2:]
    print(week)  # ('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')
    ```
  

#### 元组的常用操作符与其它方法

- 等号操作符`==`；连接操作符 `+`；重复操作符 `*`；成员关系操作符 `in`、`not in`

- 注意：

  - 与列表一致

- 元组的其他方法

  - `tuple.count(obj)` ：统计元素出现次数

  - `tuple.index(x[, start[, end]])` 从列表中找出某个值第一个匹配项的索引位置

  - 元组的解压

    ```python
    #解压（unpack）一维元组，有几个元素左边括号定义几个变量（可以不用括号）；
    t = (1, 10.31, 'python')
    (a, b, c) = t # a = 1, b = 10.31, c = 'python'
    #解压二维元组（按照元组里的元组结构来定义变量）
    t = (1, 10.31, ('OK', 'python'))
    (a, b, (c, d)) = t # a = 1, b = 10.31, c = 'OK', d = 'python'
    #可用通配符加上变量名取得元组中的多个元素
    t = 1, 2, 3, 4, 5
    a, b, *rest, c = t # a = 1, b = 2, rest = [3, 4], c = 5
    #注意多个元素以列表方式取得
    ```
  

### 字符串

```

字符串
- 字符串的定义与形式
- 字符串操作：切片与拼接
- 字符串的常用方法与格式化

```

#### 字符串的定义与形式

- 定义：引号之间的字符集合

- 转义字符：

  | 转义字符 | 描述            |
  | :------: | --------------- |
  |   `\\`   | 反斜杠符号      |
  |   `\'`   | 单引号          |
  |   `\"`   | 双引号          |
  |   `\n`   | 换行            |
  |   `\t`   | 横向制表符(TAB) |
  |   `\r`   | 回车            |

- 亦可在原始字符串前面加一个r，如`print(r'C:\Program Files\Intel\Wifi\Help') `

- `'''`允许跨多行字符串，其中可以使用所有特殊字符

#### 字符串操作：切片与拼接

- 类似元组的切片与拼接

#### 字符串的常用方法与格式化

- 等号操作符`==`；连接操作符 `+`；重复操作符 `*`；成员关系操作符 `in`、`not in`

- 注意：

  - 与列表一致

- 字符串的其他方法

  - 大小写转换

    - `str.capitalize()` ：将字符串的第一个字符转换为大写
    - `str.lower()` ：所有大写字母转为小写
    - `str.upper()` ：所有小写字母转为大写
    - `str.swapcase()` ：大小写调换

  - 查找与匹配

    - `str_.count(str, beg= 0,end=len(string))` 返回`str`在 string 里面出现的次数，如果`beg`或者`end`指定则返回指定范围内`str`出现的次数
    - `str.endswith(suffix, beg=0, end=len(string))` 检查字符串是否以指定子字符串 `suffix` 结束，返回 True或False
    - `str.startswith(substr, beg=0,end=len(string))` 检查字符串是否以指定子字符串 `substr` 开头，同上
    - `str_.find(str, beg=0, end=len(string))` 与`str_.rfind(str, beg=0,end=len(string))`检测 `str` 是否包含在字符串中，若包含，返回开始的索引值，否则返回 -1。其中`rfind`是从右边开始查找。
    - `str.isnumeric()` 判断包含数字字符

  - 排版操作

    - `str.ljust(width[, fillchar])`返回一个原字符串左对齐，并使用fillchar（默认空格）填充至长度width的新字符串。
    - `str.rjust(width[, fillchar])`返回一个原字符串右对齐……
    - `str.lstrip([chars])` 截掉字符串左边的空格或指定字符。
    - `str.rstrip([chars])`删除字符串右边的空格或指定字符。
    - `str.strip([chars])` 在字符串上执行lstrip()和rstrip()。

  - 其他操作：

    - `str.partition(sub)`找到子串，将字符串分为三元组。

    - `str.replace(old, new [, max]`将字符串中的`old`替换成`new`，如果`max`指定，则不超过`max`次

    - `str_.split(str="", num)`不带参数默认是以空格为分隔符切片字符串

    - `str.splitlines([keepends])` 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数`keepends`为 False，不包含换行符，如果为 True，则保留换行符。

    - `str.maketrans(intab, outtab)` 创建字符映射的转换表，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。

    - `str.translate(table, deletechars="")` 根据参数`table`给出的表，转换字符串的字符，要过滤掉的字符放到`deletechars`参数中。

      ```python
      str7 = 'this is string example....wow!!!'
      intab = 'aeiou'
      outtab = '12345'
      trantab = str7.maketrans(intab, outtab)
      print(trantab)  # {97: 49, 111: 52, 117: 53, 101: 50, 105: 51}
      print(str7.translate(trantab))  # th3s 3s str3ng 2x1mpl2....w4w!!!
      ```

- 字符串格式化

  - `format` 格式化函数

    ```python
    str8 = "{0} Love {1}".format('I', 'Lsgogroup')  # 位置参数
    print(str8)  # I Love Lsgogroup
    
    str8 = "{a} Love {b}".format(a='I', b='Lsgogroup')  # 关键字参数
    print(str8)  # I Love Lsgogroup
    
    str8 = "{0} Love {b}".format('I', b='Lsgogroup')  # 位置参数要在关键字参数之前
    print(str8)  # I Love Lsgogroup
    
    str8 = '{0:.2f}{1}'.format(27.658, 'GB')  # 保留小数点后两位
    print(str8)  # 27.66GB
    ```

  - Python 字符串格式化符号

    | 符   号 | 描述                                                     |
    | :-----: | :------------------------------------------------------- |
    |   %c    | 格式化字符及其ASCII码                                    |
    |   %s    | 格式化字符串，用str()方法处理对象                        |
    |   %r    | 格式化字符串，用repr()方法处理对象（供解释器读取的形式） |
    |   %d    | 格式化整数                                               |
    |   %o    | 格式化无符号八进制数                                     |
    |   %x    | 格式化无符号十六进制数                                   |
    |   %X    | 格式化无符号十六进制数（大写）                           |
    |   %f    | 格式化浮点数字，可指定小数点后的精度                     |
    |   %e    | 用科学计数法格式化浮点数                                 |
    |   %E    | 作用同%e，用科学计数法格式化浮点数                       |
    |   %g    | 根据值的大小决定使用%f或%e                               |
    |   %G    | 作用同%g，根据值的大小决定使用%f或%E                     |


    【例子】
    ```python
    print('%o' % 10)  # 12
    print('%x' % 10)  # a
    print('%X' % 10)  # A
    print('%f' % 27.658)  # 27.658000
    print('%e' % 27.658)  # 2.765800e+01
    print('%E' % 27.658)  # 2.765800E+01
    print('%g' % 27.658)  # 27.658
    text = "I am %d years old." % 22
    print("I said: %s." % text)  # I said: I am 22 years old..
    print("I said: %r." % text)  # I said: 'I am 22 years old.'
    ```

    格式化操作符辅助指令（在%与字母之间）

    | 符号  | 功能                                                         |
    | :---: | :----------------------------------------------------------- |
    | `m.n` | m 是显示的最小总宽度,n 是小数点后的位数（如果可用的话）      |
    |  `-`  | 用作左对齐                                                   |
    |  `+`  | 在正数前面显示加号( + )                                      |
    |  `#`  | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
    |  `0`  | 显示的数字前面填充'0'而不是默认的空格                        |

    【例子】
    ```python
    print('%5.1f' % 27.658)  # ' 27.7'
    print('%.2e' % 27.658)  # 2.77e+01
    print('%10d' % 10)  # '        10'
    print('%-10d' % 10)  # '10        '
    print('%+d' % 10)  # +10
    print('%#o' % 10)  # 0o12
    print('%#x' % 108)  # 0x6c
    print('%010d' % 5)  # 0000000005
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

   
