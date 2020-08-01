# Task05：字典、集合和序列

## 目录

**理论部分**

- 字典
  - 字典的定义与创建
  - 字典的可变类型和不可变类型
  - 字典的内置方法
- 集合
  - 集合的定义与创建
  - 集合的内置方法
  - 集合的转换与不可变集合
- 五种数据类型的总结
  - 三种分类
  - 序列的内置函数

**练习部分**

- 字典
  - 操作练习
  - 字典中的value
- 集合
  - 操作练习
- 序列
  - 内置函数练习

---

## 笔记

### 字典

```

字典
- 字典的定义与创建
- 字典的可变类型和不可变类型
- 字典的内置方法

```

#### 字典的定义与创建

- 定义：

  - 字典是**无序的**键值对（`key:value`）集合，在同一个字典之内，键互异。
  - 语法为`{元素1, 元素2, ..., 元素n}`

- 创建：

  - 直接以`{key1: value1, key2: value2, key3: value3}`形式创建。

  - 通过构造函数`dict`来创建字典。

    - `dict()` 创建一个空的字典。

    - `dict(mapping)`由映射对象的键值对创建，如：

      ```python
      #二元元组的列表
      dic1 = dict([('apple', 4139), ('peach', 4127), ('cherry', 4098)])
      print(dic1)  # {'cherry': 4098, 'apple': 4139, 'peach': 4127}
      
      #二元元组的元组
      dic2 = dict((('apple', 4139), ('peach', 4127), ('cherry', 4098)))
      print(dic2)  # {'peach': 4127, 'cherry': 4098, 'apple': 4139}
      ```

    - `dict(**kwargs)`由参数列表中的key=value对创建，如：

      ```python
      dic = dict(name='Tom', age=10)
      print(dic)  # {'name': 'Tom', 'age': 10}
      print(type(dic))  # <class 'dict'>
      #注意该方法所使用的key必须是字符串，且不可加引号，作为变量名书写
      ```

- 注意：

  - `dict` 内部存放的顺序和 `key` 放入的顺序是没有关系的。
  - `dict` **查找和插入的速度极快**，不会随着 `key` 的增加而增加，但是需要**占用**大量的**内存**。
  - 通过`key`直接把数据放入字典中，但一个`key`只能对应一个`value`，**后面的值会把前面的值冲掉**。

#### 字典的可变类型和不可变类型

- 概念：
  - 字典以**关键字**为索引，关键字可以是任意**不可变类型**，通常用字符串或数值。
  - 字典是 Python 唯一的一个**映射类型**，字符串、元组、列表属于序列类型。
  
- 快速判断可变不可变：

  - 麻烦法：对该变量进行某种操作前后查看`id(X)`，若一致，则可变；若不一致，则不可变。

  - 便捷法：`hash(X)`，不报错证明可哈希，即不可变，不可哈希即可变。

    ```python
    x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
    del x[0:2]
    print(x)  # ['Wednesday', 'Thursday', 'Friday']
    ```
  
- 小结：

  - 数值、字符、元组都能被哈希，因此它们是不可变类型。
  - 列表、集合、字典不能被哈希，因此它是可变类型。

#### 字典的内置方法

- `dict.fromkeys(seq[, value])` 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值。（元组形式，且值均相同）

  ```python
  seq = ('name', 'age', 'sex')
  dic1 = dict.fromkeys(seq)
  print(dic1)
  # {'name': None, 'age': None, 'sex': None}
  
  dic2 = dict.fromkeys(seq, 10)
  print(dic2)
  # {'name': 10, 'age': 10, 'sex': 10}
  
  dic3 = dict.fromkeys(seq, ('小马', '8', '男'))
  print(dic3)
  # {'name': ('小马', '8', '男'), 'age': ('小马', '8', '男'), 'sex': ('小马', '8', '男')}
  ```

- `dict.keys()`返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有键。

  ```python
  dic = {'Name': 'lsgogroup', 'Age': 7}
  print(dic.keys())  # dict_keys(['Name', 'Age'])
  lst = list(dic.keys())  # 转换为列表
  print(lst)  # ['Name', 'Age']
  ```

- `dict.values()`返回一个迭代器，可以使用 `list()` 来转换为列表，列表为字典中的所有值。

- `dict.items()`以**列表**返回可遍历的 (键, 值) 元组数组。

  ```python
  dic = {'Name': 'Lsgogroup', 'Age': 7}
  print(dic.items())
  # dict_items([('Name', 'Lsgogroup'), ('Age', 7)])
  
  print(tuple(dic.items()))
  # (('Name', 'Lsgogroup'), ('Age', 7))
  
  print(list(dic.items()))
  # [('Name', 'Lsgogroup'), ('Age', 7)]
  ```

- `dict.get(key, default=None)` 返回指定键的值，如果值不在字典中返回默认值。

  ```python
  dic = {'Name': 'Lsgogroup', 'Age': 27}
  print("Age 值为 : %s" % dic.get('Age'))  # Age 值为 : 27
  print("Sex 值为 : %s" % dic.get('Sex', "NA"))  # Sex 值为 : NA
  ```

- `dict.setdefault(key, default=None)`和`get()`方法类似，如果键不存在于字典中，将会**添加键并将值设为默认值**。

  ```python
  dic = {'Name': 'Lsgogroup', 'Age': 7}
  print("Age 键的值为 : %s" % dic.setdefault('Age', None))  # Age 键的值为 : 7
  print("Sex 键的值为 : %s" % dic.setdefault('Sex', None))  # Sex 键的值为 : None
  print(dic)  
  # {'Age': 7, 'Name': 'Lsgogroup', 'Sex': None}
  ```

- `key in dict` `in` 操作符用于判断键是否存在于字典中，如果键在字典 dict 里返回`true`，否则返回`false`。而`not in`操作符刚好相反，如果键在字典 dict 里返回`false`，否则返回`true`。

  ```python
  dic = {'Name': 'Lsgogroup', 'Age': 7}
  
  # in 检测键 Age 是否存在
  if 'Age' in dic:
      print("键 Age 存在")
  else:
      print("键 Age 不存在")
  ```

- `dict.pop(key[,default])`删除字典给定键 `key` 所对应的值，返回值为被删除的值。`key` 值必须给出。若`key`不存在，则返回 `default` 值。（**未设置 `default` 将报错**）
- `del dict[key]` 删除字典给定键 `key` 所对应的值。

- `dict.popitem()`随机返回并删除字典中的一对键和值，如果字典已经为空，却调用了此方法，就报出KeyError异常。

- `dict.clear()`用于删除字典内所有元素。

- `dict.copy()`返回一个字典的**浅复制**。

  ```python
  dic1 = {'user': 'lsgogroup', 'num': [1, 2, 3]}
  
  # 引用对象
  dic2 = dic1  
  # 浅拷贝父对象（一级目录），子对象（二级目录）不拷贝，还是引用
  dic3 = dic1.copy()  
  
  print(id(dic1))  # 148635574728
  print(id(dic2))  # 148635574728
  print(id(dic3))  # 148635574344
  
  # 修改 data 数据
  dic1['user'] = 'root'
  dic1['num'].remove(1)
  
  # 输出结果
  print(dic1)  # {'user': 'root', 'num': [2, 3]}
  print(dic2)  # {'user': 'root', 'num': [2, 3]}
  print(dic3)  # {'user': 'runoob', 'num': [2, 3]}
  
  # 注意复制了一个父对象，原有对子对象的引用不变，因此子对象里的不可变对象无法被由其他引用造成改变，而可变对象则可能被其他引用进行修改而产生变化。
  ```

- `dict.update(dict2)`把字典参数 `dict2` 的 `key:value`对 更新到字典 `dict` 里。

### 集合

```

集合
- 集合的定义与创建
- 集合的内置方法
- 集合的转换与不可变集合

```

#### 集合的定义与创建

- 定义：

  - Python 中`set`与`dict`类似，也是一组`key`的集合，但不存储`value`，无序。
  - 形式上由`{}`括出，但只有键，而不是键值对。
  - 由于`key`不能重复，所以，在`set`中，**没有重复的`key`**。

    ```python
    num = {1, 2, 3, 4}
    print(type(num))  # <class 'set'>
    ```

- 创建：

  - 创建空集合的时候只能使用`s = set()`，因为`s = {}`创建的是空字典。
  - 也可用花括号括起元素创建`{元素1, 元素2, ..., 元素n}`。重复元素在`set`中会被自动被过滤。
  - 使用`set(value)`工厂函数，把列表、元组或者字符串转换成集合。（同时也完成了去重）

- 注意：

  - `key`为不可变类型，即可哈希的值。
  - 由于 `set` 存储的是无序集合，所以我们不可以为集合创建索引或执行切片(slice)操作，也没有键(keys)可用来获取集合中元素的值，但是可以**判断一个元素是否在集合中**。

#### 集合的内置方法

- `set.add(elmnt)`用于给集合添加元素，如果添加的元素在集合中已存在，则不执行任何操作。
- `set.update(set)`用于修改当前集合，可以添加新的元素或**集合**到当前集合中，如果添加的元素在集合中已存在，则该元素只会出现一次，重复的会忽略。
- `set.remove(item)` 用于移除集合中的指定元素。若元素不存在，则会发生错误。
- `set.discard(value)` 用于移除指定的集合元素。若元素不存在， `discard()` 方法**不会发生错误**。
- `set.pop()` 用于随机移除一个元素。
- 两个或多个 set 可以做数学意义上的集合操作。
  - `set.intersection(set1, set2)` 与`set1 & set2` 返回两个集合的交集。
  - `set.intersection_update(set1, set2)` 在调用者集合取与参数集合的交集（即直接移除前者中的不重叠的元素），无返回值。
  - `set.union(set1, set2)` 与`set1 | set2` 返回两个集合的并集。
  - `set.difference(set)` 与`set1 - set2` 返回集合的差集。
  - `set.difference_update(set)` 调用者集合取与参数集合的差集（即直接移除前者中的重叠元素），无返回值。
  - `set.symmetric_difference(set)`与`set1 ^ set2`返回集合的异或。
  - `set.symmetric_difference_update(set)`调用者集合与参数集合进行异或（即直接移除前者中的重叠元素，向前者插入后者的不同元素），无返回值。
  - `set.issubset(set)`与`set1 <= set2` 判断集合是不是被其他集合包含，如果是则返回 True，否则返回 False。
  - `set.issuperset(set)`与`set1 >= set2` 判断集合是不是包含其他集合，如果是则返回 True，否则返回 False。
  - `set.isdisjoint(set)` 用于判断两个集合是不是**不相交**，如果是返回 True，否则返回 False。

#### 集合的转换与不可变集合

- 集合可以转为链表或元组
- Python 提供了不能改变元素的集合的实现版本，即不能增加或删除元素，类型名叫`frozenset`。需要注意的是`frozenset`仍然可以进行集合操作，只是不能用带有`update`的方法。
- `frozenset([iterable])` 返回一个冻结的集合，冻结后集合不能再添加或删除任何元素。

### 五种数据类型的总结

```

五种数据类型的总结
- 三种分类
- 序列的内置函数

```

#### 三种分类

- 序列类型：字符串、列表、元组
- 映射类型：字典
- 集合类型：集合

- 注意：集合和字典不支持索引、切片、相加和相乘操作。

#### 序列的内置函数

- `list(sub)` 把一个可迭代对象转换为列表。

- `tuple(sub)` 把一个可迭代对象转换为元组。

- `str(obj)` 把obj对象转换为字符串

- `len(s)` 返回对象（字符、列表、元组等）长度或元素个数。

- `max(sub)`返回序列或者参数集合中的最大值

- `min(sub)`返回序列或参数集合中的最小值

- `sum(iterable[, start=0])` 返回序列`iterable`与可选参数`start`的总和。

  ```python
  print(sum([1, 3, 5, 7, 9]))  # 25
  print(sum([1, 3, 5, 7, 9], 10))  # 35
  ```

- `sorted(iterable, key=None, reverse=False) ` 对所有可迭代的对象进行排序操作。`key` 主要是用来进行比较的元素，如

  ```python
  t = ({"age": 20, "name": "a"}, {"age": 25, "name": "b"}, {"age": 10, "name": "c"})
  x = sorted(t, key=lambda a: a["age"])
  print(x)
  # [{'age': 10, 'name': 'c'}, {'age': 20, 'name': 'a'}, {'age': 25, 'name': 'b'}]
  ```

- `reversed(seq)` 函数返回一个反转的**迭代器**。（seq可以是 tuple, string, list 或 range）

- `enumerate(sequence, [start=0])`用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

- `zip(iter1 [,iter2 [...]])`

  - 用于将可迭代的对象（一或多）作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象，这样做的好处是节约了不少的内存。

  - 我们可以使用 `list()` 转换来输出列表。

  - 如果各个迭代器的元素个数不一致，则返回列表**长度与最短的对象相同**，利用 `*` 号操作符，可以将元组解压为列表。

    ```python
    a = [1, 2, 3]
    b = [4, 5, 6]
    c = [4, 5, 6, 7, 8]

    zipped = zip(a, b)
    print(zipped)  # <zip object at 0x000000C5D89EDD88>
    print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]
    zipped = zip(a, c)
    print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]

    a1, a2 = zip(*zip(a, b))
    print(list(a1))  # [1, 2, 3]
    print(list(a2))  # [4, 5, 6]
    ```

---
## 练习

### 字典练习题：

#### 1、字典基本操作

字典内容如下:

```python
dic = {
    'python': 95,
    'java': 99,
    'c': 100
    }
```

用程序解答下面的题目

- 字典的长度是多少
  ```python
  len(dic)
  ```
- 请修改'java' 这个key对应的value值为98
  ```python
  dic['java'] = 98
  ```
- 删除 c 这个key
  ```python
  del dic['c']
  ```
- 增加一个key-value对，key值为 php, value是90
  ```python
  dic['php'] = 90
  ```
- 获取所有的key值，存储在列表里
  ```python
  k = list(dic.keys())
  ```
- 获取所有的value值，存储在列表里
  ```python
  v = list(dic.values())
  ```
- 判断 javascript 是否在字典中
  ```python
  ans = 'javascript' in dic
  ```
- 获得字典里所有value 的和
  ```python
  s = 0
  for key, value in dic.items():
    s += value
  ```
- 获取字典里最大的value
  ```python
  max(dic.values())
  ```
- 获取字典里最小的value
  ```python
  min(dic.values())
  ```
- 字典 dic1 = {'php': 97}， 将dic1的数据更新到dic中
  ```python
  dic.update(dic1)
  ```
  
#### 2、字典中的value

有一个字典，保存的是学生各个编程语言的成绩，内容如下

```
data = {
        'python': {'上学期': '90', '下学期': '95'},
        'c++': ['95', '96', '97'],
        'java': [{'月考':'90', '期中考试': '94', '期末考试': '98'}]
        }
```

各门课程的考试成绩存储方式并不相同，有的用字典，有的用列表，但是分数都是字符串类型，请实现函数`transfer_score(score_dict)`，将分数修改成int类型

```python
   
def transfer_score(score_dict):#针对传入dict/list/str，方便递归调用
    if type(score_dict) == dict:
        for key, value in score_dict.items():
            score_dict[key] = transfer_score(value)
    elif type(score_dict) == list:
        for i, value in enumerate(score_dict):
            score_dict[i] = transfer_score(value)
    elif type(score_dict) == str:
        return int(score_dict)
    return score_dict

```

### 集合练习题：

1. 怎么表示只包含⼀个数字1的元组。
`(1,)`
2. 创建一个空集合，增加 {‘x’,‘y’,‘z’} 三个元素。
```python
ans = set()
ans.update({'x','y','z'})
```
3. 列表['A', 'B', 'A', 'B']去重。
```python
ans = set(['A', 'B', 'A', 'B'])
```
4. 求两个集合{6, 7, 8}，{7, 8, 9}中不重复的元素（差集指的是两个集合交集外的部分）。
```python
ans = {6, 7, 8} ^ {7, 8, 9}
```
5. 求{'A', 'B', 'C'}中元素在 {'B', 'C', 'D'}中出现的次数。
```python
ans = len({'A', 'B', 'C'} & {'B', 'C', 'D'})
```


### 序列练习题：

1. 怎么找出序列中的最⼤、⼩值？

`max(sub)`返回序列或者参数集合中的最大值

`min(sub)`返回序列或参数集合中的最小值

2. sort() 和 sorted() 区别

`sort`是`list`的内置方法，无返回值。

`sorted`是内建函数，可对所有可迭代的对象进行排序操作，返回新的`list`。

3. 怎么快速求 1 到 100 所有整数相加之和？

```python
sum(range(1,101))
```

4. 求列表 [2,3,4,5] 中每个元素的立方根。

```python
ans = [2,3,4,5]
for index, value in enumerate(ans):
    ans[index] = pow(value, 1/3)
```

5. 将[‘x’,‘y’,‘z’] 和 [1,2,3] 转成 [(‘x’,1),(‘y’,2),(‘z’,3)] 的形式。

```python
ans = list(zip(['x','y','z'], [1,2,3]))
```

