语句
#######################

真刀真枪地编写程序前，先来说说何为计算机编程。简而言之，计算机编程就是告诉计算机如何做。计算机多才多艺，但不太善于独立思考，我们必须提供详尽的细节，使用它们能够明白的语言将算法提供给它们。算法只不过是流程或菜谱的时髦说法，详尽地描述了如何完成某项任务。菜谱和算法都由原料（对象）和操作说明（语句）组成。表达式是一些东西，而语句做一些事情，表达式和语句的行为很像，因此它们之间的界线可能并非那么明确。

简单语句
***********************

简单语句只包含一个逻辑行。

表达式语句
=======================

表达式本身可以为语句。这在表达式为函数调用或文档字符串时特别有用。

.. highlight:: none

::

    "This module contains SPAM-related functions."

断言语句
=======================

断言语句检查条件是否满足，如果不满足，就引发 AssertionError 异常（并可提供错误消息）。

::

    assert age >= 12, 'Children under the age of 12 are not allowed'


赋值语句
=======================

赋值语句将变量与值关联起来。可通过序列解包同时给多个变量赋值，还可进行链式赋值。

::

    x = 42                     # 简单赋值
    name, age = 'Gumby', 60    # 序列解包
    x = y = z = 10             # 链式赋值

增强赋值语句
=======================

可使用运算符来增强赋值。在这种情况下，将对变量的当前值和指定的值执行运算符指定的运算，并将变量重新关联到结果。如果原来的值是可变的，可能修改原来的值（并让变量依然关联到原来的值）。

::

    x *= 2     #将x的值翻倍
    x += 5     #将x的值加5


pass 语句
=======================

pass 语句不执行任何操作，可用作占位符。在语法要求的代码块中，如果你不想执行任何操作，可让它只包含pass 语句。

::

    try:
        x.name
    except AttributeError:
        pass
    else:
        print('Hello', x.name)

del 语句
=======================

del 语句用于解除变量和属性与值的关联，以及将数据结构（映射或序列）的一部分（如位置、切片或存储槽）删除。不能直接使用它来删除值，因为值只能通过垃圾收集来删除。

::

    del x            # 解除变量与值的关联
    del seq[42]      # 删除序列中的一个元素
    del seq[42:]     # 删除序列中的一个切片
    del map['foo']   # 删除映射中的一项

return 语句
=======================

return 语句结束函数的执行并返回一个值。如果没有指定值，将返回 None。

::

    return              # 从当前函数返回None
    return 42           # 从当前函数返回42
    return 1, 2, 3      # 从当前函数返回(1, 2, 3)


yield 语句
=======================

yield 语句暂停执行生成器，并返回一个值。生成器是一种迭代器，可用于 for 循环中。

::

    yield 42            # 从当前函数返回42

raise 语句
=======================

raise 语句引发异常。调用它时可不提供任何参数（在 except 子句中用于重新引发当前捕获的异常），提供 Exception 的一个子类和一个可选参数（在这种情况下，将创建一个实例）或提供 Exception 子类的一个实例。

::

    raise # 只可用于except子句中
    raise IndexError
    raise IndexError, 'index out of bounds'
    raise IndexError('index out of bounds')

break 语句
=======================

break 语句结束它所属的循环语句（for 或 while 语句），并接着执行该循环语句后面的语句。

::

    while True:
        line = file.readline()
        if not line: break
        print(line)

continue 语句
=======================

continue 语句类似于 break 语句，但结束所属循环的当前迭代而不是整个循环，即跳到下一次迭代开头继续执行。

::

    while True:
        line = file.readline()
        if not line: break
        if line.isspace(): continue
        print(line)

import 语句
=======================

import 语句用于从外部模块导入名称（与函数、类或其他值相关联的变量）。这也包括 from __future__ import 语句，它们用于导入在未来的 Python 版本中将包含在标准中的功能。

::

    import math
    from math import sqrt
    from math import sqrt as squareroot
    from math import *


global 语句
=======================

global 语句用于将变量标记为全局的。在函数中，可使用它给全局变量重新赋值。使用 global 语句通常被视为糟糕的编程风格，因此应尽可能避免。

::

    count = 1
    def inc():
        global count
        count += 1


nonlocal 语句
=======================

类似于 global 语句，但引用内部函数（闭包）的外部作用域。换而言之，如果你在一个函数内定义了另一个函数并返回它，这个函数就可引用并修改外部函数中的变量，条件是使用 nonlocal 来标记它。

::

    def makeinc():
        count = 1
        def inc():
            nonlocal count
            count += 1
        return inc

复合语句
***********************

复合语句包含一组其他的语句（代码块）。

if 语句
=======================

if 语句用于有条件地执行，可包含 elif 和 else 子句。

::

    if x < 10:
        print('Less than ten')
    elif 10 <= x < 20:
        print('Less than twenty')
    else:
        print('Twenty or more')

while 语句
=======================

while 语句用于在指定条件为真时反复地执行（循环），可包含 else 子句，这种子句将在循环正常结束时执行（如没有执行任何 break 和 return 语句）。

::

    x = 1
    while x < 100:
        x *= 2
    print(x)


for 语句
=======================

for 语句用于对序列的元素或其他可迭代对象（包含返回迭代器的方法 __iter__ 的对象）反复地执行（循环），可包含 else 子句，这种子句将在循环正常结束时执行（如没有执行任何break 和return 语句）。

::

    for i in range(10, 0, -1):
        print(i)
    print('Ignition!')


try 语句
=======================

try 语句用于执行可能发生异常的代码段，让程序能够捕获这些异常并执行异常处理代码。try 语句可包含多个 except 子句（用于处理异常）和 finally 子句（这种子句不管情况如何都将执行，可用于执行清理工作）。

::

    try:
        1  0
    except ZeroDivisionError:
        print("Can't divide anything by zero.")
    finally:
        print("Done trying to calculate 1 0")

with 语句
=======================

with 语句用于包装使用上下文管理器的代码块，让管理器能够执行一些设置和清理操作。例如，可将文件用作上下文管理器，这样它们将在执行清理工作时关闭自己。

::

    with open("somefile.txt") as myfile:
        dosomething(myfile)
    # 到这里时文件已关闭


函数定义
=======================

函数定义用于创建函数对象以及将全局或局部变量与函数对象关联起来。

::

    def double(x):
        return x * 2


类定义
=======================

类定义用于创建类对象以及将全局或局部变量与类对象关联起来。

::

    class Doubler:
        def __init__ (self, value):
            self.value = value
        def double(self):
            self.value *= 2
