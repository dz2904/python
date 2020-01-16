生成器 yield
#######################

在一个百万级元素的序列中，如果我们仅仅需要访问前几个元素，而需要把整个序列加载到内存中，会造成很大的内存空间浪费。如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必加载完整的序列，从而节省大量的内存空间。在 Python 中，这种一边循环一边计算的机制，称为生成器：generator。

生成器是一个特殊的程序，可以被用作控制循环的迭代行为，python 中生成器是迭代器的一种，使用 ``yield`` 返回值函数，每次调用 ``yield`` 会暂停，而可以使用 ``__next__()`` 函数和 ``__send__()`` 函数恢复生成器。

生成器类似于返回值为数组的一个函数，这个函数可以接受参数，可以被调用，但是，不同于一般的函数会一次性返回包括了所有数值的数组，生成器一次只能产生一个值，这样消耗的内存数量将大大减小，因此生成器看起来像是一个函数，但是表现得却像是迭代器。

如果使用 ``yield`` 语句，可以让函数生成一个结果序列，而不仅仅是一个值，例如：

.. highlight:: none

::

    def countdown(n):
        print "Counting down!"
        while n > 0:
             yield n       # 生成一个值 n
             n -= 1

任何使用 ``yield`` 的函数都称为生成器。调用生成器函数将创建一个对象，该对象通过连续调用 ``__next__()`` 方法生成一系列的结果，例如：

::

    >>> c = countdown(5)
    >>> c.__next__()
    Counting down!
    5
    >>> c.__next__()
    4
    >>> c.__next__()
    3
    >>>

``__next__()`` 调用使生成器函数一直运行，到下一条 ``yield`` 语句为止。此时 ``__next__()`` 将返回传递给 ``yield`` 的值，而且函数将暂时中止执行。再次调用 ``__next__()`` 时，函数将继续执行 ``yield`` 之后的语句。此过程持续到函数返回为止。

通常不会像上面这样手动调用 ``__next__()`` ，而是会使用一个 ``for`` 循环，例如：

::

    >>> for i in countdown(5):
    ...     print i,
    Counting down!
    5 4 3 2 1
    >>>

生成器是编写基于处理管道、流或数据流程序的一种极其强大的方式。例如，下面的生成器函数模拟了常用于监控日志文件的 ``UNIX tail –f`` 命令的行为：

::

    # tail一个文件（如 tail -f）
    import time
    def tail(f):
        f.seek(0,2)     # 移动到 EOF
        while True:
            line = f.readline()    # 尝试读取一个新的文本行
            if not line:           # 如果没有内容，暂时休眠并再次尝试
                 time.sleep(0.1)
                 continue
            yield line

下面的生成器用于在很多行中查找特定的子字符串：

::

    def grep(lines, searchtext):
        for line in lines:
            if searchtext in line: yield line

下面的例子将以上两个生成器合并在一起，创建了一个简单的处理管道：

::

    # UNIX "tail –f | grep python" 命令的 python 实现
    wwwlog = tail(open("access-log"))
    pylines = grep(wwwlog,"python")
    for line in pylines:
        print line,

生成器的微妙之处在于，它经常和其他可迭代的对象（如列表或文件）混合在一起。特别是在编写如 for item in s 这样的语句时，s 可以代表一个列表、文件的各行、生成器函数的结果，或者支持迭代的其他任何对象。能够在 s 中插入不同对象，为创建可扩展的程序提供了一个强大的工具。

生成器函数完成的标志是返回或引发 ``StopIteration`` 异常，这标志着迭代的结束。如果生成器在完成时返回 ``None`` 之外的值，都是不合法的。

生成器使用时存在一个棘手的问题，即生成器函数仅被部分消耗。例如，请看以下代码：

::

    for n in countdown(10):
    　　 if n == 2: break
    　　 statements

在这个例子中，通过调用 ``break`` 退出 ``for`` 循环，而相关的生成器也没有全部完成。为了处理这种情况，生成器对象提供方法 ``close()`` 标识关闭。不再使用或删除生成器时，就会调用 close() 方法。通常不必手动调用 ``close()`` 方法，但也可以这么做，例如：

::

    >>> c = countdown(10)
    >>> c.__next__()
    Counting down from 10
    10
    >>> c.__next__()
    9
    >>> c.close()
    >>> c.__next__()
    Traceback (most recent call last):
    　File "<stdin>", line 1, in <module>
    StopIteration
    >>>

在生成器函数内部，在 yield 语句上出现 ``GeneratorExit`` 异常时就会调用 ``close()`` 方法。也可以选择捕捉这个异常，以便执行清理操作。

::

    def countdown(n):
    　　print("Counting down from %d" % n)
    　　try:
    　　　　 while n > 0:
    　　　　　　　yield n
    　　　　　　　n = n - 1
    　　except GeneratorExit:
    　　　　 print("Only made it to %d" % n)

虽然可以捕捉 ``GeneratorExit`` 异常，但对于生成器函数而言，使用 ``yield`` 语句处理异常并生成另一个输出值是不合法的。另外，如果程序当前正在对生成器进行迭代，不应通过另一个的执行线程或从信号处理程序异步调用该生成器上的 ``close()`` 方法。
