lambda 表达式
####################################

lambda 表达式用于创建匿名函数。其功能类似于：

.. highlight:: none

::

    >>> def addone(n):
    ...     return n+1
    ...
    >>> addone(2)
    3
    >>> addone(5)
    6

    # 使用 lambda 定义函数
    >>> l = lambda x: x+1
    >>> l(2)
    3
    >>> l(5)
    6

表达式 ``lambda parameters: expression`` 会产生一个函数对象。该未命名对象的行为类似于用以下方式定义的函数:

::

    def <lambda>(parameters):
        return expression

Lambda 函数可以接受任意数量的参数:

::

    >>> l = lambda a, b, c: a+b+c
    >>> l(1, 2, 3)
    6
    >>> l(5, 6, 7)
    18

.. note::

    lambda 和 def 的基本用法差不多，参数都是可选的，也都会返回值。最大的区别是：lambda 可以定义一个匿名函数，而 def 定义的函数必须有一个名字。

为什么使用 lambda 函数?
************************************

1. lambda 函数主要用来写一些小体量的一次性函数，避免污染环境（定义多个临时变量），同时也能简化代码。
2. lambda 起到了一种函数速写的作用，允许在使用的代码内嵌入一个函数的定义。
3. 在非多次调用的情况下，lambda 表达式即用既得。
4. 在 GUI 编程中，tkinter 由按钮触发的回调函数不能含有参数，这样就可以统一的去调用。当含有参数时经常用到 lambda。

::

    import sys
    from tkinter import Button, mainloop

    x = Button(text='Press me', command=(lambda : sys.stdout.write('Hello,World\n')))
    x.pack()
    x.mainloop()
