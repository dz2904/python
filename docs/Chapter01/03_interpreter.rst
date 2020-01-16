Python 解释器
####################################

当人们谈论起 Python 时，不仅是在说语言本身，还包括其 CPython 实现。
Python 实际上是一个可以用许多不同的方式来实现的语言规范。


CPython
************************************

`CPython <http://www.python.org>`_ 是 Python 的参考实现，用 C 语言编写。它把 Python 代码编译成中间态的字节码，然后由虚拟机解释。CPython 为 Python 包和 C 扩展模块提供了最大限度的兼容。

如果您正在写开源的 Python 代码，并希望有尽可能广泛的应用，用 CPython 是最好的选择。当使用依赖于 C 扩展的包时，CPython 是唯一的选择。

所有版本的 Python 语言都用 C 语言实现，因为 CPython 是参考实现。


PyPy
************************************

`PyPy <http://pypy.org/>`_ 是用 RPython 实现的解释器。RPython 是 Python 的子集，具有静态类型。这个解释器的特点是即时编译，支持多重后端（C, CLI, JVM）。

PyPy 旨在提高性能，同时保持最大兼容性（请参考 CPython 的实现）。

如果您正在寻找提高您的 Python 代码性能的方法，值得试一试 PyPy。在一套的基准测试下，它目前比 CPython 的速度快超过 5 倍 。


Jython
************************************

`Jython <http://www.jython.org/>`_ 是一个将 Python 代码编译成 Java 字节码的实现，运行在 JVM (Java Virtual Machine) 上。另外，它可以像是用 Python 模块一样，导入并使用任何 Java 类。

如果您需要与现有的 Java 代码库对接或者基于其他原因需要为 JVM 编写 Python 代码，那么 Jython 是最好的选择。


IronPython
************************************

`IronPython <http://ironpython.net/>`_ 是一个针对 .NET 框架的 Python 实现。它可以用 Python 和 .NET framework 的库，也能将 Python 代码暴露给给 .NET 框架中的其他语言。

`Python Tools for Visual Studio <http://ironpython.net/tools/>`_ 直接集成了 IronPython 到 Visual Studio 开发环境中，使之成为 Windows 开发者的理想选择。


PythonNet
************************************

`Python for .NET <http://pythonnet.github.io/>`_ 是一个近乎无缝集成的，提供给本机已安装的 Python .NET 公共语言运行时（CLR）包。它采取与 IronPython 相反的方法，与其说是竞争，不如说是互补。

PythonNet 与 Mono 相结合使用，通过 .NET 框架，能使 Python 在非 windows 系统上（如OS X和Linux）完成操作。它可以在除外 IronPython 的环境中无冲突运行。

