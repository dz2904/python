集合方法
####################################

由于集合中的元素不能重复出现，所以集合可以执行并集、交集、差集等常见的的数学操作。其中修改的操作不适用于 frozenset 对象。

- `set.add()`_  添加元素
- `set.clear()`_  清空集合
- `set.copy()`_  返回原集合的浅拷贝
- `set.difference()`_  返回多个集合的差集
- `set.difference_update()`_  用差集更新集合
- `set.discard()`_  删除指定元素
- `set.intersection()`_  返回多个集合的交集
- `set.intersection_update()`_  用交集更新集合
- `set.isdisjoint()`_  判断多个集合是否有相交元素
- `set.issubset()`_  判断集合是否为另一个集合的子集
- `set.issuperset()`_  判断集合是否为另一个集合的超集
- `set.pop()`_  随机删除一个元素
- `set.remove()`_  删除指定元素
- `set.symmetric_difference()`_  返回一个新集合，只保留不共同存在的元素
- `set.symmetric_difference_update()`_  更新集合，只保留不共同存在的元素
- `set.union()`_  返回多个集合的并集
- `set.update()`_  用并集更新集合




.. _`set.add()`:

set.add(elem)
************************************

将元素 elem 添加到集合中。如果元素已在集合中，则不执行任何操作。


.. highlight:: none

::

    >>> s = set('abc')
    >>> s.add('d')
    >>> s
    {'d', 'a', 'c', 'b'}

    # 重复元素不会添加
    >>> s.add('a')
    >>> s
    {'d', 'a', 'c', 'b'}


.. _`set.clear()`:

set.clear()
************************************

清空集合，删除集合中所有元素。


::

    >>> s = set('abc')
    >>> s.clear()
    >>> s
    set()


.. _`set.copy()`:

set.copy()
************************************

返回原集合的浅拷贝。关于深浅复制的区别请参考 ``list.copy()`` 。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = s.copy()
    >>> a.add('d')
    >>> a
    {'d', 'a', 'c', 'b'}
    >>> s
    {'a', 'c', 'b'}


.. _`set.difference()`:

set.difference(*others)
************************************

返回集合的差集，即返回的集合元素包含在第一个集合中，但不包含在第二个集合中。


::

    >>> d = {'a', 'b', 'c'}
    >>> s = {'b', 'e', 'f'}

    >>> s.difference(d)
    {'f', 'e'}

    # 差集运算符为 -
    >>> s - d
    {'f', 'e'}

    >>> a = {'b', 'd', 'e'}
    >>> s.difference(d, a)
    {'f'}


.. _`set.difference_update()`:

set.difference_update(*others)
************************************

更新集合，移除其中也存在于 others 中的元素（即移除两个集合中共同的元素）。

.. note::

    该方法与与 ``difference()`` 的主要区别是， ``difference()`` 返回一个新集合，而 ``difference_update()`` 会直接在原来的集合中修改。


::

    >>> d = {'a', 'c', 'b'}
    >>> s = {'b', 'f', 'e'}

    >>> s.difference_update(d)
    >>> s
    {'f', 'e'}


.. _`set.discard()`:

set.discard(elem)
************************************

如果元素 elem 存在于集合中则将其移除，如果 elem 不存在，则返回 None。

.. note::

    该方法与 ``remove()`` 的主要区别是， ``remove()`` 在移除一个不存在的元素时会发生错误。


::

    >>> s = {'b', 'e', 'f'}
    >>> s.discard('f')
    >>> s
    {'b', 'e'}

    >>> s.discard('abc')
    >>> s
    {'b', 'e'}


.. _`set.intersection()`:

set.intersection(*others)
************************************

返回一个新集合，其中包含原集合以及 others 指定的所有集合中都包含的元素，即交集。

::

    >>> d = {'a', 'c', 'b'}
    >>> s = {'b', 'f', 'e'}

    >>> s.intersection(d)
    {'b'}

    # 交集运算符为 &
    >>> s & d
    {'b'}

    >>> a = {'d', 'b', 'f'}
    >>> s.intersection(d, a)
    {'b'}


.. _`set.intersection_update()`:

set.intersection_update(*others)
************************************

更新集合，只保留其中在所有 others 中也存在的元素，即交集。

::

    >>> d = {'a', 'c', 'b'}
    >>> s = {'b', 'f', 'e'}

    >>> s.intersection_update(d)
    >>> s
    {'b'}


.. _`set.isdisjoint()`:

set.isdisjoint(other)
************************************

如果集合中没有与 other 共有的元素则返回 True（判断多个集合是否有相交元素）。当两个集合的交集不为空集合时，返回 False。

::

    >>> d = {'a', 'c', 'b'}
    >>> s = {'b', 'f', 'e'}

    >>> s.isdisjoint(d)
    False
    >>> s & d
    {'b'}

    >>> a = {'x', 'y', 'z'}
    >>> s.isdisjoint(a)
    True


.. _`set.issubset()`:

set.issubset(other)
************************************

判断集合中的每个元素都在 other 之中（集合是否为另一个集合的子集），如果是则返回 True，否则返回 False。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'a', 'c'}

    >>> a.issubset(s)
    True

    >>> s.issubset(a)
    False

    >>> a <= s
    True


.. _`set.issuperset()`:

set.issuperset(other)
************************************

判断是否 other 中的每个元素都在集合之中，如果是则返回 True，否则返回 False。与 ``issubset()`` 操作相反。


::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'a', 'c'}

    >>> a.issuperset(s)
    False

    >>> s.issuperset(a)
    True

    >>> s >= a
    True


.. _`set.pop()`:

set.pop()
************************************

从集合中删除并返回任意一个元素。 如果集合为空则会引发 KeyError。

::

    >>> a = {'a', 'b', 'c'}

    >>> a.pop()
    'a'
    >>> a.pop()
    'c'
    >>> a.pop()
    'b'

    >>> a.pop()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'pop from an empty set'


.. _`set.remove()`:

set.remove(elem)
************************************

从集合中移除元素 elem。 如果 elem 不存在于集合中则会引发 KeyError。在删除集合元素时建议使用 `set.discard()`_ 。

::

        >>> s = {'a', 'b', 'c'}

        >>> s.remove('a')
        >>> s
        {'c', 'b'}

        >>> s.remove('abc')
        Traceback (most recent call last):
        File "<stdin>", line 1, in <module>
        KeyError: 'abc'


.. _`set.symmetric_difference()`:

set.symmetric_difference(other)
************************************

返回一个新集合，只保留两个集合中不共同存在的元素。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'b', 'e', 'f'}

    >>> s.symmetric_difference(a)
    {'f', 'c', 'a', 'e'}

    >>> s ^ a
    {'f', 'c', 'a', 'e'}


.. _`set.symmetric_difference_update()`:

set.symmetric_difference_update(other)
*******************************************************************************

更新集合，只保留不共同存在的元素。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'b', 'e', 'f'}

    >>> s.symmetric_difference_update(a)
    >>> s
    {'f', 'c', 'a', 'e'}


.. _`union()`:

set.union(*others)
************************************

返回一个新集合，其中包含来自原集合以及 others 指定的所有集合中的元素，即并集。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'b', 'e', 'f'}

    >>> s.union(a)
    {'a', 'b', 'e', 'f', 'c'}

    >>> s | a
    {'a', 'b', 'e', 'f', 'c'}


.. _`set.update()`:

set.update(*others)
************************************

更新集合，添加来自 others 中的所有元素，即用并集更新集合。

::

    >>> s = {'a', 'b', 'c'}
    >>> a = {'b', 'e', 'f'}

    >>> s.update(a)
    >>> s
    {'a', 'b', 'e', 'f', 'c'}
