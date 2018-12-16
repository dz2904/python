for 语句
########################

while 语句非常灵活，可用于在条件为真时反复执行代码块。这在通常情况下很好，但有时候你可能想根据需要进行定制。一种这样的需求是为序列（或其他可迭代对象）中每个元素执行代码块。

.. note::

    基本上，可迭代对象是可使用 for 循环进行遍历的对象。通常情况下，只需将可迭代对象视为序列即可。

为此，可使用for 语句：

.. highlight:: none

::

    words = ['this', 'is', 'an', 'ex', 'parrot']
    for word in words:
       print(word)

鉴于迭代（也就是遍历）特定范围内的数是一种常见的任务，Python 提供了一个创建范围的内置函数。

::

    >>> range(0, 10)
    range(0, 10)
    >>> list(range(0, 10))
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

范围类似于切片。它们包含起始位置（这里为0），但不包含结束位置（这里为10）。在很多情况下，你都希望范围的起始位置为0。实际上，如果只提供了一个位置，将把这个位置视为结束位置，并假定起始位置为0。range()函数也可以有第三个参数，那就是是“步长”（类似于切片的步长）。

相比使用 while 循环，这些代码要紧凑得多。只要能够使用 for 循环，就不要使用 while 循环。

迭代字典
************************

要遍历字典的所有关键字，可像遍历序列那样使用普通的 for 语句。

::

    d = {'x': 1, 'y': 2, 'z': 3}
    for key in d:
       print(key, 'corresponds to', d[key])

也可使用 keys 等字典方法来获取所有的键。如果只对值感兴趣，可使用 d.values 。你可能还记得，d.items 以元组的方式返回键-值对。for 循环的优点之一是，可在其中使用序列解包。

::

    for key, value in d.items():
       print(key, 'corresponds to', value)

一些迭代工具
************************

Python 提供了多个可帮助迭代序列（或其他可迭代对象）的函数，其中一些位于模块 itertools 中，但还有一些内置函数使用起来也很方便。

并行迭代
========================

有时候，你可能想同时迭代两个序列。假设有两个列表。如果要打印名字和对应的年龄，可以像下面这样做：

   names = ['anne', 'beth', 'george', 'damon']
   ages = [12, 45, 32, 102]

   for i in range(len(names)):
       print(names[i], 'is', ages[i], 'years old')

i 是用作循环索引的变量的标准名称。一个很有用的并行迭代工具是内置函数 zip，它将两个序列“缝合”起来，并返回一个由元组组成的序列。返回值是一个适合迭代的对象，要查看其内容，可使用 list 将其转换为列表。

::

   >>> list(zip(names, ages))
   [('anne', 12), ('beth', 45), ('george', 32), ('damon', 102)]


“缝合”后，可在循环中将元组解包。函数 zip 可用于“缝合”任意数量的序列。需要指出的是，当序列的长度不同时，函数 zip 将在最短的序列用完后停止“缝合”。

::

   for name, age in zip(names, ages):
       print(name, 'is', age, 'years old')


迭代时获取索引
========================

在有些情况下，你需要在迭代对象序列的同时获取当前对象的索引。例如，你可能想替换一个字符串列表中所有包含子串 'xxx' 的字符串。当然，完成这种任务的方法有很多，但这里假设你要像下面这样做：

::

   for string in strings:
       if 'xxx' in string:
           index = strings.index(string) # 在字符串列表中查找字符串
           strings[index] = '[censored]'

这可行，但替换前的搜索好像没有必要。另外，如果没有替换，搜索返回的索引可能不对（即返回的是该字符串首次出现处的索引）。下面是一种更佳的解决方案：

::

   index = 0
   for string in strings:
       if 'xxx' in string:
           strings[index] = '[censored]'
       index += 1

这个解决方案虽然可以接受，但看起来也有点笨拙。另一种解决方案是使用内置函数 enumerate，这个函数让你能够迭代索引-值对，其中的索引是自动提供的。

::

   for index, string in enumerate(strings):
       if 'xxx' in string:
           strings[index] = '[censored]'

反向迭代和排序后再迭代
========================

来看另外两个很有用的函数：reversed 和 sorted。它们类似于列表方法 reverse 和 sort（sorted 接受的参数也与 sort 类似），但可用于任何序列或可迭代的对象，且不就地修改对象，而是返回反转和排序后的版本。

::

   >>> sorted([4, 3, 6, 8, 3])
   [3, 3, 4, 6, 8]
   >>> sorted('Hello, world!')
   [' ', '!', ',', 'H', 'd', 'e', 'l', 'l', 'l', 'o', 'o', 'r', 'w']
   >>> list(reversed('Hello, world!'))
   ['!', 'd', 'l', 'r', 'o', 'w', ' ', ',', 'o', 'l', 'l', 'e', 'H']
   >>> ''.join(reversed('Hello, world!'))
   '!dlrow ,olleH'

请注意，sorted 返回一个列表，而 reversed 像 zip 那样返回一个更神秘的可迭代对象。你无需关心这到底意味着什么，只管在 for 循环或 join 等方法中使用它，不会有任何问题。只是你不能对它执行索引或切片操作，也不能直接对它调用列表的方法。要执行这些操作，可先使用 list 对返回的对象进行转换。
