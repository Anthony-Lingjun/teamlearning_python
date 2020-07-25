# Task03：异常处理

## 简介

**理论部分**

- Python标准异常总结
- Python标准警告总结
- 相关语句介绍

**练习部分**

- 猜数字游戏

## 笔记

### Python标准异常总结

- BaseException：所有异常的 **基类**
- Exception：常规异常的 **基类**
- StandardError：所有的内建标准异常的基类
- ArithmeticError：所有数值计算异常的基类
- FloatingPointError：浮点计算异常
- OverflowError：数值运算超出最大限制
- ZeroDivisionError：除数为零
- AssertionError：断言语句（assert）失败
- AttributeError：尝试访问未知的对象属性
- EOFError：没有内建输入，到达EOF标记
- EnvironmentError：操作系统异常的基类
- IOError：输入/输出操作失败
- OSError：操作系统产生的异常（例如打开一个不存在的文件）
- WindowsError：系统调用失败
- ImportError：导入模块失败的时候
- KeyboardInterrupt：用户中断执行
- LookupError：无效数据查询的基类
- IndexError：索引超出序列的范围
- KeyError：字典中查找一个不存在的关键字
- MemoryError：内存溢出（可通过删除对象释放内存）
- NameError：尝试访问一个不存在的变量
- UnboundLocalError：访问未初始化的本地变量
- ReferenceError：弱引用试图访问已经垃圾回收了的对象
- RuntimeError：一般的运行时异常
- NotImplementedError：尚未实现的方法
- SyntaxError：语法错误导致的异常
- IndentationError：缩进错误导致的异常
- TabError：Tab和空格混用
- SystemError：一般的解释器系统异常
- TypeError：不同类型间的无效操作
- ValueError：传入无效的参数
- UnicodeError：Unicode相关的异常
- UnicodeDecodeError：Unicode解码时的异常
- UnicodeEncodeError：Unicode编码错误导致的异常
- UnicodeTranslateError：Unicode转换错误导致的异常

异常体系内部有层次关系，Python异常体系中的部分关系如下所示：

![](https://img-blog.csdnimg.cn/20200710131404548.png)

### Python标准警告总结

- Warning：警告的基类
- DeprecationWarning：关于被弃用的特征的警告
- FutureWarning：关于构造将来语义会有改变的警告
- UserWarning：用户代码生成的警告
- PendingDeprecationWarning：关于特性将会被废弃的警告
- RuntimeWarning：可疑的运行时行为(runtime behavior)的警告
- SyntaxWarning：可疑语法的警告
- ImportWarning：用于在导入模块过程中触发的警告
- UnicodeWarning：与Unicode相关的警告
- BytesWarning：与字节或字节码相关的警告
- ResourceWarning：与资源使用相关的警告

### 相关语句介绍

* try - except 语句

```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
    
‘’‘
语句的工作方式是
1. 检查在try子句的执行过程中是否有异常发生……
2. 若无，则执行完结束，不执行except内容；若有，则跳过余下部分，并进一步判断
3. 确定是否与except所指异常类型相符……
4. 若否，则该异常向外层传递；若是，则执行匹配except的子句
’‘’
```

【说明一】reason即是引用该exception对象的变量，可用作打印，如

```python
except OSError as error:
    print('打开文件出错\n原因是：' + str(error))
    #打开文件出错
    #原因是：[Errno 2] No such file or directory: 'test.txt'
```

【说明二】使用多个`except`代码块时，必须坚持对其规范排序，要从最具针对性的异常到最通用的异常，以免针对性的异常判断位于父类异常判断之后导致无法被捕捉。

【说明三】一个 `except` 子句可以同时处理元组内的多个异常。

```python
except (OSError, TypeError, ValueError) as error:
    print('出错了！\n原因是：' + str(error))
```

* try - except - finally 语句

```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
finally:
    无论如何都会被执行的代码
    
‘’‘
语句的工作特性是
- 不管try子句里面有没有发生异常，finally子句都会执行。
- 若try中跑出异常，又未被except接住，那么该异常将在finally执行结束后抛出。
’‘’
```

* try - except - else 语句

```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
    
‘’‘
语句的工作特性是
- 如果在try子句执行时没有发生异常，Python将执行else语句后的语句。
‘’‘
```

【说明】`else`语句的存在必须以`except`语句的存在为前提。

* raise语句

Python 使用`raise`语句抛出一个指定的异常。

```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    
# An exception flew by!
```

---
## 练习

### 猜数字游戏

**题目描述:**

电脑产生一个零到100之间的随机数字，然后让用户来猜，如果用户猜的数字比这个数字大，提示太大，否则提示太小，当用户正好猜中电脑会提示，"恭喜你猜到了这个数是......"。在用户每次猜测之前程序会输出用户是第几次猜测，如果用户输入的根本不是一个数字，程序会告诉用户"输入无效"。

(尝试使用try catch异常处理结构对输入情况进行处理)

获取随机数采用random模块。

![](https://img-blog.csdnimg.cn/20200714230819193.png)

```python
# your code here
   
   
   
   
   
```

   
   
