try 异常
############################

编写计算机程序时，通常能够区分正常和异常（不正常）情况。异常事件可能是错误（如试图除以零），也可能是通常不会发生的事情。为处理这些异常事件，可在每个可能发生这些事件的地方都使用条件语句。例如，对于每个除法运算，都检查除数是否为零。然而，这样做不仅效率低下、缺乏灵活性，还可能导致程序难以阅读。你可能很想忽略这些异常事件，希望它们不会发生，但 Python 提供功能强大的替代解决方案 —— **异常处理机制** 。

python 中可使用 ``try/except`` 语句，捕获异常。然后进行异常处理，就像下边这样：

.. highlight:: none

::

    try:
        代码块
    except NameError as e:
        NameError 异常时执行此代码
    except:
        其它异常时执行此代码
    else:
        没有引发异常时执行此代码
    finally:
        发生异常时执行清理工作
        
    # try 语句结束，继续执行后续操作
    
异常是什么
****************************

Python 使用异常对象来表示异常状态，并在遇到错误时引发异常。异常对象未被处理（或捕获）时，程序将终止并显示一条错误消息（traceback）。

::

    >>> 1 / 0
    Traceback (most recent call last):
       File "<stdin>", line 1, in ?
    ZeroDivisionError: integer division or modulo by zero

如果异常只能用来显示错误消息，就没多大意思了。但事实上，每个异常都是某个类（这里是 ZeroDivisionError）的实例。你能以各种方式引发和捕获这些实例，从而逮住错误并采取措施，而不是放任整个程序失败。


让事情沿你指定的轨道出错
****************************

正如你看到的，出现问题时，将自动引发异常。先来看看如何自主地引发异常，还有如何创建异常，然后再学习如何处理这些异常。

用 raise 语句引发异常
============================

要引发异常，可使用 raise 语句，并将一个类（必须是 Exception 的子类）或实例作为参数。将类作为参数时，将自动创建一个实例。下面的示例使用的是内置异常类 Exception ：

::

    >>> raise Exception
    Traceback (most recent call last):
       File "<stdin>", line 1, in ?
    Exception
    >>> raise Exception('hyperdrive overload')
    Traceback (most recent call last):
       File "<stdin>", line 1, in ?
    Exception: hyperdrive overload

在第一个示例中，引发的是通用异常，没有指出出现了什么错误。在第二个示例中，添加了错误消息 hyperdrive overload 。

有很多内置的异常类，下表描述了其中最重要的几个。这些异常类都可用于 raise 语句中。

=====================   =============
类名                       描述
=====================   =============
Exception                 几乎所有的异常类都是从它派生而来的
AttributeError            引用属性或给它赋值失败时引发
OSError                   操作系统不能执行指定的任务（如打开文件）时引发，有多个子类
IndexError                使用序列中不存在的索引时引发，为 LookupError 的子类
KeyError                  使用映射中不存在的键时引发，为 LookupError 的子类
NameError                 找不到名称（变量）时引发
SyntaxError               代码不正确时引发
TypeError                 将内置操作或函数用于类型不正确的对象时引发
ValueError                将内置操作或函数用于这样的对象时引发：其类型正确但包含的值不合适
Exception                 几乎所有的异常类都是从它派生而来的
AttributeError            引用属性或给它赋值失败时引发
OSError                   操作系统不能执行指定的任务（如打开文件）时引发，有多个子类
IndexError                使用序列中不存在的索引时引发，为 LookupError 的子类
KeyError                  使用映射中不存在的键时引发，为 LookupError 的子类
NameError                 找不到名称（变量）时引发
SyntaxError               代码不正确时引发
TypeError                 将内置操作或函数用于类型不正确的对象时引发
ValueError                将内置操作或函数用于这样的对象时引发：其类型正确但包含的值不合适
ZeroDivisionError         在除法或求模运算的第二个参数为零时引发
=====================   =============

自定义的异常类
============================

虽然内置异常涉及的范围很广，能够满足很多需求，但有时你可能想自己创建异常类。例如，在上面的超光速推进装置过载（hyperdrive overload）示例中，使用专用的 HyperdriveError 类来表示超光速推进装置的错误状态不是更自然吗？如果你要使用特殊的错误处理代码对超光速推进装置错误进行处理，就必须有一个专门用于表示这些异常的类。

那么如何创建异常类呢？就像创建其它类一样，但务必直接或间接地继承 Exception （这意味着从任何内置异常类派生都可以）。因此，自定义异常类的代码类似于下面这样：

::

    class SomeCustomException(Exception): pass

工作量真的不大。（当然，如果你愿意，也可在自定义异常类中添加方法。）

用 try 语句捕获异常
****************************

前面说过，异常比较有趣的地方是可对其进行处理，通常称之为捕获异常。为此，可使用 ``try/except`` 语句，当 ``try`` 执行错误时，才会执行 ``except`` 中的代码。假设你创建了一个程序，让用户输入两个数，再将它们相除，如下所示：

::

    x = int(input('Enter the first number: '))
    y = int(input('Enter the second number: '))
    print(x / y)

这个程序运行正常，直到用户输入的第二个数为零。

::

    Enter the first number: 10
    Enter the second number: 0
    Traceback (most recent call last):
      File "exceptions.py", line 3, in ?
        print(x / y)
    ZeroDivisionError: integer division or modulo by zero

为捕获这种异常并对错误进行处理（这里只是打印一条对用户更友好的错误消息），可像下面这样重写这个程序：

::

    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        print(x / y)
    except ZeroDivisionError:
        print("The second number can't be zero!")

使用一条 if 语句来检查 y 的值好像简单些，就本例而言，这可能也是更佳的解决方案。然而，如果这个程序执行的除法运算更多，则每个除法运算都需要一条 if 语句，而使用 ``try/except`` 的话只需要一个错误处理程序。

.. note ::

    异常从函数向外传播到调用函数的地方。如果在这里也没有被捕获，异常将向程序的最顶层传播。这意味着你可使用 ``try/except`` 来捕获他人所编写函数引发的异常。

不用提供参数
============================

捕获异常后，如果要重新引发它（即继续向上传播），可调用 raise 且不提供任何参数（也可显式地提供捕获到的异常）。

为说明这很有用，来看一个能够“抑制”异常 ZeroDivisionError 的计算器类。如果启用了这种功能，计算器将打印一条错误消息，而不让异常继续传播。在与用户交互的会话中使用这个计算器时，抑制异常很有用；但在程序内部使用时，引发异常是更佳的选择。下面是这样一个类的代码：

::

    class MuffledCalculator:
        muffled = False
        def calc(self, expr):
            try:
                return eval(expr)
            except ZeroDivisionError:
                if self.muffled:
                    print('Division by zero is illegal')
                else:
                    raise

.. note ::

    发生除零行为时，如果启用了“抑制”功能，方法 calc 将（隐式地）返回 None 。换而言之，如果启用了“抑制”功能，就不应依赖返回值。

下面的示例演示了这个类的用法（包括启用和关闭了抑制功能的情形）：

::

    >>> calculator = MuffledCalculator()
    >>> calculator.calc('10  2')
    5.0
    >>> calculator.calc('10  0') # 关闭了抑制功能
    Traceback (most recent call last): File "<stdin>", line 1, in ?
      File "MuffledCalculator.py", line 6, in calc
         return eval(expr)
      File "<string>", line 0, in ?
    ZeroDivisionError: integer division or modulo by zero
    >>> calculator.muffled = True
    >>> calculator.calc('10 / 0')
    Division by zero is illegal

如你所见，关闭抑制功能时，捕获了异常 ZeroDivisionError ，但继续向上传播它。

如果无法处理异常，在 except 子句中使用不带参数的 raise 通常是不错的选择，但有时你可能想引发别的异常。在这种情况下，导致进入 except 子句的异常将被作为异常上下文 存储起来，并出现在最终的错误消息中，如下所示：

::

    >>> try:
    ...     1/0
    ... except ZeroDivisionError:
    ...     raise ValueError
    ...
    Traceback (most recent call last):
      File "<stdin>", line 2, in <module>
    ZeroDivisionError: division by zero

在处理上述异常时，引发了另一个异常：

::

    Traceback (most recent call last):
      File "<stdin>", line 4, in <module>
    ValueError

你可使用 raise ... from ... 语句来提供自己的异常上下文，也可使用 ``None`` 来禁用上下文。

::

    >>> try:
    ...     1/0
    ... except ZeroDivisionError:
    ...     raise ValueError from None
    ...
    Traceback (most recent call last):
      File "<stdin>", line 4, in <module>
    ValueError

多个 except 子句
============================

如果你运行前一节的程序，并在提示时输入一个非数字值，将引发另一种异常。

::

    Enter the first number: 10
    Enter the second number: "Hello, world!"
    Traceback (most recent call last):
      File "exceptions.py", line 4, in ?
         print(x  y)
    TypeError: unsupported operand type(s) for: 'int' and 'str'

由于该程序中的 except 子句只捕获 ZeroDivisionError 异常，这种异常将成为漏网之鱼，导致程序终止。为同时捕获这种异常，可在 ``try/except`` 语句中再添加一个 except 子句。

::

    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        print(x / y)
    except ZeroDivisionError:
        print("The second number can't be zero!")
    except TypeError:
        print("That wasn't a number, was it?")

现在使用 if 语句来处理将更加困难。如何检查一个值能否用于除法运算呢？方法有很多，但最佳的方法无疑是尝试将两个值相除，看看是否可行。

另外，注意到异常处理并不会导致代码混乱，而添加大量的if 语句来检查各种可能的错误状态将导致代码的可读性极差。

一箭双雕
============================

如果要使用一个 except 子句捕获多种异常，可在一个元组中指定这些异常，如下所示：

::

    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        print(x / y)
    except (ZeroDivisionError, TypeError, NameError):
        print('Your numbers were bogus ...')

在上述代码中，如果用户输入字符串、其他非数字值或输入的第二个数为零，都将打印同样的错误消息。当然，仅仅打印错误消息帮助不大。另一种解决方案是不断地要求用户输入数字，直到能够执行除法运算为止。

在 except 子句中，异常两边的圆括号很重要。一种常见的错误是省略这些括号，这可能导致你不想要的结果。

捕获对象
============================

要在 except 子句中访问异常对象本身，可使用两个而不是一个参数。（请注意，即便是在你捕获多个异常时，也只向 except 提供了一个参数——一个元组。）需要让程序继续运行并记录（显示）错误时，这很有用。下面的示例程序打印发生的异常并继续运行：

::

    try:
        x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        print(x / y)
    except (ZeroDivisionError, TypeError) as e:
        print(e)

在这个小程序中，except 子句也捕获两种异常，但由于你同时显式地捕获了对象本身，因此可将其打印出来，让用户知道发生了什么情况。

一网打尽
============================

即使程序处理了好几种异常，还是可能有一些漏网之鱼。例如，对于前面执行除法运算的程序，如果用户在提示时不输入任何内容就按回车键，将出现一条错误消息，还有一些相关问题出在什么地方的信息（栈跟踪 ），如下所示：

::

    Traceback (most recent call last):
      ...
    ValueError: invalid literal for int() with base 10: ''

这种异常未被 ``try/except`` 语句捕获，这理所当然，因为你没有预测到这种问题，也没有采取相应的措施。在这些情况下，与其使用并非要捕获这些异常的 ``try/except`` 语句将它们隐藏起来，还不如让程序马上崩溃，因为这样你就知道什么地方出了问题。

然而，如果你就是要使用一段代码捕获所有的异常，只需在 except 语句中不指定任何异常类即可。

::

    try:
    x = int(input('Enter the first number: '))
        y = int(input('Enter the second number: '))
        print(x / y)
    except:
       print('Something wrong happened ...')

现在，用户想怎么做都可以。

::

    Enter the first number: "This" is completely

     illegal 123
    Something wrong happened ...

像这样捕获所有的异常很危险，因为这不仅会隐藏你有心理准备的错误，还会隐藏你没有考虑过的错误。这还将捕获用户使用 ``Ctrl + C`` 终止执行的企图、调用函数 sys.exit 来终止执行的企图等。在大多数情况下，更好的选择是使用 ``except Exception as e`` 并对异常对象进行检查。这样做将让不是从 Exception 派生而来的为数不多的异常成为漏网之鱼，其中包括 SystemExit 和 KeyboardInterrupt ，因为它们是从 BaseException （Exception 的超类）派生而来的。

万事大吉时
============================

在有些情况下，在没有出现异常时执行一个代码块很有用。为此，可像条件语句和循环一样，给 ``try/except`` 语句添加一个 else 子句。

::

    try:
        print('A simple task')
    except:
        print('What? Something went wrong?')
    else:
        print('Ah ... It went as planned.')

如果你运行这些代码，输出将如下：

::

    A simple task
    Ah ... It went as planned.

通过使用 else 子句，可以在 try 没有引发异常时执行 else 代码块。

::

    while True:
        try:
            x = int(input('Enter the first number: '))
            y = int(input('Enter the second number: '))
            value = x / y
            print('x / y is', value)
        except:
            print('Invalid input. Please try again.')
        else:
            break

在这里，仅当没有引发异常时，才会跳出循环（这是由 else 子句中的 break 语句实现的）。换而言之，只要出现错误，程序就会要求用户提供新的输入。下面是这些代码的运行情况：

::

    Enter the first number: 1
    Enter the second number: 0
    Invalid input. Please try again.
    Enter the first number: 'foo'
    Enter the second number: 'bar'
    Invalid input. Please try again.
    Enter the first number: baz
    Invalid input. Please try again.
    Enter the first number: 10
    Enter the second number: 2
    x / y is 5

前面说过，一种更佳的替代方案是使用空的 except 子句来捕获所有属于类 Exception（或其子类）的异常。你不能完全确定这将捕获所有的异常，因为 try/except 语句中的代码可能使用旧式的字符串异常或引发并非从 Exception 派生而来的异常。

::

    while True:
        try:
            x = int(input('Enter the first number: '))
            y = int(input('Enter the second number: '))
            value = x / y
            print('x / y is', value)
        except Exception as e:
            print('Invalid input:', e)
            print('Please try again')
        else:
            break

下面是这个程序的运行情况：

::

    Enter the first number: 1
    Enter the second number: 0
    Invalid input: integer division or modulo by zero
    Please try again
    Enter the first number: 'x' Enter the second number: 'y'
    Invalid input: unsupported operand type(s) for : 'str' and 'str'
    Please try again
    Enter the first number: quuux
    Invalid input: name 'quuux' is not defined
    Please try again
    Enter the first number: 10
    Enter the second number: 2
    x / y is 5

最后
============================

最后，还有 finally 子句，可用于在发生异常时执行清理工作。这个子句是与 try 子句配套的。

::

    x = None
    try:
        x = 1 / 0
    finally:
        print('Cleaning up ...')
        del x

在上述示例中，不管 try 子句中发生什么异常，都将执行 finally 子句。为何在 try 子句之前初始化 x 呢？因为如果不这样做，ZeroDivisionError 将导致根本没有机会给它赋值，进而导致在 finally 子句中对其执行 del 时引发未捕获的异常。

如果运行这个程序，它将在执行清理工作后崩溃。

::

    Cleaning up ...
    Traceback (most recent call last):
      File "C:\python\div.py", line 4, in ?
         x = 1 / 0
    ZeroDivisionError: integer division or modulo by zero

虽然使用 del 来删除变量是相当愚蠢的清理措施，但 finally 子句非常适合用于确保文件或网络套接字等得以关闭。

也可在一条语句中同时包含 try 、except 、finally 和 else （或其中的3个）。

::

    try:
        1 / 0
    except NameError:
        print("Unknown variable")
    else:
        print("That went well!")
    finally:
        print("Cleaning up.")

异常和函数
****************************

异常和函数有着天然的联系。如果不处理函数中引发的异常，它将向上传播到调用函数的地方。如果在那里也未得到处理，异常将继续传播，直至到达主程序（全局作用域）。如果主程序中也没有异常处理程序，程序将终止并显示栈跟踪消息。来看一个示例：

::

    >>> def faulty():
    ...     raise Exception('Something is wrong')
    ...
    >>> def ignore_exception():
    ...     faulty()
    ...
    >>> def handle_exception():
    ...     try:
    ...         faulty()
    ...     except:
    ...         print('Exception handled')
    ...
    >>> ignore_exception()
    Traceback (most recent call last):
      File '<stdin>', line 1, in ?
      File '<stdin>', line 2, in ignore_exception
      File '<stdin>', line 2, in faulty
    Exception: Something is wrong
    >>> handle_exception()
    Exception handled

如你所见，faulty 中引发的异常依次从 faulty 和ignore_exception 向外传播，最终导致显示一条栈跟踪消息。调用 handle_exception 时，异常最终传播到 handle_exception ，并被这里的 try/except 语句处理。

异常之禅
****************************

异常处理并不是很复杂。如果你知道代码可能引发某种异常，且不希望出现这种异常时程序终止并显示栈跟踪消息，可添加必要的 try/except 或 try/finally 语句（或结合使用）来处理它。

有时候，可使用条件语句来达成异常处理实现的目标，但这样编写出来的代码可能不那么自然，可读性也没那么高。另一方面，有些任务使用 if/else 完成时看似很自然，但实际上使用 try/except 来完成要好得多。下面来看两个示例。

假设有一个字典，你要在指定的键存在时打印与之相关联的值，否则什么都不做。实现这种功能的代码可能类似于下面这样：

::

    def describe_person(person):
        print('Description of', person['name'])
        print('Age:', person['age'])
        if 'occupation' in person:
            print('Occupation:', person['occupation'])

如果你调用这个函数，并向它提供一个包含姓名 Throatwobbler Mangrove 和年龄 42（但不包含职业）的字典，输出将如下：

::

    Description of Throatwobbler Mangrove
    Age: 42

如果你在这个字典中添加职业 camper，输出将如下：

::

    Description of Throatwobbler Mangrove
    Age: 42
    Occupation: camper

这段代码很直观，但效率不高（虽然这里的重点是代码简洁），因为它必须两次查找 'occupation' 键：一次检查这个键是否存在（在条件中），另一次获取这个键关联的值，以便将其打印出来。下面是另一种解决方案：

::

    def describe_person(person):
        print('Description of', person['name'])
        print('Age:', person['age'])
        try:
            print('Occupation:', person['occupation'])
        except KeyError: pass

在这里，函数直接假设存在 'occupation' 键。如果这种假设正确，就能省点事：直接获取并打印值，而无需检查这个键是否存在。如果这个键不存在，将引发 KeyError 异常，而 except 子句将捕获这个异常。

你可能发现，检查对象是否包含特定的属性时，try/except 也很有用。例如，假设你要检查一个对象是否包含属性 write ，可使用类似于下面的代码：

::

    try:
        obj.write
    except AttributeError:
        print('The object is not writeable')
    else:
        print('The object is writeable')

在这里，try 子句只是访问属性 write ，而没有使用它来做任何事情。如果引发了 AttributeError 异常，说明对象没有属性 write ，否则就说明有这个属性。具体使用哪种解决方案，在很大程度上取决于个人喜好。

请注意，这里在效率方面的提高并不大（实际上是微乎其微）。一般而言，除非程序存在性能方面的问题，否则不应过多考虑这样的优化。关键是在很多情况下，相比于使用 if/else ，使用 try/except 语句更自然，也更符合 Python 的风格。因此你应养成尽可能使用 try/except语句的习惯 。

.. note ::

    海军少将 Grace Hopper 有句至理名言：请求宽恕比获得允许更容易。这解释了 Python 偏向于使用 try/except 的原因。这种策略可总结为习语“闭眼就跳”——直接去做，有问题再处理，而不是预先做大量的检查。

不那么异常的情况
****************************

如果你只想发出警告 ，指出情况偏离了正轨，可使用模块 warnings 中的函数 warn 。

::

    >>> from warnings import warn
    >>> warn("I've got a bad feeling about this.")
    __main__:1: UserWarning: I've got a bad feeling about this.
    >>>

警告只显示一次。如果再次运行最后一行代码，什么事情都不会发生。

如果其他代码在使用你的模块，可使用模块 warnings 中的函数 filterwarnings 来抑制你发出的警告（或特定类型的警告），并指定要采取的措施，如 "error" 或 "ignore" 。

::

    >>> from warnings import filterwarnings
    >>> filterwarnings("ignore")
    >>> warn("Anyone out there?")
    >>> filterwarnings("error")
    >>> warn("Something is very wrong!")
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    UserWarning: Something is very wrong!

如你所见，引发的异常为 UserWarning 。发出警告时，可指定将引发的异常（即警告类别），但必须是 Warning 的子类。如果将警告转换为错误，将使用你指定的异常。另外，还可根据异常来过滤掉特定类型的警告。

::

    >>> filterwarnings("error")
    >>> warn("This function is really old...", DeprecationWarning)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    DeprecationWarning: This function is really old...
    >>> filterwarnings("ignore", category=DeprecationWarning)
    >>> warn("Another deprecation warning.", DeprecationWarning)
    >>> warn("Something else.")
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    UserWarning: Something else.

除上述基本用途外，模块 warnings 还提供了一些高级功能。如果你对此感兴趣，请参阅库参考手册。

小结
****************************

* 异常对象 ：异常情况（如发生错误）是用异常对象表示的。对于异常情况，有多种处理方式；如果忽略，将导致程序终止。
* 引发异常 ：可使用 raise 语句来引发异常。它将一个异常类或异常实例作为参数，但你也可提供两个参数（异常和错误消息）。如果在 except 子句中调用 raise 时没有提供任何参数，它将重新引发该子句捕获的异常。
* 自定义的异常类 ：你可通过从 Exception 派生来创建自定义的异常。
* 捕获异常 ：要捕获异常，可在 try 语句中使用 except 子句。在 except 子句中，如果没有指定异常类，将捕获所有的异常。你可指定多个异常类，方法是将它们放在元组中。如果向 except 提供两个参数，第二个参数将关联到异常对象。在同一条 try/except 语句中，可包含多个 except 子句，以便对不同的异常采取不同的措施。
* else 子句 ：除 except 子句外，你还可使用 else 子句，它在主 try 块没有引发异常时执行。
* finally ：要确保代码块（如清理代码）无论是否引发异常都将执行，可使用 try/finally ，并将代码块放在 finally 子句中。
* 异常和函数 ：在函数中引发异常时，异常将传播到调用函数的地方（对方法来说亦如此）。
* 警告 ：警告类似于异常，但（通常）只打印一条错误消息。你可指定警告类别 ，它们是 Warning 的子类。
