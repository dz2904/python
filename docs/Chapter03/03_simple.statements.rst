简单语句
####################################

简单语句由一个单独的逻辑行构成。多条简单语句可以存在于同一行内并以分号分隔。 


表达式语句
************************************

表达式本身可以为语句。这在表达式为函数调用或文档字符串时特别有用。

表达式语句用于计算和写入值（大多是在交互模式下），或者调用一个过程。 表达式本身可以为语句。这在表达式为函数调用或文档字符串时特别有用。

.. highlight:: none

::

    >>> "This module contains SPAM-related functions."


赋值语句
************************************

赋值语句将变量与值关联起来。可通过序列解包同时给多个变量赋值，还可进行链式赋值。

::

    # 简单赋值
    >>> x = 42

    # 链式赋值
    x = y = z = 10

    # 序列解包
    >>> name, age = 'Gumby', 60
    
    >>> a, *b, c = 0, 1, 2, 3
    >>> a
    0
    >>> b
    [1, 2]
    >>> c
    3


增强赋值语句
====================================

可使用运算符来增强赋值。在这种情况下，将对变量的当前值和指定的值执行运算符指定的运算，并将变量重新关联到结果。

::

    >>> x = 2

    # 将 x 的值翻倍
    >>> x *= 2
    >>> x
    4

    # 将 x 的值加 2
    >>> x += 2
    >>> x
    6


assert 断言语句
************************************

断言语句用于判断一个表达式条件是否满足，如果不满足，则抛出 AssertionError 异常。

断言可以在条件不满足时直接返回错误，而不必等待程序运行后出现崩溃。例如代码只能在 Linux 系统下运行，可以先判断当前系统是否符合条件。


::

    import sys

    # 如果是 Linux 系统则运行下边的代码，否则报错
    assert ('linux' in sys.platform)

设置错误信息：

::

    >>> assert 1 == 2
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AssertionError

    >>> assert 1 == 2, 'one does not equal two'
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AssertionError: one does not equal two



pass 语句
************************************

pass 语句不执行任何操作，可用作占位符。在代码块中，如果不想执行任何操作，可让它只包含pass 语句。

::

    def f(arg):
        pass


del 语句
************************************

del 语句用于解除变量和属性与值的关联，以及将数据结构（映射或序列）的一部分（如位置、切片）删除。不能直接使用 del 来删除值，因为值只能通过垃圾收集来删除。

注意：删除是递归定义的，与赋值的定义方式非常类似。

::

    # 删除变量，实际上只是解除变量与值的关联
    >>> del x

    # 删除序列中的一个元素
    >>> del seq[42]

    # 删除序列中的一个切片
    >>> del seq[42:]

    # 删除映射中的一项
    >>> del map['foo']


return 语句
************************************

return 语句会结束函数的执行并返回一个值。如果没有指定值，将返回 None。

::

    def abc(nu):
        if nu > 0:
            return         # 从当前函数返回 None
        else:
            return True    # 从当前函数返回 True


yield 语句
************************************

yield 语句在语义上等同于 yield 表达式。 

yield 语句暂停执行生成器，并返回一个值。生成器是一种迭代器，可用于 for 循环中。

::

    yield 42    # 从当前函数返回42


raise 语句
************************************

raise 语句引发异常。

如果不带表达式，raise 会重新引发当前作用域内最后一个激活的异常。 如果当前作用域内没有激活的异常，将会引发 RuntimeError 来提示错误。


::

    >>> raise
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    RuntimeError: No active exception to reraise

    >>> raise IndexError
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    IndexError

    >>> raise IndexError('Index out of bounds')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    IndexError: Index out of bounds


break 语句
************************************

break 语句用于跳出所属的循环（for 或 while），并继续执行循环后面的语句。

::

    while True:
        line = file.readline()
        if not line:
            break
        print(line)


continue 语句
************************************

continue 语句类似于 break 语句，但只会跳出所属循环的当前迭代而不是整个循环，即跳到下一次迭代开头继续执行。

::

    while True:
        line = file.readline()
        if line.isspace():
            continue
        print(line)

import 语句
************************************

import 语句用于从外部模块导入名称（与函数、类或其他值相关联的变量）。这也包括 ``from __future__ import`` 语句，它们用于导入在未来的 Python 版本中将包含在标准中的功能。

基本的 import 语句（不带 from 子句）会分两步执行:
1. 查找一个模块，如果有必要还会加载并初始化模块。
2. 在局部命名空间中为 import 语句发生位置所处的作用域定义一个或多个名称。

::

    import math
    from math import sqrt
    from math import sqrt as squareroot
    from math import *


global 语句
************************************

global 语句用于将变量标记为全局变量。在函数中，可使用它给全局变量重新赋值。使用 global 语句通常被视为糟糕的编程风格，因此应尽可能避免。

::

    >>> def f():
    ...     global count
    ...     count = 1
    ... 

    >>> f()
    >>> count += 1
    >>> count
    2


nonlocal 语句
************************************

类似于 global 语句，但引用内部函数（闭包）的外部作用域。换言之，如果你在一个函数内定义了另一个函数并返回它，这个函数就可引用并修改外部函数中的变量，条件是使用 nonlocal 来标记它。

::

    def makeinc():
        count = 1
        def inc():
            nonlocal count
            count += 1
        return inc

