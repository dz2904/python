os.path — 路径操作
##########################

os.path 模块常用于解析、构建、测试以及处理文件名和路径，用于开发跨平台的程序。

路径参数可以是字符串也可以是字节，应该首选将文件名称表示为（Unicode）字符串。不幸的是，一些文件的名称可能不可以在 Unix 上表示为字符串，所以需要在 Unix 上支持任意文件名的程序应使用字节对象来表示路径名。反之亦然，使用字节对象不能表示所有 Windows 上的文件名 （在标准 mbcs 编码），因此在 Windows 程序中应使用字符串对象来访问所有文件。


.. note::

    所有的参数仅接受只有字节或只有字符串对象，不可以传入两种对象参数。在返回路径或文件名时，结果与传入参数的类型相同。

有时候，路径解析会依赖于定义在  os 中的一些变量:

- os.sep -- 路径各部分之间的分隔符 （例如， 在 win 平台下的 ``\\`` 和在 Linux 平台下的 ``/`` ）
- os.extsep -- 文件名和 「扩展名」之间的分隔符 （例如， ``.`` ）
- os.pardir -- 表示上级目录的路径组件（例如， ``..`` ）
- os.curdir -- 表示当前目录的路径组件（例如， ``.`` ）


解析路径
************************************

os.path 中有一组函数用于将表示文件名称的字符串解析成它的组成部分，这些函数不依赖于实际存在的路径，它们只能用来操作字符串。

**os.path.split(path)**  分离路径和文件名。将路径名 path 拆分为一个元组对 (head, tail)，其中 tail 是路径名的最后一个部分，head 是前面的所有内容。tail 部分不会包含斜杠；如果 path 以斜线结尾，则 tail 将为空。如果 path 中没有斜线，head 将为空。如果 path 为空，head 和 tail 两个都将为空。尾部的斜线会从 head 中去除掉，除非它是根目录（只包含一个或多个斜线的目录）。

::

    >>> os.path.split('/usr/lib/python3.6')
    ('/usr/lib', 'python3.6')
    >>> os.path.split('/usr/lib/python3.6/')
    ('/usr/lib/python3.6', '')
    >>> os.path.split('/usr/lib/python3.6/pp.py')
    ('/usr/lib/python3.6', 'pp.py')


**os.path.basename(path)**  返回路径名 path 的最后一级的名称（等同于 split() 函数 tail 部分的值）。

::

    >>> os.path.basename('/usr/lib')
    'lib'

    >>> os.path.basename('/usr/lib/')
    ''
    >>> os.path.basename('/usr/lib/python3/pp.py')
    'pp.py'


**os.path.dirname(path)**  返回 path 中的目录名（等同于 split() 函数 head 部分的值）。

::

    >>> os.path.dirname('/usr/lib/python3/pp.py')
    '/usr/lib/python3'
    >>> os.path.dirname('/usr/lib/')
    '/usr/lib'
    >>> os.path.dirname('/usr/lib')
    '/usr'


**os.path.splitext(path)**  分离文件名和后缀名。为避免出现不可预测的结果，最好不要带有路径。

::

    >>> os.path.splitext('/usr/lib/python3/pp.py')
    ('/usr/lib/python3/pp', '.py')
    >>> os.path.splitext('pp.py')
    ('pp', '.py')
    >>> os.path.splitext('abc.tar.gz')
    ('abc.tar', '.gz')
    >>> os.path.splitext('/usr/lib/python3.6/')
    ('/usr/lib/python3.6/', '')
    >>> os.path.splitext('/usr/lib/python3.6')
    ('/usr/lib/python3', '.6')


构建路径
************************************

**os.path.join(path, *paths)**  将一个或多个路径连接起来。如果某个参数是以 os.sep 开头，那么它之前的所有参数都将被丢弃，并且返回值将以它作为新的开始。。

::

    >>> os.path.join('usr', 'lib', 'python3')
    'usr/lib/python3'
    >>> os.path.join('/usr/', 'lib/python3/')
    '/usr/lib/python3/'
    >>> os.path.join('/usr', 'lib/python3/')
    '/usr/lib/python3/'
    >>> os.path.join('/usr/', '/lib/python3/')
    '/lib/python3/'


**os.path.expanduser(path)**  在 Unix 和 Windows 上，将参数中原始的 ~ 或 ~user 部分用 user 主目录替换。如果扩展失败或者参数不以 ~ 开头，则返回 path 不变。

::

    >>> os.path.expanduser('~/Document')
    '/home/gavin/Document'
    >>> os.path.expanduser('/usr/lib')
    '/usr/lib'


规范路径
************************************

**os.path.normpath(path)**  通过折叠冗余分隔符和上级引用来规范化路径名。

::

    >>> os.path.normpath('/usr//lib//')
    '/usr/lib'
    >>> os.path.normpath('////usr/lib/')
    '/usr/lib'


**os.path.abspath(path)**  返回一个标准的绝对路径名。

.. highlight:: none

::

    >>> os.path.abspath('./')
    '/usr/lib'

    >>> os.path.abspath('./python3')
    '/usr/lib/python3'


文件时间
************************************

除了处理文件路径，os.path 还包含了一些用于检索文件属性的函数。

**os.path.getatime(path)**  返回 path 的最后访问时间。返回值是一个数字，表示自纪元以来的秒数（参见time模块）。如果文件不存在或无法访问，则引发 OSError。

::

    >>> os.path.getatime('/usr/lib')
    1552996323.36275
    >>> os.path.getatime('/mnt')
    1552224407.037561


**os.path.getmtime(path)**  返回 path 的最后修改时间。返回值是一个数字，表示自纪元以来的秒数（参见 time 模块）。如果文件不存在或无法访问，则引发 OSError。

::

    >>> os.path.getmtime('/usr/lib')
    1552309861.3857274
    >>> os.path.getmtime('/mnt')
    1532487836.0


**os.path.getctime(path)**  返回 path 的创建时间。返回值是一个数字，表示自纪元以来的秒数（参见时间模块）。如果文件不存在或无法访问，则引发 OSError。

::

    >>> os.path.getctime('/mnt')
    1546701154.282817
    >>> os.path.getctime('/usr/lib')
    1552309861.3857274


**os.path.getsize(path)**  返回 path 的大小，以字节为单位。如果文件不存在或无法访问，则引发 OSError。

::

    >>> os.path.getsize('/usr/lib')
    4096
    >>> os.path.getsize('/usr/lib/python3.6')
    20480


检测文件
************************************

当一个程序中遇到一个路径名称时，经常需要知道这个路径是指一个文件，目录，系统链接或者它是否存在。

**os.path.isabs(path)**  如果路径是绝对路径名，则返回 True。

::

    >>> os.path.isabs('./')
    False
    >>> os.path.isabs('/usr/lib/')
    True


**os.path.isfile(path)**  如果路径是现有的常规文件，则返回 True。这遵循符号链接(软链接)，因此 islink() 和 isfile() 对于同一路径可以为 True。

::

    >>> os.path.isfile('./')
    False
    >>> os.path.isfile('/usr/lib/')
    False
    >>> os.path.isfile('/home/gavin/Downloads/01.jpg')
    True


**os.path.isdir(path)**  如果文件是目录，则返回 True。这遵循符号链接，因此 islink() 和 isdir() 对于同一路径可以为 True。

::

    >>> os.path.isdir('./')
    True
    >>> os.path.isdir('/usr/lib/')
    True
    >>> os.path.isdir('/home/gavin/Downloads/01.jpg')
    False


**os.path.islink(path)**  如果路径指的是符号链接的目录条目，则返回 True。始终 False 如果 Python 运行时不支持符号链接。

::

    gavin@lib$ ls -l
    lrwxrwxrwx  1 root root      15 Jan 16  2018 libchm.so.1 -> libchm.so.1.0.0
    -rw-r--r--  1 root root   26464 Jan 16  2018 libchm.so.1.0.0

    >>> os.path.islink('/usr/lib/libchm.so.1')
    True
    >>> os.path.islink('/usr/lib/libchm.so.1.0.0')
    False


其它
************************************

**os.path.realpath(path)**  返回指定的文件名的规范名字，并消除路径中遇到的任何符号链接（如果操作系统支持的话）。

::

    >>> os.path.realpath('/usr/lib/')
    '/usr/lib'
    >>> os.path.realpath('/home/gavin/Downloads/01.jpg')
    '/home/gavin/Downloads/01.jpg'
    >>> os.path.realpath('/usr/lib/libchm.so.1')
    '/usr/lib/libchm.so.1.0.0'

**os.path.relpath(path, start=os.curdir)**  返回自当前目录或者可选的 start 目录到 path 的相对文件路径。

::

    >>> os.path.relpath('/home/gavin/Document')
    '../../home/gavin/Document'
    >>> os.path.relpath('/home/gavin/Document', '/mnt')
    '../home/gavin/Document'

**os.path.samefile(path1, path2)**  如果两个路径名参数都指向相同的文件或目录，则返回 True。这由设备号和 i 节点号决定，如果对任一路径名的 os.stat() 调用失败，则引发异常。

::

    >>> os.path.samefile('/usr/lib/python3',  'python3')
    True
    >>> os.path.samefile('/usr/lib/python3',  'python3.6')
    False

**os.path.sameopenfile(fp1, fp2)**  如果文件描述器 fp1 和 fp2 指向同一文件，则返回 True。

**os.path.samestat(stat1, stat2)**  如果统计数据元组 stat1 和 stat2 指向同一文件，则返回 True。


**os.path.splitdrive(path)**  将路径名路径拆分为（drive， tail）其中 drive 为挂载点或空字符串。在没有使用驱动器描述符的系统上，drive 将永远是空字符串。

::

    >>> os.path.splitdrive('/usr/lib/python3.6/')
    ('', '/usr/lib/python3.6/')
    >>> os.path.splitdrive('/usr/lib/python3.6')
    ('', '/usr/lib/python3.6')



