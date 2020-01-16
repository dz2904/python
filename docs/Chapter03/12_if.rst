if 语句
########################

Python 条件语句是通过一条或多条语句的执行结果（True 或 False）来决定执行的代码块。

可以通过下图来简单了解条件语句的执行过程:

.. image:: ../images/if.01.jpg

.. highlight:: none

::

    name = input('What is your name? ')
    if name.endswith('Gumby'):
        print('Hello, Mr. Gumby')

这就是if 语句，让你能够有条件地执行代码。这意味着如果条件（if 和冒号之间的表达式）为真，就执行后续代码块（这里是一条print 语句）；如果条件为假，就不执行。

else 子句
************************

在前一节的示例中，如果你输入以 Gumby 结尾的名字，方法 name.endswith 将返回 True，导致后续代码块执行——打印问候语。如果你愿意，可使用 else 子句增加一种选择（之所以叫子句是因为 else 不是独立的语句，而是 if 语句的一部分）。

::

    name = input('What is your name?')
    if name.endswith('Gumby'):
        print('Hello, Mr. Gumby')
    else:
        print('Hello, stranger')

在这里，如果没有执行第一个代码块（因为条件为假），将进入第二个代码块（if 和　else　联合使用时，必定会选择其中一个语句执行）。

还有一个与 if 语句很像的“亲戚”，它就是条件表达式 ——C语言中三目运算符的Python版本。下面的表达式使用if 和 else 确定其值：

::

    status = "friend" if name.endswith("Gumby") else "stranger"

如果条件为真，表达式的结果为提供的第一个值（这里为"friend" ），否则为第二个值（这里为"stranger" ）。

elif 子句
************************

要检查多个条件，可使用 elif。elif 是 else if 的缩写，由一个 if 子句和一个 else 子句组合而成，也就是包含条件的 else 子句。

::

    num = int(input('Enter a number: '))
    if num > 0:
        print('The number is positive')
    elif num < 0:
        print('The number is negative')
    else:
        print('The number is zero')

代码块嵌套
************************

下面穿插点额外的内容。你可将if 语句放在其他if 语句块中，如下所示：

::

    name = input('What is your name? ')
    if name.endswith('Gumby'):
        if name.startswith('Mr.'):
            print('Hello, Mr. Gumby')
        elif name.startswith('Mrs.'):
            print('Hello, Mrs. Gumby')
        else:
            print('Hello, Gumby')
    else:
        print('Hello, stranger')

在这里，如果名字以 Gumby 结尾，就同时检查名字开头，这是在第一个代码块中使用一条独立的 if 语句完成的。请注意，这里还使用了 elif 。最后一个分支（else 子句）没有指定条件——如果没有选择其他分支，就选择最后一个分支。如果需要，这里的两个 else 子句都可省略。如果省略里面的 else 子句，将忽略并非以 Mr. 或 Mrs. 打头的名字。如果省略外面的 else 子句，将忽略陌生人。

断言
************************

if 语句有一个很有用的“亲戚”，其工作原理类似于下面的伪代码：

::

    if not condition:
        crash program

问题是，为何要编写类似于这样的代码呢？因为让程序在错误条件出现时立即崩溃胜过以后再崩溃。基本上，你可要求某些条件得到满足（如核实函数参数满足要求或为初始测试和调试提供帮助），为此可在语句中使用关键字 assert 。

::

    >>> age = 10
    >>> assert 0 < age < 100
    >>> age = -1
    >>> assert 0 < age < 100
    Traceback (most recent call last):
       File "<stdin>", line 1, in ?
    AssertionError

如果知道必须满足特定条件，程序才能正确地运行，可在程序中添加 assert 语句充当检查点，这很有帮助。

还可在条件后面添加一个字符串，对断言做出说明。

::

    >>> age = -1
    >>> assert 0 < age < 100, 'The age must be realistic'
    Traceback (most recent call last):
       File "<stdin>", line 1, in ?
    AssertionError: The age must be realistic
