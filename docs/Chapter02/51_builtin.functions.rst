内置函数
####################################

Python 解释器内置了很多函数和类型，您可以在任何时候使用它们。

- `abs()`_  返回数字的绝对值
- `all()`_  判断可迭代对象中的所有元素是否都为 True
- `any()`_  判断可迭代对象中的所有元素是否都为 False
- ascii()  返回一个对象可打印的字符串
- `bin()`_  返回一个整数的二进制字符串
- `bool()`_  将给定参数转换为布尔类型
- breakpoint()  在调用时将陷入调试器中
- bytearray()  返回一个新的 bytes 数组（可变序列）
- bytes()  返回一个新的 bytes 数组（不可变序列）
- callable()  判断一个对象是否可调用
- `chr()`_  返回整数的 Unicode 码位的字符串格式
- classmethod()  将一个方法封装成类方法
- `compile()`_  将一个字符串编译为可执行的代码
- complex()  返回值为 real + imag*1j 的复数
- `delattr()`_  删除类对象中的属性
- `dict()`_  创建一个新的字典
- `dir()`_  返回当前作用域中的变量、方法和定义的类型列表
- `divmod()`_  返回一对数字的商和余数的元组
- `enumerate()`_  为一个可遍历的对象添加一个索引
- `eval()`_  执行一个字符串表达式
- `exec()`_  执行储存在字符串或文件中的代码
- `filter()`_  根据条件过滤序列，并返回一个迭代器对象
- `float()`_  将整数和字符串转换成浮点数
- `format()`_  格式化字符
- frozenset()  创建一个不能修改的集合，与 set() 相似只是集合不可以修改
- `getattr()`_  返回类对象属性的值
- `globals()`_  以字典类型返回当前位置的全局变量
- `hasattr()`_  判断对象是否包含对应的属性
- `hash()`_  返回对象的哈希值
- `help()`_  查看函数或模块的帮助信息
- `hex()`_  将一个整数转换为十六进制字符串
- `id()`_ 返回对象的“标识值”（内存地址）
- `input()`_  接受一个标准输入数据，返回为字符串类型
- `int()`_  将一个字符串或数字转换为整数
- `isinstance()`_  判断对象是否是一个已知的类型，类似 type()
- `issubclass()`_  判断俩个类对象是否为继承关系（子类）
- `iter()`_  创建一个迭代器对象
- `len()`_  返回对象的长度（元素个数）
- `list()`_  创建一个列表
- `locals()`_  以字典类型返回当前位置的局部变量
- `map()`_  将序列做函数计算，并返回一个迭代器对象
- `max()`_  返回参数的最大值
- memoryview()  返回参数的“内存视图”对象
- `min()`_  返回参数的最小值
- `next()`_  返回迭代器的下一个项目
- object()  返回一个没有特征的新对象。object 是所有类的基类。
- `oct()`_  将一个整数转换为八进制字符串
- `open()`_  打开一个文件，并返回文件对象
- `ord()`_  返回字符的 Unicode 码位的字符串格式
- `pow()`_  返回参数的次幂
- `print()`_  打印输出
- property()  返回 property 属性
- `range()`_  返回一个可迭代对象
- repr()  返回一个表示对象的可打印字符串
- `reversed()`_  返回一个反向的迭代器
- `round()`_  返回浮点数的四舍五入值
- `set()`_  创建一个集合
- `setattr()`_  设置类对象的属性值，该属性不一定要存在
- `slice()`_  切片对象
- `sorted()`_  返回一个新的排序列表
- `staticmethod()`_  将方法转换为静态方法
- `str()`_  将对象转化为字符串，并返回
- `sum()`_  计算序列中值的总和
- `super()`_  调用父类（超类）的方法
- `tuple()`_  创建一个元组
- `type()`_   返回对象的类型
- `vars()`_  返回对象的 {属性: 属性值} 字典对象
- `zip()`_  将多个可迭代对象中对应的元素打包成一个个元组
- __import__()  动态加载类和函数


.. _`abs()`:

abs(x)
************************************

返回一个数值的绝对值。实参可以是整数或浮点数。如果实参是一个复数，返回它的模。

- x -- 整数，浮点数，复数

.. highlight:: none

::

    >>> abs(-3.14)
    3.14

    >>> abs(-10)
    10

    >>> abs(1j)
    1.0


.. _`all()`:

all(iterable)
************************************

如果 iterable 的所有元素为真（或迭代器为空），返回 True，否则返回 False。
元素除了是 0、空、None、False 之外都算 True。

- iterable -- 元组、列表、集合或字典

::

    >>> all(['a', 1])
    True

    >>> all(['a', False])
    False

    >>> all(['a', ''])
    False

    >>> all(['a', 0])
    False

    >>> all([])
    True

    >>> all({'a': 0})
    True

    >>> all({0: 'a'})
    False


.. _`any()`:

any(iterable)
************************************

如果 iterable 的任一元素为真则返回 True，否则返回 False。 如果迭代器为空，返回 False。

此函数与 `all()`_ 正好相反。


.. _`bin()`:

bin(x)
************************************

返回一个整数 int 的二进制字符串。

- x -- 整数

::

    >>> bin(3)
    '0b11'

    >>> bin(-10)
    '-0b1010'


.. _`bool()`:

class bool([x])
************************************

返回一个布尔值，True 或 False。 x 使用标准的真值测试过程来转换。如果 x 是假的或者被省略，返回 False；其他情况返回 True。

::

    >>> bool('a')
    True

    >>> bool(0)
    False

    >>> bool('')
    False

    >>> bool([])
    False

    >>> bool(3>2)
    True

    >>> bool(True or False)
    True


.. _`chr()`:

chr(i)
************************************

返回 i 参数的 Unicode 码位的字符串格式。这是 `ord()`_ 的逆函数。

- i -- 整数，合法范围是 0 到 1,114,111（16 进制表示是 0x10FFFF）

::

    >>> chr(97)
    'a'
    >>> chr(8364)
    '€'
    >>> chr(0x30)
    '0'


.. _`compile()`:

compile(source, filename, mode, flags=0, dont_inherit=False, optimize=-1)
*******************************************************************************

将 source 编译成代码或 AST 对象。代码对象可以被 `exec()`_ 或 `eval()`_ 执行。

- source -- 字符串或者AST（Abstract Syntax Trees）对象
- filename -- 代码文件名称，如果不是从文件读取代码则传递一些可辨认的值
- mode -- 指定编译代码的种类。可以指定为 exec, eval, single
- flags -- 变量作用域，局部命名空间，如果被提供，可以是任何映射对象
- flags 和 dont_inherit 控制在编译 source 时要用到哪个 future 语句
- optimize 实参指定编译器的优化级别；默认值 -1 选择与解释器的 -O 选项相同的优化级别。显式级别为 0（没有优化）、1（断言被删除）或 2（文档字符串也被删除）

::

    >>> str = '''
    ... for i in range(3):
    ...     print(i)
    ... '''
    >>> cc = compile(str, '', 'exec')
    >>> cc
    <code object <module> at 0x7fded2f3e810, file "", line 2>
    >>> exec(cc)
    0
    1
    2

    >>> str = '3 * 4 + 1'
    >>> ee = compile(str, 'abc', 'eval')
    >>> ee
    <code object <module> at 0x7fded2f44150, file "abc", line 1>
    >>> eval(ee)
    13

.. note::

    在 single 或 eval 模式编译多行代码字符串时，输入必须以至少一个换行符结尾。 这使得 code 模块更容易检测语句的完整性。

    在将足够大或者足够复杂的字符串编译成 AST 对象时，Python 解释器有可以因为 Python AST 编译器的栈深度限制而崩溃。 


.. _`delattr()`:

delattr(object, name)
************************************

如果对象允许，该函数将删除指定对象的属性。例如 delattr(x, 'foobar') 等价于 del x.foobar 。`setattr()`_ 相关的函数。

- object -- 一个 class 对象
- name -- 该字符串必须是对象的某个属性

::

    >>> class A:
    ...     x = 1
    ...     y = 2
    ... 
    >>> a = A()

    >>> print('x =', a.x)
    x = 1
    >>> print('y = ', a.y)
    y =  2

    >>> delattr(A, 'x')

    >>> print('x =', a.x)
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    AttributeError: 'A' object has no attribute 'x'

    # 不能用于删除实例中的属性
    >>> delattr(a, 'y')
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    AttributeError: y
    >>> a.y
    2


.. _`dict()`:

class dict(\*\*kwarg)
************************************

用于创建一个新的字典。其他的创建方式 class dict(mapping, \*\*kwarg)， class dict(iterable, \*\*kwarg)。

- \*\*kwargs -- 关键字
- mapping -- 元素的容器
- iterable -- 可迭代对象

::

    # 创建空字典
    >>> dict()
    {}

    # 将关键字创建新的字典
    >>> dict(a=1, b=2, c=3)
    {'a': 1, 'b': 2, 'c': 3}

    # 将映射创造新的字典
    >>> dict(zip(['a', 'b', 'c'], [1, 2, 3]))
    {'a': 1, 'b': 2, 'c': 3}

    # 将可迭代对象创建新的字典
    >>> dict([('a', 1), ('b', 2), ('c', 3)])
    {'a': 1, 'b': 2, 'c': 3}


.. _`dir()`:

dir([object])
************************************

如果没有实参，则返回当前本地作用域中的名称列表（变量、方法等）。如果有实参，它会尝试返回该对象的有效属性列表。返回的列表按字母表排序。

默认的 dir() 机制对不同类型的对象行为不同，它会试图返回最相关而不是最全的信息：

- 如果对象是模块对象，则列表包含模块的属性名称。
- 如果对象是类型或类对象，则列表包含它们的属性名称，并且递归查找所有基类的属性。
- 否则，列表包含对象的属性名称，它的类属性名称，并且递归查找它的类的所有基类的属性。

::

    >>> import struct
    >>> dir()
    ['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'struct']

    >>> dir(struct)
    ['Struct', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', '_clearcache', 'calcsize', 'error', 'iter_unpack', 'pack', 'pack_into', 'unpack', 'unpack_from']

    >>> class Shape:
    ...     def __dir__(self):
    ...         return ['area', 'perimeter', 'location']
    ... 
    >>> s = Shape()

    >>> dir(s)
    ['area', 'location', 'perimeter']


.. _`divmod()`:

divmod(a, b)
************************************

将两个参数执行除法并返回商和余数的元组。对于混合操作数类型，适用双目算术运算符的规则。对于整数，结果和 (a // b, a % b) 一致。

- a -- 数字类型，非复数
- b -- 数字类型，非复数

::

    >>> divmod(7, 2)
    (3, 1)

    >>> divmod(8, -2)
    (-4, 0)

    >>> divmod(8, 1.5)
    (5.0, 0.5)

    >>> divmod(8, 1.2)
    (6.0, 0.8000000000000003)


.. _`enumerate()`:

enumerate(iterable, start=0)
************************************

将一个可遍历的对象（如列表、元组或字符串）组合为枚举对象。一般用在 for 循环当中返回一个元组，里面包含一个计数值和通过迭代 iterable 获得的值。

- iterable -- 一个序列、迭代器或其他支持迭代的对象
- start -- 下标起始数值

::

    >>> abcd = ['a', 'b', 'c', 'd']
    >>> list(enumerate(abcd))
    [(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]
    
    >>> for n, i in enumerate(abcd, 5):
    ...     print(n, i)
    ... 
    5 a
    6 b
    7 c
    8 d


.. _`eval()`:

eval(expression[, globals[, locals]])
*******************************************************************************

执行一个字符串表达式，并返回表达式的值。

- expression -- 字符串表达式
- globals -- 变量作用域，全局命名空间，必须是一个字典对象
- locals -- 变量作用域，局部命名空间，可以是任何映射对象

提示： `exec()`_ 函数支持动态执行语句。 `globals()`_ 和 `locals()`_ 函数各自返回当前的全局和本地字典，因此您可以将它们传递给 `eval()`_ 或 `exec()`_ 来使用。

::

    >>> x = 1
    >>> eval('x + 1')
    2
    
    >>> eval('3 * 7')
    21


.. _`exec()`:

exec(object[, globals[, locals]])
************************************

相比于 eval，exec 可以执行更复杂的 Python 代码，支持动态执行 Python 代码。

- object -- 字符串表达式或者代码对象
- globals -- 变量作用域，全局命名空间，必须是一个字典对象
- locals -- 变量作用域，局部命名空间，可以是任何映射对象

::

    >>> x = 2
    >>> str = '''
    ... y = 3
    ... print(x * y)
    ... '''

    >>> exec(str)
    6

    >>> exec(str, {'x': 5})
    15

    # eval 不能动态的构建代码
    >>> eval(str, {'x': 5})
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    File "<string>", line 2
        y = 3
        ^
    SyntaxError: invalid syntax


.. _`filter()`:

filter(function, iterable)
************************************

根据条件过滤序列，并返回一个迭代器对象。

用 iterable 中函数 function 返回真的那些元素，构建一个新的迭代器。iterable 可以是一个序列，一个支持迭代的容器，或一个迭代器。如果 function 是 None ，则会假设它是一个身份函数，即 iterable 中所有返回假的元素会被移除。

- function -- 判断函数
- iterable -- 可迭代对象

.. note::

    filter(function, iterable) 相当于一个生成器表达式。
    当 function 不是 None 的时候为 (item for item in iterable if function(item))；
    function 是 None 的时候为 (item for item in iterable if item) 。

::

    >>> a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    >>> def odd(n):
    ...     return n % 2 == 1
    ...

    >>> filter(odd, a)
    <filter object at 0x7efca499f0b8>

    >>> list(filter(odd, a))
    [1, 3, 5, 7, 9]


.. _`float()`:

class float([x])
************************************

返回数字或字符串的浮点数。对于一个普通 Python 对象 x，float(x) 会委托给 ``x.__float__()`` 。 如果 ``__float__()`` 未定义则将回退至 ``__index__()`` 。

- x -- 整数、浮点数或字符串。字符串必须是包含十进制数字的字符串

::

    >>> float(123)
    123.0

    >>> float('+1.23')
    1.23

    >>> float('  -123\n')
    -123.0

    >>> float('1E6')
    1000000.0

    >>> float('-Infinity')
    -inf


.. _`format()`:

format(value[, format_spec])
************************************

根据 format_spec 格式化 value。其中 format_spec 的解释取决于 value 实参的类型，但是大多数内置类型使用标准格式化语法：格式规格迷你语言。

- value -- 整数、浮点数、字符串
- format_spec 内置类型标准格式化语法：格式规格迷你语言


::

    # 字符串左对齐
    >>> format('abc', '<20')
    'abc                 '

    # 字符串右对齐
    >>> format('abc', '>10')
    '       abc'

    # 字符串居中对齐
    >>> format('abc', '^20')
    '        abc         '

    # 字符串居中对齐，用 + 号填充空字符
    >>> format('abc', '+^30')
    '+++++++++++++abc++++++++++++++'


    # 将整数转换成二进制格式
    >>> format(28, 'b')
    '11100'

    # 将整数转换成八进制格式
    >>> format(28, 'o')
    '34'

    # 将整数转换成十六进制格式，使用大写字母表示 9 以上的数字
    >>> format(28, 'X')
    '1C'

    # 四舍五入小数点后两位
    >>> format(3.1415926, '.3')
    '3.14'


.. _`getattr()`:

getattr(object, name[, default])
************************************

返回类对象属性的值。例如， ``getattr(x, 'foobar')`` 等同于 ``x.foobar`` 。如果指定的属性不存在，且提供了 default 值，则返回它，否则触发 AttributeError。

- object -- 对象
- name -- 字符串，对象的属性
- default -- 默认返回值

::

    >>> class A:
    ...    bar = 1
    ... 
    >>> a = A()

    >>> getattr(a, 'bar')
    1

    >>> getattr(a, 'bar', 5)
    1

    >>> getattr(a, 'abc')
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    AttributeError: 'A' object has no attribute 'abc'

    >>> getattr(a, 'abc', 5)
    5


.. _`globals()`:

globals()
************************************

以字典类型返回当前位置的全部全局变量。这总是当前模块的字典（在函数或方法中，不是调用它的模块，而是定义它的模块）。

::

    >>> globals()
    {'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>}

    >>> a = 'aaaaaaaaaaa'
    >>> b = 'bbbbbbbbbbb'
    >>> c = 'ccccccccccc'
    >>> globals()
    {'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, 'a': 'aaaaaaaaaaa', 'b': 'bbbbbbbbbbb', 'c': 'ccccccccccc'}


.. _`hasattr()`:

hasattr(object, name)
************************************

判断对象是否包含对应的属性。如果包含对应的属性则返回 True，否则返回 False。（此功能是通过调用 getattr(object, name) 看是否有 AttributeError 异常来实现的。）

- object -- 对象
- name -- 字符串，属性名

::

    >>> class A:
    ...     x = 1
    ...     z = 3
    ... 
    >>> a = A()

    >>> hasattr(a, 'x')
    True

    >>> hasattr(a, 'abc')
    False


.. _`hash()`:

hash(object)
************************************

返回对象的哈希值（如果有的话）。哈希值是整数，在字典查找元素时用来快速比较字典的键。

注意：相同大小的数字变量有相同的哈希值（即使它们类型不同，如 1 和 1.0）。

- object -- 对象

::

    >>> hash('abc')
    -8467699554597568636

    >>> hash(100)
    100
    >>> hash(100.00)
    100

    >>> class A:
    ...    x = 1
    ...    y = 2
    ... 
    >>> hash(A)
    -9223372036853017173

    >>> a = A()
    >>> hash(a)
    8741473463318

    >>> hash((1, 2, 3))
    2528502973977326415

    # 列表和字典等可变对象不能计算哈希值
    >>> hash([1, 2, 3, 4])
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    TypeError: unhashable type: 'list'


.. _`help()`:

help([object])
************************************

启动 Python 内置的帮助系统（此函数主要在交互式中使用），类似于 Linux 系统中的 man 命令。如果没有实参，解释器控制台里会启动交互式帮助系统。如果实参是一个字符串，则在模块、函数、类、方法、关键字或文档主题中搜索该字符串，并在控制台上打印帮助信息。如果实参是其他任意对象，则会生成该对象的帮助页。


.. _`hex()`:

hex(x)
************************************

将整数转换为以 ``0x`` 开头的小写十六进制字符串。

- x -- 一个整数

::

    >>> hex(255)
    '0xff'

    >>> hex(-42)
    '-0x2a'


.. _`id()`:

id(object)
************************************

返回对象的“标识值”（内存地址）。该值是一个整数，在对象的生命周期中保证是唯一且恒定的。两个生命期不重叠的对象可能具有相同的 id 值。

::

    >>> a = 'abc'
    >>> id(a)
    139863576175984

    # a 和 b 其实是一个对象
    >>> b = a
    >>> id(b)
    139863576175984


.. _`input()`:

input([prompt])
************************************

接受一个标准输入数据，将其转换为字符串（除末尾的换行符之外）并返回。

- prompt -- 字符串（提示信息）

::

    >>> s = input('--> ')
    --> My name is Gavin
    >>> s
    'My name is Gavin'


.. _`int()`:

class int(x, base=10)
************************************

返回一个基于数字或字符串的整数对象，或者在未给出参数时返回 0。 如果 x 定义了 ``__int__()`` ，int(x) 将返回 ``x.__int__()`` 。 如果 x 定义了 ``__index__()`` ，它将返回 ``x.__index__()`` 。 如果 x 定义了 ``__trunc__()`` ，它将返回 ``x.__trunc__()`` 。 对于浮点数，将直接舍弃小数点后边的值。

- x -- 整数、浮点数或字符串
- base -- 进制数，默认十进制。

::

    >>> int(13)
    13

    >>> int(3.14)
    3

    >>> int('-50')
    -50

    # 字符串中可以包含空格
    >>> int ('  40  ')
    40

    # 只有字符串才可以指定进制时
    >>> int(13, 16)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: int() can't convert non-string with explicit base

    >>> int('13', 16)
    19


.. _`isinstance()`:

isinstance(object, classinfo)
************************************

判断一个对象是否是一个已知的类型，类似 type()。如果要判断两个类型是否相同推荐使用 isinstance()。

- object -- 实例对象。
- classinfo -- 直接或间接类名、基本类型，或是多个类名组成的元组

.. note::

    isinstance() 与 type() 区别：
    - type() 不会认为子类是一种父类类型，不考虑继承关系。
    - isinstance() 会认为子类是一种父类类型，考虑继承关系。

::

    >>> a = 'abc'
    >>> isinstance(a, str)
    True
    >>> isinstance(a, int)
    False

    >>> c = {'a': 1, 'b': 2}
    >>> isinstance(c, dict)
    True
    >>> isinstance(c, list)
    False
    
    # 传入元组
    >>> isinstance(c, (int, str, float))
    False


.. _`issubclass()`:

issubclass(class, classinfo)
************************************

判断参数 class 是否是类型参数 classinfo 的子类。

- class -- 类对象
- classinfo -- 类对象

::

    >>> class A:
    ...     pass
    ... 
    >>> class B(A):
    ...     pass
    ... 
    >>> issubclass(B, A)
    True


.. _`iter()`:

iter(object[, sentinel])
************************************

创建一个迭代器（iterator）对象。

- object -- 支持迭代的集合对象
- sentinel -- 如果传递了第二个参数，则参数 object 必须是一个可调用的对象（如函数），此时，iter 创建了一个迭代器对象，每次调用这个迭代器对象的__next__()方法时，都会调用 object。 

::

    >>> a = 'abcdef'

    # 字符串不是一个迭代器对象，会报错
    >>> a.__next__()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'str' object has no attribute '__next__'

    >>> b = iter(a)
    >>> b.__next__()
    'a'
    >>> b.__next__()
    'b'
    >>> b.__next__()
    'c'


.. _`len()`:

len(s)
************************************

返回对象的长度（元素个数）。

- s -- 对象。可以是序列（如 string、bytes、tuple、list 或 range 等）或集合（如 dictionary、set 或 frozen set 等）

::

    >>> len('abc')
    3

    >>> len([1, 2, 3, 4, 5, 6, 7, 8])
    8

    >>> len({'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5})
    5


.. _`list()`:

class list([iterable])
************************************

创建一个列表，虽然被称为函数，list 实际上是一种可变序列类型。

- iterable -- 元组或字符串

::

    >>> l = list()
    >>> l
    []

    >>> list('abcdefg')
    ['a', 'b', 'c', 'd', 'e', 'f', 'g']


.. _`locals()`:

locals()
************************************

以字典类型返回当前位置的全部局部变量。

::

    >>> locals()
    {'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>}
    >>> def abc():
    ...     a = 1
    ...     b = 2
    ...     c = 3
    ...     print(locals())
    ... 
    >>> abc()
    {'a': 1, 'b': 2, 'c': 3}


.. _`map()`:

map(function, iterable, ...)
************************************

返回一个将 function 应用于 iterable 中每一项并输出其结果的迭代器。

- function -- 函数
- iterable -- 一个或多个序列，当有多个序列时，最短的序列耗尽就将结束

::

    >>> def add(x):
    ...     return x*2
    ... 
    >>> list(map(add, [1, 2, 3, 4, 5]))
    [2, 4, 6, 8, 10]

    # 最短列表只有四个值，所以只计算了四次
    >>> a = map(lambda x, y: x*y, [1, 2, 3, 4, 5, 6, 7], [5, 5, 5, 5])
    >>> list(a)
    [5, 10, 15, 20]


.. _`max()`:

max(iterable, \*[, key, default])
************************************

返回可迭代对象中最大的元素，或者返回两个及以上实参中最大的元素。
比较规则可以参考官方排序指南：https://docs.python.org/zh-cn/3/howto/sorting.html

::

    >>> a = (90, 123, 25, 18)
    >>> max(a)
    123

    # 转换成字符串之后的最大值
    >>> max(a, key=str)
    90

    # 通过自定义函数，比较最后一位的最大值
    >>> max(a, key=lambda i: str(i)[-1])
    18


.. _`min()`:

min(iterable, \*[, key, default])
************************************

返回可迭代对象中最小的元素，或者返回两个及以上实参中最小的元素。与 max() 相反，具体操作详见 `max()`_ 。


.. _`next()`:

next(iterator[, default])
************************************

通过调用 iterator 的 ``__next__()`` 方法获取下一个元素。

- iterator -- 可迭代对象
- default -- 在没有下一个对象时返回的值，如果不设置迭代器耗尽时会触发 StopIteration 异常

如果迭代器耗尽，则返回给定的 default，如果没有默认值则触发 StopIteration。

::

    >>> a = iter('ab')
    >>> next(a)
    'a'
    >>> next(a)
    'b'
    >>> next(a)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    StopIteration

    >>> a = iter('ab')
    >>> next(a)
    'a'
    >>> next(a)
    'b'
    >>> next(a, 'no more')
    'no more'


.. _`oct()`:

oct(x)
************************************

将整数转换为以 ``0o`` 开头的八进制字符串。

- x -- 一个整数

::

    >>> oct(8)
    '0o10'

    >>> oct(-56)
    '-0o70'


.. _`open()`:

open()
************************************

打开一个文件，并返回文件对象。如果该文件不能打开，则触发 OSError。

**open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)** 参数很多，下边一一说明：

- file -- 必需，文件路径（相对或者绝对路径）
- mode -- 可选，指定打开文件的模式，默认值是 'r'
- buffering -- 设置缓冲策略
- encoding -- 设置解码或编码文件的编码，一般使用 utf8
- errors -- 报错级别，不能在二进制模式下使用
- newline -- 区分换行符（仅适用于文本模式）。可以是 None，''，'\n'，'\r' 和 '\r\n'。
- closefd -- 传入的 file 参数类型
- opener -- 指定自定义开启器

mode
====================================

mode 是一个可选字符串，用于指定打开文件的模式。可用的模式有：

==========   ==========
字符           意义
==========   ==========
'r'            读取（默认）
'w'            写入，并先截断文件
'x'            排它性创建，如果文件已存在则失败
'a'            写入，如果文件存在则在末尾追加
'b'            二进制模式
't'            文本模式（默认）
'+'            打开用于更新（读取与写入）
==========   ==========

默认模式为 'r' (打开用于读取文本，与 'rt' 同义)。 模式 'w+' 与 'w+b' 将打开文件并清空内容。 模式 'r+' 与 'r+b' 将打开文件并不清空内容。

.. note::

    Python 不依赖于底层操作系统的文本文件概念;所有处理都由 Python 本身完成，因此与平台无关。 


errors
====================================

errors 是一个可选的字符串参数，用于指定如何处理编码和解码错误，这不能在二进制模式下使用。可以使用各种标准错误处理程序，但是使用 ``codecs.register_error()`` 注册的任何错误处理名称也是有效的。标准名称包括:

- 'strict' 如果存在编码错误会引发 ValueError 异常。 默认值 None 具有相同的效果。
- 'ignore' 忽略错误。请注意，忽略编码错误可能会导致数据丢失。
- 'replace' 会将替换标记（例如 '?' ）插入有错误数据的地方。
- 'surrogateescape' 将任何不正确的字节作为 Unicode 专用区中的代码点，范围从U+DC80到U+DCFF。这对于处理未知编码的文件很有用。
- 只有在写入文件时才支持 'xmlcharrefreplace'。编码不支持的字符将替换为相应的 XML 字符引用 ``&#nnn;`` 。
- 'backslashreplace' 用 Python 的反向转义序列替换格式错误的数据。
- 'namereplace' 只在编写时支持，用 \N{...} 转义序列替换不支持的字符。

::

    >>>f = open('test.txt')
    >>> f.read()
    'one\ntwo\n'


.. _`ord()`:

ord(c)
************************************

返回 c 参数的 Unicode 码位的字符串格式。这是 `chr()`_ 的逆函数。

- c -- 字符

::

    >>> ord('a')
    97

    >>> ord('€')
    8364


.. _`pow()`:

pow(base, exp[, mod])
************************************

返回 base 的 exp 次幂，等价于乘方运算符: ``base**exp`` ；如果 mod 存在，则返回 base 的 exp 次幂对 mod 取余，等价于 pow(base, exp) % mod 。

- base -- 数值类型
- exp -- 数值类型
- mod -- 数值类型

::

    >>> pow(8, 2)
    64

    >>> pow(8, 2, 5)
    4


.. _`print()`:

print(\*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
******************************************************************************

将 objects 打印到 file 指定的文本流，最常见的一个函数。

- objects -- 复数，可以一次输出多个对象。
- sep -- 设置间隔字符，默认值是一个空格。
- end -- 设置结尾字符。默认值是换行符 \n，
- file -- 要写入的文件对象。须是具有 write(string) 方法的对象
- flush -- 输出是否被缓存通常决定于 file，如果为 True，流会被强制刷新。

::

    >>> print(1)
    1
    >>> print(1, 'a')
    1 a
    >>> print('www', 'dongxg', 'top', sep='.')
    www.dongxg.top

    >>> l = ['a', 'b', 'c', 'd']
    >>> for i in l:
    ...     print(i)
    ... 
    a
    b
    c
    d
    >>> for i in l:
    ...     print(i, end='')
    ... 
    abcd


.. _`range()`:

class range(start, stop[, step])
************************************

虽然被称为函数，但 range 实际上是一个不可变的序列类型。

- start: 计数从 start 开始。默认从 0 开始。例如 range(5) 等价于 range(0, 5)
- stop: 计数到 stop 结束，但不包括 stop
- step：步长，默认为 1

::

    >>> list(range(5))
    [0, 1, 2, 3, 4]

    >>> list(range(0, 5))
    [0, 1, 2, 3, 4]

    >>> list(range(0, 5, 2))
    [0, 2, 4]


.. _`reversed()`:

reversed(seq)
************************************

返回一个反向的迭代器。 

- seq -- 要转换的序列，可以是 tuple, string, list 或 range

::

    >>> list(reversed('Python'))
    ['n', 'o', 'h', 't', 'y', 'P']

    >>> list(reversed([1, 2, 3, 4, 5, 6]))
    [6, 5, 4, 3, 2, 1]


.. _`round()`:

round(number[, ndigits])
************************************

返回浮点数的四舍五入值，准确的说保留值将保留到离上一位更近的一端（四舍六入）。

- number -- 数字表达式。
- ndigits -- 保留小数点的位数，默认值为 0

::

    >>> round(3.1415926, 2)
    3.14

    >>> round(3.1415926, 4)
    3.1416

.. note::

    有时对浮点数执行 round() 操作可能会令人惊讶，如

    ::

        >>> round(2.675, 2)
        2.67

    不会返回期望的 2.68。 
    这不是程序错误：这一结果是由于大多数十进制小数实际上都不能以浮点数精确地表示。所以对精度要求高的情况下，不建议使用该函数。


.. _`set()`:

class set([iterable])
************************************

创建一个集合（无序不重复的元素集，相当于字典中键的集合）。可以删除重复数据，还可以计算交集、差集、并集等。

- iterable -- 可迭代对象

::

    >>> x = set('good')
    >>> x
    {'o', 'd', 'g'}
    >>> y = set('google')
    >>> y
    {'e', 'o', 'l', 'g'}

    # 交集
    >>> x & y
    {'o', 'g'}

    # 并集
    >>> x | y
    {'o', 'e', 'd', 'l', 'g'}

    # 差集
    >>> x - y
    {'d'}
    >>> y - x
    {'e', 'l'}


.. _`setattr()`:

setattr(object, name, value)
************************************

此函数对应函数 `getattr()`_ ，用于设置类对象的属性值，该属性不一定要存在。例如， ``setattr(x, 'foobar', 123)`` 等价于 ``x.foobar = 123`` 。

- object -- 对象
- name -- 字符串，对象属性
- value -- 属性值

::

    >>> class A:
    ...     bar = 1
    ... 
    >>> a = A()

    # getattr() 获取属性值
    >>> getattr(a, 'bar')
    1

    >>> setattr(a, 'bar', 3)
    >>> a.bar
    3

    # 属性不存在时，创建新属性并赋值
    >>> a.new
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'A' object has no attribute 'new'

    >>> setattr(a, 'new', 5)
    >>> a.new
    5


.. _`slice()`:

class slice(start, stop[, step])
************************************

返回一个切片对象（类似于正则表达式中的匹配语句），可以应用在所以序列中。

- start -- 起始位置，默认值为 None
- stop -- 结束位置
- step -- 间距，默认值为 None

::

    >>> a = slice(5)
    >>> a
    slice(None, 5, None)

    >>> l = list(range(10))
    >>> l
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

    >>> l[a]
    [0, 1, 2, 3, 4]

    >>> 'abcdefg'[a]
    'abcde'


.. _`sorted()`:

sorted(iterable, \*, key=None, reverse=False)
*******************************************************************************

对所有可迭代的对象进行排序，并返回一个新的排序列表。

- iterable -- 可迭代对象
- key -- 带有单个参数的函数，每个元素中用于比较的键（如 key=str.lower），默认值为 None
- reverse -- 排序规则，False 升序（默认），True 降序

::

    >>> a = list('abcdABCD')
    >>> a
    ['a', 'b', 'c', 'd', 'A', 'B', 'C', 'D']

    >>> sorted(a)
    ['A', 'B', 'C', 'D', 'a', 'b', 'c', 'd']

    # 以降序排序
    >>> sorted(a, reverse=True)
    ['d', 'c', 'b', 'a', 'D', 'C', 'B', 'A']

    # 不区分字符大小写
    >>> sorted(a, key=str.lower)
    ['a', 'A', 'b', 'B', 'c', 'C', 'd', 'D']


    >>> a = [1, '3', 4, '21']

    # 不能对不同类型的值排序
    >>> sorted(a)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: '<' not supported between instances of 'str' and 'int'

    # 折中的解决办法
    >>> sorted(a, key=lambda i: int(i))
    [1, '3', 4, '21']


.. _`staticmethod()`:

@staticmethod
************************************

将方法转换为静态方法。该方法不强制要求传递参数，如下声明一个静态方法：

::

    class C:
        @staticmethod
        def f(arg1, arg2, ...): ...

@staticmethod 这样的形式称为函数的 decorator，静态方法的调用可以在类上进行 (例如 C.f()) 也可以在实例上进行 (例如 C().f())。

::

    >>> class C:
    ...     @staticmethod
    ...     def f():
    ...         print('good')
    ... 
    >>> C.f()
    good
    >>> cobj = C()
    >>> cobj.f()
    good


.. _`str()`:

class str(object=b'', encoding='utf-8', errors='strict')
*******************************************************************************

将对象转化为字符串，并返回。如果未提供 object 则返回空字符串。

- object -- 对象
- encoding -- 设置字符串编码，默认为 'utf-8'
- errors -- 容错级别

::

    >>> str(12)
    '12'

    >>> str([1, 2, 3, 4, 5])
    '[1, 2, 3, 4, 5]'

    >>> str({'a': 1, 'b': 2})
    "{'a': 1, 'b': 2}"


.. _`sum()`:

sum(iterable, /, start=0)
************************************

计算序列中值的总和。注意：序列中的值只能是数字。

- iterable -- 可迭代对象，如：列表、元组、集合
- start -- 指定相加的参数，默认为 0

对某些用例来说，存在 sum() 的更好替代。 拼接字符串序列的更好更快方式是调用 ''.join(sequence)。 要以扩展精度对浮点值求和，请参阅 math.fsum()。 要拼接一系列可迭代对象，请考虑使用 itertools.chain()。

::

    >>> sum([1, 2, 3])
    6

    # 计算列表总和后再加 4
    >>> sum([1, 2, 3], 4)
    10


.. _`super()`:

super([type[, object-or-type]])
************************************

调用父类（超类）的方法。super 是用来解决多重继承问题的，直接用类名调用父类方法在使用单继承的时候没问题，但是如果使用多继承，会涉及到查找顺序（MRO）、重复调用（钻石继承）等种种问题。

- type -- 子类对象
- object-or-type -- 父类对象，一般是 self

::

    class Foo:
        def __init__(self):
            self.parent = "I'm the parent."
            print('Parent')
        
        def bar(self, message):
            print('{} from Parent'.format(message))

    class FooChild(Foo):
        def __init__(self):
            # 调用父类 Foo 对象
            super(FooChild, self).__init__()
            
            # 可以不带参数
            super().bar('abcdefg')
            print('Child')


    # 输出结果：
    Parent
    abcd from Parent
    Child


.. _`tuple()`:

class tuple([iterable])
************************************

创建一个元组。虽然被称为函数，但 tuple 实际上是一个不可变的序列类型。

- iterable -- 可迭代对象，序列

::

    >>> tuple('abcde')
    ('a', 'b', 'c', 'd', 'e')

    >>> tuple([1, 2, 3, 4, 5])
    (1, 2, 3, 4, 5)

    >>> tuple(range(8))
    (0, 1, 2, 3, 4, 5, 6, 7)


.. _`type()`:

class type(name, bases, dict)
************************************

返回对象的类型。通常与 ``object.__class__`` 所返回的对象相同。

- name -- 类对象
- bases -- 基类的元组
- dict -- 字典，类内定义的命名空间变量

推荐使用 `isinstance()`_ 函数来检测对象的类型，因为它会考虑子类的情况。

::

    >>> type(1)
    <class 'int'>

    >>> type('abc')
    <class 'str'>

    >>> type(3.14)
    <class 'float'>

    # 判断类型是否相等
    >>> type(1) == int
    True


    >>> class X:
    ...     a = 1
    ... 
    >>> type(X)
    <class 'type'>

    # 三个参数同时使用，创建一个新的类型 X
    >>> X = type('X', (object, ), dict(a=1))
    >>> X
    <class '__main__.X'>


.. _`vars()`:

vars([object])
************************************

返回对象（模块、类、实例）的属性和属性值的字典对象。

- object -- 类对象

不带参数时，vars() 的行为类似 `locals()`_ 。 请注意，locals 字典仅对于读取起作用，因为对 locals 字典的更新会被忽略。

::

    >>> vars()
    {'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>}

    >>> class A:
    ...    a = 1
    ...    b = 2
    ... 
    >>> vars(A)
    mappingproxy({'__module__': '__main__', 'a': 1, 'b': 2, '__dict__': <attribute '__dict__' of 'A' objects>, '__weakref__': <attribute '__weakref__' of 'A' objects>, '__doc__': None})

    # 实例对象返回空字典
    >>> a = A()
    >>> vars(a)
    {}


.. _`zip()`:

zip(\*iterables)
************************************

将多个可迭代对象中对应的元素打包成一个个元组，然后返回这些元组的迭代器，当所输入可迭代对象中最短的一个被耗尽时，迭代器将停止迭代。 这样做的好处是节约了不少的内存。

- iterabl -- 一个或多个迭代器对象。不带参数时，返回一个空迭代器；只有一个参数时，返回一个单元组成的迭代器。 

::

    >>> x = [1, 2, 3]
    >>> y = [4, 5, 6]
    >>> list(zip(x, y))
    [(1, 4), (2, 5), (3, 6)]

    # 元素个数与最短的一致
    >>> z = 'abcdefg'
    >>> list(zip(x, z))
    [(1, 'a'), (2, 'b'), (3, 'c')]
