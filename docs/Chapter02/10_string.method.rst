字符串方法
####################################

字符串是 Python 中最常用的数据类型，几乎所有的 Python 程序中都有字符串的身影。字符串实现了所有一般序列的操作，还额外提供了很多附加方法。

标准库的文本处理服务部分涵盖了许多其他模块，提供各种文本相关工具（例如包含于 re 模块中的正则表达式支持）。

- str.capitalize()  首个字符大写，其余均为小写
- `str.casefold()`_  消除字符串的大小写，比 lower() 更彻底
- `str.center()`_  返回指定长度的字符串，原字符串居中，相似方法：str.ljust() str.rjust()
- `str.count()`_  返回子字符串重复的次数
- str.encode()  字符串编码
- `str.endswith()`_  判断结尾的字符，相似方法：str.startswith()
- `str.expandtabs()`_  用空格替换字符串中的制表符
- `str.find()`_  在字符串中查找子字符串，相似方法：str.rfind() str.index() str.rindex()
- `str.format()`_  字符串格式化，相似方法：str.format_map()
- `str.is()`_   很多 is 为前缀的方法，用于判断字符串是否满足特定的条件
- `str.join()`_  将序列中所有的值拼接成一个长字符串
- `str.lower()`_  返回字符串的小写版本，相似方法：str.upper() str.swapcase() str.title()
- `str.partition()`_  以指定的子字符串拆分原字符串，相似方法：str.rpartition(sep)
- `str.replace()`_ 替换字符串
- `str.split()`_  将字符串拆分为列表，相似方法：str.rsplit()
- `str.splitlines()`_  将多行字符串按行拆分为列表
- `str.strip()`_  删除开头和末尾的字符，相似方法：str.lstrip() str.rstrip()
- str.translate()  单字符替换字符串，相似方法：str.maketrans()
- `str.zfill()`_  用 0 在字符串开头填充到指定长度




.. _`str.casefold()`:

str.casefold()
************************************

返回原字符串消除大小写的副本。 消除大小写的字符串可用于忽略大小写的匹配。

消除大小写类似于转为小写，但是更加彻底一些，因为它会移除字符串中的所有大小写变化形式。 例如，德语小写字母 'ß' 相当于 "ss"。 由于它已经是小写了，lower() 不会对 'ß' 做任何改变；而 casefold() 则会将其转换为 "ss"。

.. highlight:: none

::

    >>> 'HELLO'.casefold()
    'hello'

    >>> 'Hello'.casefold()
    'hello'

    >>> 'heLLO'.casefold()
    'hello'


.. _`str.center()`:

str.center(width[, fillchar])
************************************

返回长度为 width 的字符串，原字符串居中对齐。 使用指定的 fillchar 填充两边的空位（默认使用空格），fillchar 只能指定一个字符，如果是多个字符会报 TypeError 错误。
如果 width 小于等于字符串长度则返回原字符串的副本。

::

    >>> 'Hello World'.center(40)
    '              Hello World               '

    >>> 'Hello World'.center(40, '+')
    '++++++++++++++Hello World+++++++++++++++'


    # str.ljust()  左对齐
    >>> 'Hello World'.ljust(40)
    'Hello World                             '


    # str.rjust()  右对齐
    >>> 'Hello World'.rjust(40, '-')
    '-----------------------------Hello World'


.. _`str.count()`:

str.count(sub[, start[, end]])
************************************

返回子字符串 sub 在 [start, end] 范围内重复出现的次数，可选参数 start 与 end 会被解读为切片表示法，范围包含索引 start，但不包含 end。

::

    >>> 'Hello World'.count('l')
    3

    >>> 'Hello World'.count('l', 4)
    1

    >>> 'Hello World'.count('abc')
    0


.. _`str.endswith()`:

str.endswith(suffix[, start[, end]])
*******************************************************************************

如果字符串结尾与指定字符相同则返回 True，否则返回 False。

suffix 也可以为由多个供查找的后缀构成的元组。
如果有可选项 start，将从所指定位置开始检查。如果有可选项 end，将在所指定位置停止比较。

::

    >>> 'Hello World'.endswith('orld')
    True

    >>> 'Hello World'.endswith('world')
    False

    # 传入后缀元组
    >>> 'Hello World'.endswith(('abc', 'def', 'world'))
    False


    # str.startswith() 判断字符串开头
    >>> 'Hello World'.startswith('H')
    True

    >>> 'Hello World'.startswith(('He', 'llo'))
    True


.. _`str.expandtabs()`:

str.expandtabs(tabsize=8)
************************************

返回字符串的副本，将所有的制表符 ``\t`` 替换为空格（一个或多个）。tabsize 设置空格的个数（默认值 8）。

::

    >>> a = 'a\tb\tc'
    >>> print(a)
    a       b       c

    >>> print(a.expandtabs(4))
    a   b   c


.. _`str.find()`:

str.find(sub[, start[, end]])
************************************

在字符串中查找子字符串。如果找到，就返回子字符串的最小（第一个）索引，未查找到则返回　-1。
可选参数 start 与 end 指定查找的范围（切片表示法），搜索范围包含 start，但不包含 end。

::

    >>> 'Hello World'.find('He')
    0

    >>> 'Hello World'.find('l')
    2

    >>> 'Hello World'.find('hello')
    -1

    >>> 'Hello World'.find('He', 3)
    -1


    # str.rfind() 返回子字符串的最大索引
    >>> 'Hello World'.rfind('l')
    9


    # str.index() 与 find() 相似，但找不到子类时会引发 ValueError
    >>> 'Hello World'.index('l')
    2

    >>> 'Hello World'.index('hello')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ValueError: substring not found

    # str.rindex() 返回子字符串的最大索引，找不到子类时会引发 ValueError
    >>> 'Hello World'.rindex('l')
    9


.. _`str.format()`:

str.format(*args, **kwargs)
************************************

执行字符串格式化操作，参数的个数必须大于等于替换域的个数。调用此方法的字符串可以包含字符串字面值或者以花括号 ``{}`` 括起来的替换域。
每个替换域可以包含一个位置参数的数字索引，或者一个关键字参数的名称。
返回的字符串副本中每个替换域都会被替换为对应参数的字符串值。

按位置访问参数:

::

    >>> '{}, {}, {}'.format('a', 'b', 'c')
    'a, b, c'

    # 位置参数
    >>> '{2}, {1}, {0}'.format('a', 'b', 'c')
    'c, b, a'

    # 序列解包参数
    >>> '{2}, {1}, {0}'.format(*'abc')
    'c, b, a'

    # 重复索引位置参数
    >>> '{0}, {1}, {0}'.format('a', 'b')
    'a, b, a'

    # 替代 %s 和 %r
    >>> "repr() shows quotes: {!r}; str() doesn't: {!s}".format('test1', 'test2')
    "repr() shows quotes: 'test1'; str() doesn't: test2"

按关键字访问参数:

::

    >>> 'Calendar: {month}  {day}, {years}'.format(years=2019, day=23, month='May')
    'Calendar: May  23, 2019'


    # 传入字典
    >>> date = {'years': 2019, 'day': 23, 'month': 'May'}
    >>> 'Calendar: {month}  {day}, {years}'.format(**date)
    'Calendar: May  23, 2019'

.. note::

    python 为字典格式化字符串提供了 format_map() 方法，类似于 str.format(**mapping)，不同之处在于 mapping 会被直接使用而不是复制字典。

    ::

        >>> date = {'years': 2019, 'day': 23, 'month': 'May'}
        >>> 'Calendar: {month}  {day}, {years}'.format_map(date)
        'Calendar: May  23, 2019'


访问参数的项:

::

    >>> coord = (3, 5)
    >>> 'X: {0[0]};  Y: {0[1]}'.format(coord)
    'X: 3;  Y: 5'

指定宽度并对齐文本:

::

    >>> '{:<30}'.format('left')
    'left                          '

    >>> '{:>30}'.format('right')
    '                         right'

    >>> '{:^30}'.format('centered')
    '           centered           '

    # 指定填充字符
    >>> '{:*^30}'.format('centered')
    '***********centered***********'

可用的整数表示类型：

::

    # b 二进制格式； c 打印相应的 unicode 字符； d 十进制整数； o 八进制格式
    # 分号前的数字为位置参数
    >>> '{0:b} {0:c} {0:d} {0:o}'.format(10)
    '1010 \n 10 12'

    # x 十六进制格式（小写字母）； X 十六进制格式（大写字母）
    >>> '{:x} {:X}'.format(45, 45)
    '2d 2D'

整数可以使用浮点数表示类型。 这时会在格式化之前使用 float() 将整数转换为浮点数。
可用的浮点数表示类型：

::

    # f 将数字转换为浮点数，默认精确度为 6
    >>> '{:f}'.format(23)
    '23.000000'

    # 指定浮点数精度，尾数四舍五入
    >>> '{:.2f}'.format(3.1355)
    '3.14'

    # % 百分比，将数字乘以 100 并显示为 f 格式，后面带百分号
    >>> '{:%}'.format(0.13)
    '13.000000%'

    >>> '{:.2%}'.format(0.13145)
    '13.15%'

指定正负号：

::

    # - 仅用于负数（这是默认行为）； + 用于正数和负数
    >>> '{0:-f}  {1:-f}  {0:+f}  {1:+f}'.format(3.14, -3.14)
    '3.140000  -3.140000  +3.140000  -3.140000'

    # space 在正数前使用空格，在负数前使用减号
    >>> '{: f}  {: f}'.format(3.14, -3.14)
    ' 3.140000  -3.140000'

使用逗号作为千位分隔符:

::

    >>> '{:,}'.format(1234567)
    '1,234,567'


.. _`''str.is()`:

str.is()
************************************

很多字符串方法都以 is 打头，它们判断字符串是否具有特定的性质。如果字符串具备特定的性质，这些方法就返回 True，否则返回 False。如果是空字符串大部分的方法会返回 False。

str.isalnum() 字符串只包含字母和数字：

::

    >>> '12aA'.isalnum()
    True

    >>> '3.14'.isalnum()
    False

    >>> '12aA '.isalnum()
    False

    >>> '12aA-'.isalnum()
    False

    >>> '12aA@'.isalnum()
    False

    >>> ''.isalnum()
    False

str.isalpha() 字符串只包含字母：

::

    >>> 'aB'.isalpha()
    True

    >>> 'a B'.isalpha()
    False

    >>> 'aB12'.isalpha()
    False

str.isascii() 字符串只包含 ASCII 字符或为空：

::

    >>> 'abAB!@   #$%^&&*()_-=+'.isascii()
    True

    >>> ''.isascii()
    True

    >>> '±'.isascii()
    False

str.isdigit() 字符串只包含数字：

::

    >>> '123'.isdigit()
    True

    >>> '3.14'.isdigit()
    False

str.islower() 字符串中所有大小写字符都是小写：

::

    >>> 'abc  123  !@#'.islower()
    True

    >>> 'abc \n \t'.islower()
    True

    >>> 'Top'.islower()
    False

str.isspace() 字符串只包含空白字符：


::

    >>> '   '.isspace()
    True

    >>> '\n \t \r'.isspace()
    True

    >>> ''.isspace()
    False

    >>> ' ab'.isspace()
    False

str.istitle() 字符串中只有单词词首是大写字符：

::

    >>> 'Tab  '.istitle()
    True

    >>> 'Hello World!'.istitle()
    True

    >>> 'Hello world'.istitle()
    False

    >>> 'HELLO'.istitle()
    False


str.isupper() 字符串中所有大小写字符都是大写：

::

    >>> 'ABC \n \t !@# 123'.isupper()
    True

    >>> 'Tab '.isupper()
    False


.. _`str.join()`:

str.join(iterable)
************************************

是一个非常重要的字符串方法，用于将一个由 iterable 中的字符串拼接而成的长字符串。 如果 iterable 中存在非字符串值则会引发 TypeError。其作用与 `str.split()`_ 相反。


::

    >>> path = ['usr', 'local', 'share', 'fonts']
    >>> '/'.join(path)
    'usr/local/share/fonts'

    >>> number = ['one', 'two', 'three', 'four', 'five']
    >>> ' < '.join(number)
    'one < two < three < four < five'

    # iterable 中只能包含字符串
    >>> number = ['one', 'two', 3]
    >>> ' < '.join(number)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: sequence item 2: expected str instance, int found


.. _`str.lower()`:

str.lower()
************************************

返回原字符串的小写字符。

在编程时，如需判断一个文件是否存在（在 Windows 系统中，文件名不区分大小写），更为保险的做法是将文件名都转换为小写字符再比较。

::

    >>> 'Hello World'.lower()
    'hello world'

    # str.upper() 原字符串的大写字符
    >>> 'Hello World'.upper()
    'HELLO WORLD'

    # str.swapcase() 反转原字符串的大小写
    >>> 'Hello World'.swapcase()
    'hELLO wORLD'

str.title()
====================================

将字符串转换为词首大写，即所有单词的首字母都大写，其余字母为小写。然而，它确定单词边界的方式可能导致结果不合理。

::
    >>> 'hello world'.title()
    'Hello World'

    # 结果并不理想
    >>> "that's all, folks".title()
    "That'S All, Folks"

另一种方法是使用模块 string 中的函数 capwords 。

::

    >>> import string
    >>> string.capwords("that's all, folks")
    That's All, Folks"


.. _`str.partition()`:

str.partition(sep)
************************************

在 sep 第一次出现的位置拆分字符串为一个 3 元组，其中包含分隔符之前的部分；分隔符本身；以及分隔符之后的部分。 如果分隔符未找到，则返回的 3 元组中包含字符本身以及两个空字符串。

::

    >>> 'This is a test'.partition('is')
    ('Th', 'is', ' is a test')

    >>> 'This is a test'.partition('abc')
    ('This is a test', '', '')

    # str.rpartition() 以最后一次出现的位置拆分字符串
    >>> 'This is a test'.rpartition('is')
    ('This ', 'is', ' a test')


.. _`str.replace()`:

str.replace(old, new[, count])
************************************

将所有的 old 子字符串替换为 new 子字符串。如果给出了可选参数 count，则只替换前 count 次出现的 old 子字符串。


::

    >>> 'This is a test'.replace('is', 'zzzz')
    'Thzzzz zzzz a test'

    >>> 'This is a test'.replace('is', 'zzzz', 1)
    'Thzzzz is a test'


.. _`str.split()`:

str.split(sep=None, maxsplit=-1)
************************************

将字符串拆分为列表，使用 sep 作为分隔字符串（默认使用空格）。如果给出了 maxsplit，则最多进行 maxsplit 次拆分（列表最多会有 maxsplit+1 个元素）。maxsplit 默认为 -1，进行所有拆分。

如果给出了 sep，连续的分隔符不会被组合在一起（例如 '1,,2'.split(',') 将返回 ['1', '', '2']）。

::

    # 默认情况下，连续的空格会被视为单个分隔符，开头或末尾的空格也将被忽略
    >>> '  Hello  World  '.split()
    ['Hello', 'World']

    # 没有找到分隔字符串
    >>> 'Hello World'.split('a')
    ['Hello World']

    # 空字符串
    >>> ''.split()
    []
    >>> ''.split('a')
    ['']

    >>> '/usr/bin/env'.split('/', 2)
    ['', 'usr', 'bin/env']

    >>> '1++2++3++4++5'.split('+')
    ['1', '', '2', '', '3', '', '4', '', '5']

    # str.rsplit() 从最末尾开始拆分字符串
    >>> '/usr/bin/env'.rsplit('/', 1)
    ['/usr/bin', 'env']


.. _`str.splitlines()`:

str.splitlines([keepends])
************************************

将多行字符串按行边界（见下表）拆分为列表，默认的结果列表中不包含行边界，keepends 为 True 时将包含行边界。

行边界是 universal newlines 的一个超集，包含一下字符：

==============     ==============
表示符                描述
==============     ==============
\\n                  换行
\\r                  回车
\\r\\n               回车 + 换行
\\v 或 \\x0b         行制表符
\\f 或 \\x0c         换表单
\\x1c               文件分隔符
\\x1d               组分隔符
\\x1e               记录分隔符
\\x85               下一行 (C1 控制码)
\\u2028             行分隔符
\\u2029             段分隔符
==============     ==============

::

    >>> 'ab c\n\nde fg\rkl\r\n'.splitlines()
    ['ab c', '', 'de fg', 'kl']

    >>> 'ab c\n\nde fg\rkl\r\n'.splitlines(keepends=True)
    ['ab c\n', '\n', 'de fg\r', 'kl\r\n']

在处理多行文本时建议使用 ``rst.splitlines()`` 而不是 ``rst.split()`` ，因为在处理空字符串和末尾空行时会更灵活。

::

    >>> ''.split('\n')
    ['']

    >>> ''.splitlines()
    []


    >>> 'One\nTwo\n'.split('\n')
    ['One', 'Two', '']

    >>> 'One\nTwo\n'.splitlines()
    ['One', 'Two']


.. _`str.strip()`:

str.strip([chars])
************************************

返回原字符串的副本，移除其中的开头和末尾的空白字符（不包括中间的空白）。 chars 参数为指定要移除字符的字符串。 如果省略或为 None，则默认移除空格符。

实际上 chars 参数并非指定单个前缀或后缀；而是参数值的所有组合（即包含的字符都会删除）。可以将参数看成一个但字符的元素，然后但字符删除。


::

    >>> '  Hello World    '.strip()
    'Hello World'

    # 指定字符参数
    >>> '** !! Hello *! World !* ! ! ** *!'.strip(' !*')
    'Hello *! World'


    # str.lstrip() 移除字符串开头的空白字符
    >>> '  Hello World  '.lstrip()
    'Hello World  '

    >>> '** !! Hello *! World !* !! ** *!'.lstrip(' !*')
    'Hello *! World !* !! ** *!'


    # str.rstrip() 移除字符串末尾的空白字符
    >>> '  Hello World  '.rstrip()
    '  Hello World'

    >>> '** !! Hello *! World !* !! ** *!'.rstrip(' !*')
    '** !! Hello *! World'


.. _`str.zfill()`:

str.zfill(width)
************************************

在原字符串开头填充 '0' 使其长度变为 width。 如果有正负值前缀（'+' 或 '-'）则在前缀之后填充。如果 width 小于等于 len(s) 则返回原字符串。

::

    >>> '32'.zfill(5)
    '00032'

    >>> '-32'.zfill(5)
    '-0032'

    >>> '+32'.zfill(5)
    '+0032'
