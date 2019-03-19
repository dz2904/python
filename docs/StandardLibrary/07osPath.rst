os.path — 路径操作
##########################

源码：Lib/posixpath.py (for POSIX), Lib/ntpath.py (for Windows NT), and Lib/macpath.py (for Macintosh)

这个模块实现了一些有关操作路径的函数。如果需要读取或写入文件请参见 open()，如果要访问文件系统请参见 os 模块。路径参数可以作为字符串或字节传递。鼓励应用程序将文件名称表示为（Unicode）字符串。不幸的是，一些文件的名称可能不可以在 Unix 上表示为字符串，所以需要在 Unix 上支持任意文件的名称的应用程序应使用字节对象来表示路径名称。反之亦然，使用字节对象不能表示所有在 Windows 上文件的名称 （在标准 mbcs 编码），因此 Windows 应用程序应使用字符串对象来访问所有文件。

.. note::

    所有的这些功能接受仅以字节或只有字符串对象作为其参数。如果返回路径或文件的名称，则结果为相同类型的对象。

**os.path.abspath(path)**  返回一个标准的绝对路径名。

.. highlight:: none

::

    >>> pwd

**os.path.basename(path)**  返回路径名 path 的最后一级的名称。注意，这个函数的结果与 Unix 的 basename 命令不同；对于 '/foo/bar/'，Unix 的 basename 返回 'bar'，而 basename() 函数返回空字符串（''）。

**os.path.commonpath(paths)**  返回 paths 参数中，所有路径序列中共有的最长的路径。如果 paths 即包含绝对路径又包含相对路径，或者 paths 为空将抛出 ValueError。

**os.path.commonprefix(list)**  返回列表中所有路径的前缀的最长路径前缀（逐个字符）。如果列表为空，则返回空字符串（''）。

.. note::

    此函数可能返回无效路径，因为它一次处理一个字符。要获取有效路径，请参阅 commonpath()。

**os.path.dirname(path)**  返回 path 中的目录名。实际上是通过将 path 参数传递个 split() 函数得到的返回值的第一个元素。

**os.path.exists(path)**  如果路径指向现有路径或打开的文件描述器，则返回 True。如果是损坏的符号链接，则返回 False。在某些平台上，如果未授予在所请求的文件上执行 os.stat() 的权限，此函数可能会返回 False，即使路径物理上确实是存在的。

版本 3.3 中的更改︰现在，path 可以是一个整数︰ 返回 True 如果它是一个打开的文件描述符，否则为False。

**os.path.lexists(path)**  如果 path 指向现有的路径，则返回 True。破碎的符号链接将返回 True。在缺少 os.lstat() 的平台上等效于 exists()。

**os.path.expanduser(path)**  在 Unix 和 Windows 上，将参数中原始的 ~ 或 ~user 部分用 user 主目录替换。如果扩展失败或者参数 path 不是以 ~ 打头，则返回 path 不变。

**os.path.expandvars(path)**  返回参数，其中的环境变量被扩展。形式 $name 或 ${name} 的子字符串由环境变量 name 的值替换。如果格式不正确或者引用了不存在的变量，则不进行替换（或者扩展）。

**os.path.getatime(path)**  返回 path 的上次访问时间。返回值是一个数字，表示自纪元以来的秒数（参见time模块）。如果文件不存在或无法访问，则引发 OSError。

**os.path.getmtime(path)**  返回 path 的最后修改时间。返回值是一个数字，表示自纪元以来的秒数（参见 time 模块）。如果文件不存在或无法访问，则引发 OSError。

**os.path.getctime(path)**  返回系统的 ctime，在某些系统（如 Unix）上是最后元数据更改的时间，在其他系统（如 Windows）上，是路径的创建时间。返回值是一个数字，表示自纪元以来的秒数（参见时间模块）。如果文件不存在或无法访问，则引发 OSError。

**os.path.getsize(path)**  返回 path 的大小，以字节为单位。如果文件不存在或无法访问，则引发 OSError。

**os.path.isabs(path)**  如果路径是绝对路径名，则返回 True。

**os.path.isfile(path)**  如果路径是现有的常规文件，则返回 True。这遵循符号链接(软链接)，因此 islink() 和 isfile() 对于同一路径可以为 True。

**os.path.isdir(path)**  如果文件是目录，则返回 True。这遵循符号链接，因此 islink() 和 isdir() 对于同一路径可以为 True。

**os.path.islink(path)**  如果路径指的是符号链接的目录条目，则返回 True。始终 False 如果 Python 运行时不支持符号链接。

**os.path.ismount(path)**  如果路径名路径是安装点，则返回 True。在 POSIX 上，函数检查路径的父节点，path/.. 是否与路径不在同一个设备上，或者 path/.. 和 path 指向同一设备上的同一个 i-node - 这应该检测所有Unix和POSIX变体的挂载点。在Windows上，驱动器号根和共享UNC始终是安装点，并且调用任何其他路径GetVolumePathName以查看它是否与输入路径不同。

**os.path.join(path, *paths)**  将一个或多个路径正确地连接起来。返回值是路径和*路径的任何成员与每个非空的后面紧跟一个目录分隔符（os.sep）的连接部分，除了最后一个，意味着结果将只在分隔符结束，如果最后一部分为空。如果组件是绝对路径，则所有先前组件都将被丢弃，并且从绝对路径组件继续加入。

在Windows上，遇到绝对路径组件（例如，r'\foo'）时，不会重置驱动器盘符。如果组件包含驱动器号，则所有以前的组件都将被丢弃，并且驱动器号被重置。请注意，由于每个驱动器都有一个当前目录，因此os.path.join（“c：”， “foo”） 驱动器C:（c:foo）上的当前目录的路径，而不是c:\foo。

**os.path.normcase(path)**  标准化路径名的大小写。在 Unix 和 Mac OS X 上，这会返回路径不变；在不区分大小写的文件系统上，它将路径转换为小写。在Windows上，还会将斜线转换成反斜线。如果路径的类型不是 str 或 bytes，则引发 TypeError。

**os.path.normpath(path)**  通过折叠冗余分隔符和上级引用来归一化路径名，以使 A//B，A/B/，A/./B 和 A/foo/../B 都变为 A/B。该字符串操作可能改变包含符号链接的路径的含义。在 Windows 上，还会将斜线转换成反斜线。要规范化情况，请使用 normcase()。

**os.path.realpath(path)**  返回指定的文件名的规范名字，并消除路径中遇到的任何符号链接（如果操作系统支持的话）。

**os.path.relpath(path, start=os.curdir)**  返回自当前目录或者可选的 start 目录的 path 相对文件路径。这是一个路径计算：不访问文件系统以确认路径或开始的存在或本质。

**os.path.samefile(path1, path2)**  如果两个路径名参数都指向相同的文件或目录，则返回 True。这由设备号和 i 节点号决定，如果对任一路径名的 os.stat() 调用失败，则引发异常。

**os.path.sameopenfile(fp1, fp2)**  如果文件描述器 fp1 和 fp2 指向同一文件，则返回 True。

**os.path.samestat(stat1, stat2)**  如果统计数据元组 stat1 和 stat2 指向同一文件，则返回 True。这些结构可能已由 os.fstat()，os.lstat() 或 os.stat() 返回。此函数实现 samefile() 和 sameopenfile() 使用的基础比较。

**os.path.split(path)**  将路径名 path 拆分为一个元组对(head, tail)，其中 tail 是路径名的最后一个部分，head 是前面的所有内容。tail 部分不会包含斜杠；如果 path 以斜线结尾，则 tail 将为空。如果 path 中没有斜线，head 将为空。如果 path 为空，head 和 tail 两个都将为空。尾部的斜线会从 head 中去除掉，除非它是根目录（只包含一个或多个斜线的目录）。在所有情况下，join(head, tail) 返回与 path 相同位置的路径（但是字符串可能不同）。

**os.path.splitdrive(path)**  将路径名路径拆分为（drive， tail）其中 drive 为挂载点或空字符串。在没有使用驱动器描述符的系统上，drive 将永远是空字符串。在所有情况下，驱动 + 尾将与路径相同。

**os.path.splitext(path)**

   Split the pathname path into a pair (root, ext) such that root + ext == path, and ext is empty or begins with a period and contains at most one period. 忽略basename前面的点号；splitext('.cshrc')返回('.cshrc', '')。
