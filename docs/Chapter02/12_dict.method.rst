字典方法
####################################

与其他内置类型一样，字典也有方法。字典的方法很有用，但其使用频率可能没有列表和字符串的方法那样高。

- `dict.clear()`_  清空字典，删除字典中所有的项
- `dict.copy()`_  返回原字典的浅复制
- `dict.fromkeys()`_  使用指定的键创建一个新字典，其中所有值都为初始值
- `dict.get()`_  返回指定键的值，如果键不存在默认返回 None
- `dict.items()`_  返回由字典项组成的一个新视图
- `dict.keys()`_  返回由字典键组成的一个新视图
- `dict.pop()`_  删除指定的键键，并返回其值
- `dict.popitem()`_  从字典中删除并返回一个 (键, 值) 对
- `dict.setdefault()`_  返回键的值，如果键不存在则添加，并返回 None
- `dict.update()`_  使用一个字典中的项来更新另一个字典（或合并两个字典）
- `dict.values()`_  返回由字典值组成的一个新视图




.. _`dict.clear()`:

dict.clear()
************************************

清空字典，删除字典中所有的项。

.. highlight:: none

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.clear()
    >>> d
    {}


.. _`dict.copy()`:

dict.copy()
************************************

返回原字典的浅复制。关于深浅复制的区别请参考 ``list.copy()`` 。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> a = d.copy()
    >>> a['name'] = 'Lucy'
    >>> a
    {'name': 'Lucy', 'age': 45}
    >>> d
    {'name': 'Gavin', 'age': 45}


.. _`dict.fromkeys()`:

dict.fromkeys(iterable[, value])
************************************

使用来自 iterable 的键创建一个新字典，并将键值设为 value（默认为 None）。fromkeys() 属于类方法，会返回一个新字典。

::

    >>> a = ['name', 'age']

    >>> {}.fromkeys(a)
    {'name': None, 'age': None}

    >>> dict.fromkeys(a)
    {'name': None, 'age': None}

    # 设定默认值
    >>> dict.fromkeys(a, True)
    {'name': True, 'age': True}

    # 不会对原字典做任何修改
    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.fromkeys(a)
    {'name': None, 'age': None}
    >>> d
    {'name': 'Gavin', 'age': 45}


.. _`dict.get()`:

dict.get(key[, default])
************************************

如果 key 存在于字典中则返回 key 的值，否则返回 default（None）。此方法为访问字典项提供了宽松的环境，绝不会引发 KeyError。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.get('name')
    'Gavin'

    >>> d.get('abc')

    >>> d.get('abc', False)
    False


.. _`dict.items()`:

dict.items()
************************************

返回由字典项（其中每个元素都为 (key, value) 的形式）组成的一个新视图。参见 `视图对象文档`_ 。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> a = d.items()
    >>> len(a)
    2

    >>> for k, v in a:
    ...     print(k, v)
    ... 
    name Gavin
    age 45


.. _`dict.keys()`:

dict.keys()
************************************

返回由字典键组成的一个新视图。参见 `视图对象文档`_ 。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.keys()
    dict_keys(['name', 'age'])


.. _`dict.pop()`:

dict.pop(key[, default])
************************************

如果 key 存在于字典中则将其移除并返回其值，否则返回 default。如果 default 未给出且 key 不存在于字典中，则会引发 KeyError。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.pop('name')
    'Gavin'

    >>> d.pop('abc', False)
    False

    >>> d.pop('abc')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'abc'


.. _`dict.popitem()`:

dict.popitem()
************************************

从字典中移除并返回一个 (键, 值) 对。键值对会按 LIFO 的顺序被返回。如果字典为空，调用 popitem() 将引发 KeyError。

popitem() 适用于对字典进行消耗性的迭代，这样无需先获取键列表就可以对字典进行操作。

在 3.7 版更改: 现在会确保采用 LIFO 顺序。 在之前的版本中，popitem() 会返回一个任意的键/值对。


::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.popitem()
    ('age', 45)
    >>> d.popitem()
    ('name', 'Gavin')

    >>> d.popitem()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'popitem(): dictionary is empty'


.. _`dict.setdefault()`:

dict.setdefault(key[, default])
************************************

返回字典中 key 的值，如果 key 不存在，则添加 key: default 的字典项，并返回 default（默认为 None）。


::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.setdefault('name')
    'Gavin'

    >>> d.setdefault('abc')
    >>> d
    {'name': 'Gavin', 'age': 45, 'abc': None}

    >>> d.setdefault('cbd', True)
    True
    >>> d
    {'name': 'Gavin', 'age': 45, 'abc': None, 'cbd': True}


.. _`dict.update()`:

dict.update([other])
************************************

使用 other 的键/值对更新字典，如果原字典中 key 存在，则更新键的值。否则则将键/值对添加到原字典中（合并字典）。返回 None。

update() 接受另一个字典对象，或者一个包含键/值对（以长度为二的元组或其他可迭代对象表示）的可迭代对象。 如果给出了关键字参数，则会以其所指定的键/值对更新字典: d.update(red=1, blue=2)。


::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> u = {'name': 'Lucy', 'height': 168}
    >>> d.update(u)
    >>> d
    {'name': 'Lucy', 'age': 45, 'height': 168}

    >>> d.update(name='Gavin')
    >>> d
    {'name': 'Gavin', 'age': 45, 'height': 168}

    >>> d.update([('height', 180), ('weight', 75)])
    >>> d
    {'name': 'Gavin', 'age': 45, 'height': 180, 'weight': 75}


.. _`dict.values()`:

dict.values()
************************************

返回由字典值组成的一个新视图。参见 `视图对象文档`_ 。

在 3.7 版更改: 字典顺序会确保为插入顺序。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> d.values()
    dict_values(['Gavin', 45])

    >>> d['height'] = 185
    >>> d.values()
    dict_values(['Gavin', 45, 185])


.. note::

    两个 dict.values() 视图之间的相等性比较将总是返回 False。这在 dict.values() 与其自身比较时也同样适用:

    ::

        >>> d = {'a': 1}
        >>> d.values() == d.values()
        False


.. _`视图对象文档`:

视图对象文档
************************************

由 `dict.keys()`_ , `dict.values()`_ 和 `dict.items()`_ 所返回的对象是视图对象。该对象提供字典条目的一个动态视图，这意味着当字典改变时，视图也会相应改变。

::

    >>> d = {'name': 'Gavin', 'age': 45}
    >>> a = d.keys()
    >>> a
    dict_keys(['name', 'age'])

    # 字典改变时，视图也会改变
    >>> d['height'] = 185
    >>> a
    dict_keys(['name', 'age', 'height'])


字典视图可以被迭代以产生与其对应的数据，并支持成员检测：

- len(dictview)  返回字典中的条目数。
- iter(dictview)  返回字典中的键、值或项的迭代器。在 3.7 版更改: 字典顺序会确保为插入顺序。
- x in dictview  如果 x 是对应字典中存在的键、值或项，则返回 True。


一个使用字典视图的示例:

::

    >>> dishes = {'eggs': 2, 'sausage': 1, 'bacon': 1, 'spam': 500}
    >>> keys = dishes.keys()
    >>> values = dishes.values()

    >>> # iteration
    >>> n = 0
    >>> for val in values:
    ...     n += val
    >>> print(n)
    504

    >>> # keys and values are iterated over in the same order (insertion order)
    >>> list(keys)
    ['eggs', 'sausage', 'bacon', 'spam']
    >>> list(values)
    [2, 1, 1, 500]

    >>> # view objects are dynamic and reflect dict changes
    >>> del dishes['eggs']
    >>> del dishes['sausage']
    >>> list(keys)
    ['bacon', 'spam']

    >>> # set operations
    >>> keys & {'eggs', 'bacon', 'salad'}
    {'bacon'}
    >>> keys ^ {'sausage', 'juice'}
    {'juice', 'sausage', 'bacon', 'spam'}
