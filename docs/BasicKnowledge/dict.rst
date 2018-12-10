字典
#####################

字典是另一种可变容器模型，且可存储任意类型对象。

字典的每个键值(key=>value)对用冒号(:)分割，每个对之间用逗号(,)分割，整个字典包括在花括号({})中,

键必须是唯一的，但值则不必。

值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。

格式如下所示：

.. highlight:: none

::

    d = {key1 : value1, key2 : value2 }


一个简单的字典实例：

::

    dict = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}

    # 也可如此创建字典：
    dict1 = { 'abc': 456 }
    dict2 = { 'abc': 123, 98.6: 37 }


字典的基本操作
**********************

访问字典里的值
=====================

把相应的键放入到方括号中，如下实例:

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}

    >>> print ("dict['Name']: ", dict['Name'])
    dict['Name']:  Runoob

    >>> print ("dict['Age']: ", dict['Age'])
    dict['Age']:  7

    # 如果用字典里没有的键访问数据，会输出错误如下：
    >>> print ("dict['Alice']: ", dict['Alice'])

    Traceback (most recent call last):
      File "test.py", line 5, in <module>
        print ("dict['Alice']: ", dict['Alice'])
    KeyError: 'Alice'


修改字典
=================

向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例:

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}

    # 更新 Age
    >>> dict['Age'] = 8

    # 添加信息
    >>> dict['School'] = "ltz"

    >>> print ("dict['Age']: ", dict['Age'])
    dict['Age']:  8

    >>> print ("dict['School']: ", dict['School'])
    dict['School']:  ltz


删除字典元素
===================

能删单一的元素也能清空字典，清空只需一项操作。

显示删除一个字典用del命令，如下实例：

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}

    # 删除键 'Name'
    >>> del dict['Name']

    # 清空字典
    >>> dict.clear()

    # 删除字典
    >>> del dict

字典键的特性
====================

字典值可以是任何的 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。

两个重要的点需要记住：

1. 不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住，如下实例：

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Name': 'zwei'}

    >>> print ("dict['Name']: ", dict['Name'])

    dict['Name']:  zwei

2. 键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行，如下实例：

::

    >>> dict = {['Name']: 'Runoob', 'Age': 7}

    # 以上实例输出结果：
    >>> print ("dict['Name']: ", dict['Name'])

    Traceback (most recent call last):
      File "test.py", line 3, in <module>
        dict = {['Name']: 'Runoob', 'Age': 7}
    TypeError: unhashable type: 'list'


字典内置函数
***********************

Python字典包含了以下内置函数：

len(dict)
====================

计算字典元素个数，即键的总数。

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
    >>> len(dict)
    3

str(dict)
=====================

输出字典，以可打印的字符串表示。

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
    >>> str(dict)
    "{'Name': 'Runoob', 'Class': 'First', 'Age': 7}"

type(variable)
======================

返回输入的变量类型，如果变量是字典就返回字典类型。

::

    >>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
    >>> type(dict)
    <class 'dict'>

Python字典包含了以下内置方法：
******************************

===========================   ===============
方法                              描述
===========================   ===============
radiansdict.clear()              删除字典内所有元素
radiansdict.copy()               返回一个字典的浅复制
radiansdict.fromkeys()           创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值
radiansdict.get()                返回指定键的值，如果值不在字典中返回default值
key in dict                      如果键在字典dict里返回true，否则返回false
radiansdict.items()              以列表返回可遍历的(键, 值) 元组数组
radiansdict.keys()               返回一个迭代器，可以使用 list() 来转换为列表
radiansdict.setdefault()         和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default
radiansdict.update()             把字典dict2的键/值对更新到dict里
radiansdict.values()             返回一个迭代器，可以使用 list() 来转换为列表
pop()                            删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。
popitem()                        随机返回并删除字典中的一对键和值(一般删除末尾对)。
===========================   ===============

clear()方法
=================

Python 字典 clear() 函数用于删除字典内所有元素。

语法
-------------

::

    dict.clear()

参数
--------------

* NA。

返回值
-------------

该函数没有任何返回值。


copy()方法
=====================

Python 字典 copy() 函数返回一个字典的浅复制。

语法
-----------------

::

    dict.copy()

参数
-----------------

* NA。

返回值
----------------

返回一个字典的浅复制。


fromkeys()方法
======================

fromkeys() 函数用于创建一个新字典，以序列 seq 中元素做字典的键，value 为字典所有键对应的初始值。

语法
----------------

::

    dict.fromkeys(seq, value)

参数
-----------------

* seq - 字典键值列表。
* value - 可选参数, 设置键序列（seq）的值。

返回值
-------------

该方法返回列表。


get() 方法
=================

Python 字典 get() 函数返回指定键的值，如果值不在字典中返回默认值。

语法
-------------

::

    dict.get(key, default=None)

参数
--------------

* key - 字典中要查找的键。
* default - 如果指定键的值不存在时，返回该默认值值。

返回值
-------------

返回指定键的值，如果值不在字典中返回默认值 None。


items() 方法
====================

Python 字典 items() 方法以列表返回可遍历的(键, 值) 元组数组。

语法
-------------

::

    dict.items()

参数
-------------

* NA。

返回值
-------------

返回可遍历的(键, 值) 元组数组。


keys() 方法
===================

Python3 字典 keys() 方法返回一个迭代器，可以使用 list() 来转换为列表。

语法
-----------

::

    dict.keys()

参数
-----------

* NA。

返回值
-----------

返回一个迭代器。


setdefault() 方法
=======================

Python 字典 setdefault() 方法和get()方法类似, 如果键不已经存在于字典中，将会添加键并将值设为默认值。

语法
----------------

::

    dict.setdefault(key, default=None)

参数
------------

* key -- 查找的键值。
* default -- 键不存在时，设置的默认键值。

返回值
-----------

如果 key 在 字典中，返回对应的值。如果不在字典中，则插入 key 及设置的默认值 default，并返回 default ，default 默认值为 None。

update() 方法
===================

Python 字典 update() 函数把字典参数 dict2 的 key/value(键/值) 对更新到字典 dict 里。

语法
---------------

::

    dict.update(dict2)

参数
-----------

* dict2 -- 添加到指定字典dict里的字典。

返回值
-----------

该方法没有任何返回值。


values() 方法
=====================

Python 字典 values() 方法返回一个迭代器，可以使用 list() 来转换为列表，列表为字典中的所有值。

语法
-------------

::

    dict.values()

参数
-------------

* NA。

返回值
------------

返回迭代器。


pop() 方法
================

Python 字典 pop() 方法删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。

语法
-------------

::

    pop(key[,default])

参数
----------

* key: 要删除的键值
* default: 如果没有 key，返回 default 值

返回值
-----------

返回被删除的值。


popitem() 方法
===================

Python 字典 popitem() 方法随机返回并删除字典中的一对键和值(一般删除末尾对)。

如果字典已经为空，却调用了此方法，就报出KeyError异常。

语法
-----------

::

    popitem()

参数
---------

* 无

返回值
--------

返回一个键值对(key,value)形式。
