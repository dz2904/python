for 语句
####################################

for 语句用于遍历任意的可迭代对象（如列表、字典、range 对象等）。

.. highlight:: none

::

    >>> for i in 'abcde':
    ...     print(i)
    ... 
    a
    b
    c
    d
    e

相比使用 while 循环，for 循环要紧凑得多。通常建议：只要能够使用 for 循环，就不要使用 while 循环。


结合序列解包
************************************

for 循环还有一个优点，那就是可以和序列解包结合使用。


要遍历字典的所有关键字，可像遍历序列那样使用普通的 for 语句。

::

    >>> d = {'a': 1, 'b': 2, 'c': 3}
    >>> for k, v in d.items():
    ...     print('key is:', k)
    ...     print('value is:', v)
    ...     print('------------')
    ... 
    key is: a
    value is: 1
    ------------
    key is: b
    value is: 2
    ------------
    key is: c
    value is: 3
    ------------


    # 循环 zip 函数
    >>> names = ['Alice', 'Bella', 'Dana', 'Elva', 'Linda']
    >>> ages = [25, 27, 25, 20, 32]

    >>> for name, age in zip(names, ages):
    ...     print('{} is {} years old.'.format(name, age))
    ... 
    Alice is 25 years old.
    Bella is 27 years old.
    Dana is 25 years old.
    Elva is 20 years old.
    Linda is 32 years old.
