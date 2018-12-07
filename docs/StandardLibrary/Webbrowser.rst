webbrowser 浏览器操作库
################################

webbrowser 模块提供了一个可以向用户展示 Web 文档的高级接口。在绝大多数情况下，使用本模块的 open() 函数即可。

脚本 webbrowser 可以用作命令行接口。它接受 URL 作为参数。它也接受如下可选参数：-n 如果可以，在新浏览器窗口打开 URL； -t 在浏览器新标签页（TAB）打开URL。当然，这两个选项是互斥的，不可共存。用法示例︰


.. highlight:: none

::

    python -m webbrowser -t "http://www.python.org"

异常定义：

::

        exception webbrowser.Error  浏览器控制引发的异常。

可用函数：
************************

webbrowser.open(url, new=0, autoraise=True)
===============================================

调用默认浏览器打开 url 。如果 new 参数为 0，将尽可能在同一个浏览器窗口打开 url。如果 new 参数为1，将使用新的浏览器窗口打开指定 url。如果 new 参数为 2，则使用新浏览器标签页（TAB）打开。如果 autoraise 是 True，则窗口会被调用（请注意，在许多窗口管理器下，不管此变量的设置如何）。

请注意，在某些平台上，尝试使用此函数打开文件名，可能会工作并启动操作系统的关联程序。

webbrowser.open_new(url)
=====================================

如果可能，在默认浏览器的新窗口中打开 url，否则，在唯一的浏览器窗口中打开 url。

webbrowser.open_new_tab(url)
======================================

如果可能，在默认浏览器的新页面（“标签”）中打开 url，否则等效于 open_new()

webbrowser.get(using=None)
========================================

使用返回浏览器类型的控制器对象。如果使用为 None，则返回适用于调用方环境的默认浏览器的控制器。

webbrowser 预定义了多种浏览器类型。该表给出可以传递到 get() 函数的类型名称以及控制器类的对应实例化，这些都在本模块中定义。

=====================   =================================
类型名称                   类名称
=====================   =================================
'mozilla'	                Mozilla('mozilla')
'firefox'                 Mozilla('mozilla')
'netscape'                Mozilla('netscape')
'galeon'                  Galeon('galeon')
'epiphany'                Galeon('epiphany')
'skipstone'               BackgroundBrowser('skipstone')
'kfmclient'               Konqueror()
'konqueror'               Konqueror()
'kfm'                     Konqueror()
'mosaic'                  BackgroundBrowser('mosaic')
'opera'                   Opera()
'grail'                   Grail()
'links'                   GenericBrowser('links')
'elinks'                  Elinks('elinks')
'lynx'                    GenericBrowser('lynx')
'w3m'                     GenericBrowser('w3m')
'windows-default'         WindowsDefault
'macosx'                  MacOSX('default')
'safari'                  MacOSX('safari')
'google-chrome'           Chrome('google-chrome')
'chrome'                  Chrome('chrome')
'chromium'                Chromium('chromium')
'chromium-browser'	      Chromium('chromium-browser')


webbrowser.register(name, constructor, instance=None)
=========================================================

注册浏览器类型名称。一旦注册了浏览器类型，get() 函数可以返回该浏览器类型的控制器。如果未提供实例或者 None，则会调用构造函数，而无需创建实例。如果提供实例，则构造函数将永远不被调用，并且可以是 None。

此入口点仅在计划设置 BROWSER 变量或调用 get() 时使用非空参数匹配处理程序。



这里有一些简单的例子：

::

    url = 'http://docs.python.org/'

    # Open URL in a new tab, if a browser window is already open.
    webbrowser.open_new_tab(url)

    # Open URL in new window, raising the window if possible.
    webbrowser.open_new(url)

浏览器控制器对象
***************************

浏览器控制器提供了这些方法，它们并行了三个模块级的便利功能：

::

    controller.open(url, new=0, autoraise=True)

使用此控制器处理的浏览器显示 url。如果 new 为 1，则尽可能打开新的浏览器窗口。如果 new 为 2，则尽可能打开新的浏览器页面（“选项卡”）。

::

    controller.open_new(url)

如果可能，在此控制器处理的浏览器的新窗口中打开 url，否则在唯一的浏览器窗口中打开 url。别名 open_new()。

::

    controller.open_new_tab(url)

如果可能，在此控制器处理的浏览器的新页面（“标签”）中打开 url，否则等效于 open_new()。
