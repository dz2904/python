编辑器
####################################

虽说任何能够编辑普通文本的编辑器都能够用来编写Python代码，然后，使用一个更加强大的编辑器可以使您的生活变得舒畅。


Atom
************************************

`Atom <https://atom.io/>`_ 是一款21世纪的可删减的文本编辑器。它基于所喜欢的编辑器的任何优秀特性，并构建于 atom-shell 上。

Atom是web原生的（HTML、CSS、JS），专注于模块化的设计和简单的插件开发。它自带本地包管理和大量的包。Python开发所推荐的插件是 `Linter <https://github.com/steelbrain/linter>`_ 和 `linter-flake8 <https://github.com/AtomLinter/linter-flake8>`_ 的组合。

Atom 是一款跨平台的开源文本编辑器（Mac、Windows、Linux），更多信息可以查看其 `GhtHub <https://github.com/atom/atom>`_ 页面。


TextMate
************************************

`TextMate <http://macromates.com/>`_ 是 Mac OS 系统下的著名的文本编辑器。尤其适合程序员使用，可以定制许多贴心使用的功能。

TextMate 2 是开源软件，采用 GPLv3 许可证，更多信息可以查看其 `GhtHub <https://github.com/textmate/textmate>`_ 页面。


Sublime Text
************************************

`Sublime Text <http://www.sublimetext.com/>`_ 是一款高级的，用来编写代码、标记和文章的文本编辑器。您将会爱上漂亮的用户界面、非凡的特性和惊人的表现。

Sublime Text 是一款跨平台的文本编辑器（Mac、Windows、Linux）。收费软件，但可以无限期试用，会有激活提示弹窗。


Vim
************************************

Vim是一个使用键盘快捷键而不是菜单或图标来编辑的文本编辑器。有许多增强Vim编辑器中
Python开发环境的插件和设置。如果您只开发Python，使用缩进和换行均符合 :pep:`8` 
要求的默认设置是一个好的开始。在您的home目录中，打开 :file:`.vimrc` 文件，
添加下面这些内容::

    set textwidth=79  " lines longer than 79 columns will be broken
    set shiftwidth=4  " operation >> indents 4 columns; << unindents 4 columns
    set tabstop=4     " a hard TAB displays as 4 columns
    set expandtab     " insert spaces when hitting TABs
    set softtabstop=4 " insert/delete 4 spaces when hitting a TAB/BACKSPACE
    set shiftround    " round indent to multiple of 'shiftwidth'
    set autoindent    " align the new line indent with the previous line

基于上述设置，新行会在超过79个字符被添加，tab键则会自动转换为4个空格。如果您还使用
Vim编辑其他语言，有一个叫做 indent_ 的便捷插件可以让这个设置只为Python源文件服务。

还有一个方便的语法插件叫做 syntax_ ，改进了Vim 6.1中的语法文件。

这些插件使您拥有一个基本的环境进行Python开发。要最有效的使用Vim，您应该时常检查代码的
语法错误和是否符合PEP8。幸运的是， pycodestyle_ 和 Pyflakes_ 将会帮您做这些。
如果您的Vim是用 ``+python`` 编译的，您也可以在编辑器中使用一些非常有用的插件来做这些检查。

对于PEP8检查和pyflakes，您可以安装 vim-flake8_ 。然后您就可以在Vim中把 ``Flake8`` 
映射到任何热键或您想要的行为上。这个插件将会在屏幕下方显示出错误，并且提供一个简单的
方式跳转到相关行。在保存文件的时候调用这个功能会是非常方便的。要这么做，
就把下面一行加入到您的 :file:`.vimrc`::

    autocmd BufWritePost *.py call Flake8()

如果您已经在使用 syntastic_ ，您可以设置它来运行Pyflakes，并在quickfix窗口中显示错误
和警告。一个这样做并还会在状态栏中显示状态和警告信息的样例是::

    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*
    let g:syntastic_auto_loc_list=1
    let g:syntastic_loc_list_height=5


Python-mode
^^^^^^^^^^^

Python-mode_ 是一个在Vim中使用Python的综合解决方案。
它拥有：

- 任意组合的异步Python代码检查（ ``pylint`` 、 ``pyflakes`` 、 ``pycodestyle`` 、 ``mccabe``）
- 使用Rope进行代码重构和补全
- Python快速折叠
- 支持virtualenv
- 搜索Python文档，运行Python代码
- 自动修复 pycodestyle_ 错误

以及其他更多。

.. _indent: http://www.vim.org/scripts/script.php?script_id=974
.. _syntax: http://www.vim.org/scripts/script.php?script_id=790
.. _Pyflakes: http://pypi.python.org/pypi/pyflakes/
.. _pycodestyle: https://pypi.org/project/pycodestyle/
.. _syntastic: https://github.com/vim-syntastic/syntastic
.. _Python-mode: https://github.com/python-mode/python-mode
.. _SuperTab: http://www.vim.org/scripts/script.php?script_id=1643
.. _vim-flake8: https://github.com/nvie/vim-flake8

Emacs
************************************

Emacs是另一个强大的文本编辑器。它是完全可编程的（Lisp），但要正确的工作要花些功夫。
如果您已经是一名Emacs的用户了，在EmacsWiki上的 `Python Programming in Emacs`_ 
将会是好的开始。

1. Emacs 本身支持Python模式。

.. _Python Programming in Emacs: https://www.emacswiki.org/emacs/PythonProgrammingInEmacs




IDEs
************************************

集成开发环境（IDE，Integrated Development Environment ）是用于提供程序开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具。集成了代码编写功能、分析功能、编译功能、调试功能等一体化的开发软件服务套。


Geany
====================================

`Geany <https://www.geany.org/>`_ 是一款使用 GTK+2 开发的强大，稳定和轻量级的集成开发环境，被翻译成超过 40 种语言，并内置了超过 50 种编程语言的支持。

Geany 是以 GPL 许可证分发的开源，跨平台（Mac、Windows、Linux）的文本编辑器。


PyCharm
====================================

`PyCharm <http://www.jetbrains.com/pycharm/>`_ 由 JetBrains 公司开发，此公司还以 IntelliJ IDEA 而闻名。它们都共享着相同的基础代码，PyCharm中大多数特性能通过免费的 `Python 插件 <https://plugins.jetbrains.com/plugin/?idea&pluginId=631>`_ 带入到 IntelliJ 中。

PyCharm 由两个版本：专业版（30天试用）和拥有相对少特性的社区版（Apache 2.0 License）；跨平台（Mac、Windows、Linux）的软件。


Enthought Canopy
====================================

`Enthought Canopy <https://www.enthought.com/product/canopy/>`_ 是一款专门面向科学家和工程师的 Python IDE，它预装了为数据分析而用的计算库。

Enthought Canopy 由两个版本：付费版和免费版；跨平台（Mac、Windows、Linux）的软件。


Spyder
====================================

`Spyder <https://github.com/spyder-ide/spyder>`_ 是一款用Python编写，专门面向和 Python 科学库（即 `SciPy <https://www.scipy.org/>`_ ）打交道的 IDE。它集成了 pyflakes_ 、 `pylint <https://www.logilab.org/857>`_ 和 `rope <https://github.com/python-rope/rope>`_ 。

Spyder 是以 MIT 许可证分发的开源，跨平台（Mac、Windows、Linux）的文本编辑器。


NINJA-IDE
====================================

`NINJA-IDE <http://www.ninja-ide.org/>`_ （来自递归缩写："Ninja-IDE Is Not Just Another IDE"）是一款跨平台的 IDE，使用 Python 和 Qt 开发。

NINJA-IDE 是以 GPLv3 许可证分发的开源，跨平台（Mac、Windows、Linux）的文本编辑器。更多信息可以查看其 `GhtHub <https://github.com/ninja-ide>`_ 页面。

