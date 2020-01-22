generator 生成器
####################################

在程序中需要用到斐波那契数列，但是不确定需要用前 10 个还是前 100 个值，这时生成前 100 个值的序列可能会解决问题，但是如果程序升级后需要 1000 个值呢？

在 Python 中，有一种可以一边循环一边计算的函数，称为生成器：generator。生成器类似于返回值为序列的函数，但是，生成器一次只返回序列中的一个值，而不是整个序列，这样消耗的内存数量将大大减小（序列越大时效果越明显）。因此生成器看起来像是函数，但是表现得却像是迭代器。


yield 表达式
************************************

yield 类似于 return 语句，用于在函数中返回一个值，但是 yield 不会结束函数。在函数内使用 yield 表达式会使这个函数变成一个生成器，并且在一个 async def 定义的函数体内使用 yield 表达式会让协程函数变成异步生成器。

.. note::

    只能在函数定义的内部使用 yield 表达式。

::

    >>> def foo():
    ...     print('Fibonacci sequence')
    ...     a, b = 0, 1
    ...     while True:
    ...         yield b
    ...         a, b = b, a+b
    ...
    >>> f = foo()
    >>> f.__next__()
    Fibonacci sequence
    1
    >>> f.__next__()
    1
    >>> f.__next__()
    2
    >>> f.__next__()
    3
    >>> f.__next__()
    5
    >>> f.__next__()
    8
    >>> f.__next__()
    13
    >>> f.__next__()
    21


调用 ``__next__()`` 方法使生成器函数运行，执行到 yield 表达式时暂停，并返回其值。再次调用 ``__next__()`` 时，函数将继续执行 yield 之后的语句，再次执行到 yield 表达式时暂停并返回值...

通常不会像上面这样手动调用 ``__next__()`` ，而是会像迭代器一样使用 for 循环。

::

    >>> def foo(n):
    ...     print('Fibonacci sequence')
    ...     a, b = 0, 1
    ...     while n > b:
    ...         yield b
    ...         a, b = b, a+b
    ...
    >>> for i in foo(30):
    ...     print(i)
    ...
    Fibonacci sequence
    1
    1
    2
    3
    5
    8
    13
    21


结束生成器
************************************

通常不应该在生成器中调用 break 语句结束生成器，应该使用 ``close()`` 方法结束生成器。

::

    >>> def foo():
    ...     print('Fibonacci sequence')
    ...     a, b = 0, 1
    ...     while True:
    ...         yield b
    ...         a, b = b, a+b
    ...
    >>> f = foo()
    >>> f.__next__()
    Fibonacci sequence
    1
    >>> f.__next__()
    1
    >>> f.__next__()
    2
    >>> f.__next__()
    3
    >>> f.__next__()
    5
    >>> f.close()
    >>> f.__next__()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    StopIteration

当生成器中出现 ``GeneratorExit`` 异常时就会调用 ``close()`` 方法结束生成器。
