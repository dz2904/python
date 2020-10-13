glob — 查找文件名
##########################

虽然 glob API 非常少，但是查找文件时非常有用。

glob 模块使用的模式规则不同于 re 模块使用的正则表达式，而是使用 Unix shell 规则去查找匹配模式的文件（目前仅支持 ``*`` ``?`` 和 ``[]`` ）。


.. attention::

    当匹配特殊字符字面值时，不能使用转义符 ``\\`` ，应该使用方括号括起来。 例如，``[?]`` 将匹配字符 ``?`` 。


**glob.glob(pathname, *, recursive=False)** 

返回匹配 pathname 的列表。 pathname 可以是绝对路径 (如 /usr/src/Python-1.5/Makefile) 或相对路径 (如 ../../Tools/*/*.gif)，并且可包含 shell 风格的通配符。

如果 recursive 为 True，模式 ``**`` 将匹配任何文件以及零个或多个目录和子目录。在一个较大的目录树中使用 ``**`` 模式可能会消耗非常多的时间。


.. highlight:: none

::

    >>> glob.glob('./[0-9].*')
    ['./1.gif', './2.txt']
    >>> glob.glob('*.gif')
    ['1.gif', 'card.gif']
    >>> glob.glob('?.gif')
    ['1.gif']
    >>> glob.glob('**/*.txt', recursive=True)
    ['2.txt', 'sub/3.txt']
    >>> glob.glob('./**/', recursive=True)
    ['./', './sub/']


如果目录中包含以 ``.`` 开头的文件，默认不会匹配。例如，考虑一个包含 card.gif  和 .card.gif 的目录:

::

    >>> glob.glob('*.gif')
    ['card.gif']
    >>> glob.glob('.c*')
    ['.card.gif']


**glob.iglob(pathname, *, recursive=False)**  

返回一个迭代器（iterator），产生的结果与 glob() 相同。


**glob.escape(pathname)**  

转义所有的特殊字符。

::

    >>> glob.escape('*.rst')
    '[*].rst'


