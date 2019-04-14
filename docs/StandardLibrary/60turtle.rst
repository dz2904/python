python turtle 模块
################################

turtle 是 python 内置的一个比较有趣味的模块，俗称海龟绘图，它是基于 tkinter 模块打造，提供一些简单的绘图工具，海龟作图最初源自 20 世纪 60 年代的 Logo 编程语言。之后一些 Python 程序员构建了 turtle 库，可以在 Python 中使用海龟作图。

在海龟作图中，我们可以编写指令让一个虚拟的（想象中的）海龟在屏幕上来回移动。这个海龟带着一只钢笔，我们可以让海龟在移动中使用这只钢笔来绘制线条。通过编写代码，以各种很酷的模式移动海龟，并绘制出令人惊奇的图片。使用海龟作图，我们不仅能够只用几行代码就创建出令人印象深刻的视觉效果，而且还可以跟随海龟看看每行代码如何影响到它的移动，这能够帮助我们理解代码的逻辑。所以海龟作图也常被用作新手学习 Python 的一种方式。

海龟移动
****************************

* forward() | fd()   # 向前移动
* backward() | bk() | back()   # 向后移动
* setx()   # 只移动 x 坐标值
* sety()   # 只移动 y 坐标值
* goto() | setpos() | setposition()   # 移到绝对位置
* home()   # 移动到原点
* setheading() | seth()   # 设置海龟的方向
* left() | lt()   # 向左转动
* right() | rt()   # 向右转动
* speed()   # 移动的速度

| turtle.**forward**(distance)
| turtle.**fd**(distance)
distance 一个数字（整数或浮点数）

按海龟的方向，向前移动指定的距离（distance 为正数）。

.. highlight:: none

::

    >>> turtle.position()
    (0.00,0.00)
    >>> turtle.forward(25)
    >>> turtle.position()
    (25.00,0.00)
    >>> turtle.forward(-75)
    >>> turtle.position()
    (-50.00,0.00)

| turtle.**back**(distance)
| turtle.**bk**(distance)
| turtle.**backward**(distance)
distance 一个数字

将海龟向后移动指定距离，不会改变海龟的方向。

::

    >>> turtle.position()
    (0.00,0.00)
    >>> turtle.backward(30)
    >>> turtle.position()
    (-30.00,0.00)

turtle. **setx** (x)
x 一个数字（整数或浮点数）

只改变 x 坐标值。

::

    >>> turtle.position()
    (0.00,240.00)
    >>> turtle.setx(10)
    >>> turtle.position()
    (10.00,240.00)

turtle.**sety**(y)
y 一个数字（整数或浮点数）

只改变 y 坐标值。

::

    >>> turtle.position()
    (0.00,40.00)
    >>> turtle.sety(-10)
    >>> turtle.position()
    (0.00,-10.00)

turtle.**goto**(x, y=None)
turtle.**setpos**(x, y=None)
turtle.**setposition**(x, y=None)
x 一个数字或一对数字
y 一个数字或 None

如果 y 是 None，则 x 必须是一对坐标或 Vec2D（例如由 pos() 返回）。

将海龟移到绝对位置，不会改变海龟的方向。

::

    >>> tp = turtle.pos()
    >>> tp
    (0.00,0.00)
    >>> turtle.setpos(60,30)
    >>> turtle.pos()
    (60.00,30.00)
    >>> turtle.setpos((20,80))
    >>> turtle.pos()
    (20.00,80.00)
    >>> turtle.setpos(tp)
    >>> turtle.pos()
    (0.00,0.00)

turtle.**home**()

将海龟移动到原点 - 坐标（0,0），并将其设置为起始方向（取决于模式，请参阅 mode()）。

::

    >>> turtle.heading()
    90.0
    >>> turtle.position()
    (0.00,-10.00)
    >>> turtle.home()
    >>> turtle.position()
    (0.00,0.00)
    >>> turtle.heading()
    0.0

turtle.**setheading**(to_angle)
turtle.**seth**(to_angle)
to_angle 一个数字（整数或浮点数）

将海龟的方向设置为 to_angle。以下是一些常用的度数方向：

============  ==============
标准模式        logo 模式
============  ==============
0 - 东          0 - 北
90 - 北         90 - 东
180 - 西        180 - 南
270 - 南        270 - 西
============  ==============

::

    >>> turtle.setheading(90)
    >>> turtle.heading()
    90.0

turtle.**left**(angle)
turtle.**lt**(angle)
angle 一个数字（整数或浮点数）

将海龟向左转动指定角度，角度方向取决于海龟模式。

::

    >>> turtle.heading()
    22.0
    >>> turtle.left(45)
    >>> turtle.heading()
    67.0

turtle.**right**(angle)
turtle.**rt**(angle)
angle 一个数字（整数或浮点数）

将海龟向右转动指定角度，角度方向取决于海龟模式。

::

    >>> turtle.heading()
    22.0
    >>> turtle.right(45)
    >>> turtle.heading()
    337.0

turtle.**speed**(speed=None)
speed 范围为 0~10 的整数或快捷键(见下文)

定义绘图的速度。如果没有给定参数，则返回当前速度。

如果输入的数字大于 10 或小于 0.5，则速度设置为 0。速度字符串映射到速度值，如下所示：

* "fastest": 0
* "fast": 10
* "normal": 6
* "slow": 3
* "slowest": 1

注意：speed = 0 相当于不发生动画。

::

    >>> turtle.speed()
    3
    >>> turtle.speed('normal')
    >>> turtle.speed()
    6
    >>> turtle.speed(9)
    >>> turtle.speed()
    9

返回海龟的位置
*********************************

* position() | pos()   # 返回海龟的当前位置
* xcor()   # 返回海龟的 x 坐标。
* ycor()   # 返回海龟的 y 坐标。
* heading()   # 返回海龟的当前方向
* distance()   # 返回从海龟到（x，y）之间的距离。
* towards()   # 返回从海龟位置到（x，y）之间的角度。

turtle.**position**()
turtle.**pos**()

返回海龟的当前位置（x，y）（作为 Vec2D 向量）。

::

    >>> turtle.pos()
    (440.00,-0.00)

turtle.**xcor**()

返回海龟的 x 坐标。

::

    >>> turtle.home()
    >>> turtle.left(50)
    >>> turtle.forward(100)
    >>> turtle.pos()
    (64.28,76.60)
    >>> print(round(turtle.xcor(), 5))
    64.27876

turtle.**ycor**()

返回海龟的 y 坐标。

::

    >>> turtle.home()
    >>> turtle.left(60)
    >>> turtle.forward(100)
    >>> print(turtle.pos())
    (50.00,86.60)
    >>> print(round(turtle.ycor(), 5))
    86.60254

turtle.**heading**()

返回海龟的当前方向（值取决于海龟模式，请参阅 mode()）。

::

    >>> turtle.home()
    >>> turtle.left(67)
    >>> turtle.heading()
    67.0

turtle.**distance**(x, y=None)
x 一个数字或一对数字或一个海龟实例的向量
y 一个数字，如果 x 是一个数字，否则为 None

返回从海龟到（x，y）之间的距离。

::

    >>> turtle.home()
    >>> turtle.distance(30,40)
    50.0
    >>> turtle.distance((30,40))
    50.0
    >>> joe = Turtle()
    >>> joe.forward(77)
    >>> turtle.distance(joe)
    77.0

turtle.**towards**(x, y=None)
x 一个数字或一对数字或一个海龟实例的向量
y 一个数字，如果 x 是一个数字，否则为 None

返回从海龟位置到（x，y）之间的角度（值取决于海龟模式，请参阅 mode()）。

::

    >>> turtle.goto(10, 10)
    >>> turtle.towards(0,0)
    225.0

海龟状态
**********************************

* showturtle() | st()   # 显示海龟
* hideturtle() | ht()   # 隐藏海龟
* isvisible()   # 如果海龟显示，返回 True
* shape()   # 设置或返回海龟形状
* shapesize() | turtlesize()   # 返回或设置海龟的变形属性
* resizemode()   # 设置或返回画笔箭头（海龟）大小的缩放模式
* shearfactor()   # 设置或返回当前的剪切因子
* tiltangle()   # 设置或返回当前的倾斜角度
* tilt()   # 从海龟当前的倾斜角度旋转它的角度
* shapetransform()   # 设置或返回海龟形状的当前转换矩阵
* get_shapepoly()   # 将当前形状多边形返回为坐标对的元组
* stamp()   # 在当前位置印上海龟副本图章
* clearstamp()   # 删除 turtle.stamp() 印在画布上的副本
* clearstamps()   # 删除多个 turtle.stamp() 印在画布上的副本

turtle.**showturtle**()
turtle.**st**()

显示海龟。


turtle.**hideturtle**()
turtle.**ht**()

隐藏海龟。


<span id="063"></span>
turtle.**isvisible**()

如果海龟状态为显示，则返回 True；如果海龟状态为隐藏，则返回 False。

::

    >>> turtle.hideturtle()
    >>> turtle.isvisible()
    False
    >>> turtle.showturtle()
    >>> turtle.isvisible()
    True

turtle.**shape**(name=None)
name 一个有效的shapename字符串。

设置或返回海龟形状。有以下几种形状："arrow", "turtle", "circle", "square", "triangle", "classic"。要了解如何处理形状，请参阅屏幕方法 register_shape()。

::

    >>> turtle.shape()
    'classic'
    >>> turtle.shape("turtle")
    >>> turtle.shape()
    'turtle'

turtle.**shapesize**(stretch_wid=None, stretch_len=None, outline=None)
turtle.**turtlesize**(stretch_wid=None, stretch_len=None, outline=None)
stretch_wid 一个正数
stretch_len 一个正数
outline 一个正数

返回或设置海龟的变形属性。当且仅当resizemode设置为 "user" 时，海龟将根据设置拉伸显示：stretch_wid 拉伸垂直方向，stretch_len 拉伸水平方向，outline 形状轮廓描边的宽度。

::

    >>> turtle.shapesize()
    (1.0, 1.0, 1)
    >>> turtle.resizemode("user")
    >>> turtle.shapesize(5, 5, 12)
    >>> turtle.shapesize()
    (5, 5, 12)
    >>> turtle.shapesize(outline=8)
    >>> turtle.shapesize()
    (5, 5, 8)

turtle.**resizemode**(rmode=None)
rmode 其中一个字符串 "auto", "user", "noresize"

设置或返回画笔箭头（海龟）大小的缩放模式。将 resizemode 设置为以下值之一：auto、user、noresize。如果没有给定 rmode，则返回当前的 resizemode。不同的残留有以下效果：

* "auto"：画笔箭头（海龟）随 pensize 变化而变化
* "user"：画笔箭头（海龟）大小取决于通过 shapesize()进行设置的 stretchfactor 和 outlinewidth (outline)的值。
* "noresize"：画笔箭头（海龟）大小不变

::

    >>> turtle.resizemode()
    'noresize'
    >>> turtle.resizemode("auto")
    >>> turtle.resizemode()
    'auto'

turtle.**shearfactor**(shear=None)
shear 一个数字（可选的）

设置或返回当前的剪切因子。根据给定的剪切因子剪切龟形，这是剪切角的切线。如果没有给出剪切：返回当前剪切因子。即剪切角的切线，平行于海龟方向的线被剪切。

::

    >>> turtle.shape("circle")
    >>> turtle.shapesize(5,2)
    >>> turtle.shearfactor(0.5)
    >>> turtle.shearfactor()
    0.5

turtle.**tiltangle**(angle=None)
angle 一个数字（可选）

设置或返回当前的倾斜角度。如果给出了角度，则不管当前的倾斜角度如何，都将海龟形状旋转指向角度指定的方向。只改变海龟的倾斜角度，并不影响海龟的绘图朝向(运动方向)。

::

    >>> turtle.reset()
    >>> turtle.shape("circle")
    >>> turtle.shapesize(5,2)
    >>> turtle.tilt(45)
    >>> turtle.tiltangle()
    45.0

turtle.**tilt**(angle)
angle 一个数字

从海龟当前的倾斜角度旋转它的角度，但是不会改变海龟的绘图朝向(运动方向)。

保持绘图朝向不变的前提下，旋转箭头方向

::

    >>> turtle.reset()
    >>> turtle.shape("circle")
    >>> turtle.shapesize(5,2)
    >>> turtle.tilt(30)
    >>> turtle.fd(50)
    >>> turtle.tilt(30)
    >>> turtle.fd(50)

turtle.**shapetransform**(t11=None, t12=None, t21=None, t22=None)
t11 一个数字（可选）
t12 一个数字（可选）
t21 一个数字（可选）
t12 一个数字（可选）

设置或返回海龟形状的当变形矩阵。

如果没有给出矩阵元素，则将变形矩阵的元组返回。否则，设置给定元素并根据由第一行 t11，t12 和第二行 t21,t22 组成的矩阵变换龟形。行列式 t11 * t22-t12 * t21 不能为零，否则会引发错误。根据给定的矩阵修改 stretchfactor，shearfactor 和 tiltangle。

::

    >>> turtle = Turtle()
    >>> turtle.shape("square")
    >>> turtle.shapesize(4,2)
    >>> turtle.shearfactor(-0.5)
    >>> turtle.shapetransform()
    (4.0, -1.0, -0.0, 2.0)

turtle.**get_shapepoly**()

将当前形状多边形返回为坐标对的元组。这可以用来定义一个新形状或复合形状的组件。

::

    >>> turtle.shape("square")
    >>> turtle.shapetransform(4, -1, 0, 2)
    >>> turtle.get_shapepoly()
    ((50, -20), (30, 20), (-50, 20), (-30, -20))

turtle.**stamp**()

在当前海龟位置上将海龟形状的副本印到画布上，并返回该副本的 stamp_id，可以通过调用 turtle.clearstamp(stamp_id) 来删除它。

::

    >>> turtle.color("blue")
    >>> turtle.stamp()
    11
    >>> turtle.fd(50)

turtle.**clearstamp**(stamp_id)
stampid 一个整数，必须是turtle.stamp()的返回值

删除 turtle.stamp() 印在画布上的副本。

::

    >>> turtle.position()
    (150.00,-0.00)
    >>> turtle.color("blue")
    >>> astamp = turtle.stamp()
    >>> turtle.fd(50)
    >>> turtle.position()
    (200.00,-0.00)
    >>> turtle.clearstamp(astamp)
    >>> turtle.position()
    (200.00,-0.00)
    *id="06E"></span>
    turtle.**clearstamps**(n=None)
    n 一个整数或 None

删除所有或第一张/最后一张海龟的 turtle.stamp() 副本。如果n为None，则删除所有的副本；如果 n>0 删除前 n 个副本，如果 n<0 删除后 n 个副本。

::

    >>> for i in range(8):
    ...     turtle.stamp(); turtle.fd(30)
    13
    14
    15
    16
    17
    18
    19
    20
    >>> turtle.clearstamps(2)
    >>> turtle.clearstamps(-2)
    >>> turtle.clearstamps()

特殊的海龟方法
**********************************

* begin_poly()   # 开始记录多边形的顶点
* end_poly()   # 停止记录多边形的顶点
* get_poly()   # 返回最后记录的多边形
* clone()   # 创建并返回具有相同位置、方向和海龟属性的克隆
* getturtle() | getpen()   # 返回 Turtle 对象本身
* getscreen()   # 返回正在绘制着海龟的 TurtleScreen 对象
* setundobuffer()   # 设置或禁用撤销功能
* undobufferentries()   # 获取当前剩余可撤销次数

turtle.**begin_poly**()

开始记录多边形的顶点。当前的海龟位置是多边形的第一个顶点。

turtle.begin_poly()、turtle.end_poly() 和 turtle.get_poly() 配合使用。

turtle.**end_poly**()

停止记录多边形的顶点。当前海龟位置是多边形的最后一个顶点，这将与第一个顶点连接。

turtle.**get_poly**()

返回最后记录的多边形，以元组方式返回记录的各个顶点坐标。

::

    >>> turtle.home()
    >>> turtle.begin_poly()
    >>> turtle.fd(100)
    >>> turtle.left(20)
    >>> turtle.fd(30)
    >>> turtle.left(60)
    >>> turtle.fd(50)
    >>> turtle.end_poly()
    >>> p = turtle.get_poly()
    >>> register_shape("myFavouriteShape", p)

turtle.**clone**()

创建并返回具有相同位置、方向和海龟属性的克隆。

::

    >>> mick = Turtle()
    >>> joe = mick.clone()
    >>> joe.fd(80)

turtle.**getturtle**()
turtle.**getpen**()

返回 Turtle 对象本身。只有合理的使用：作为返回“匿名海龟”的函数：

::

    >>> pet = getturtle()
    >>> pet.fd(50)
    >>> pet
    <turtle.Turtle object at 0x...>

turtle.**getscreen**()

返回正在绘制着海龟的 TurtleScreen 对象，获取该对象后就可以调用 TurtleScreen 方法了。

::

    >>> ts = turtle.getscreen()
    >>> ts
    <turtle._Screen object at 0x...>
    >>> ts.bgcolor("pink")

turtle.**setundobuffer**(size)
size 一个整数或 None

设置或禁用撤销功能，size 为 None 表示禁用撤销功能；否则设置多大，就可以通过调用 undo() 方法撤销多少次。如果 size 为 None，则禁用撤销功能。

::

    >>> turtle.setundobuffer(42)

turtle.**undobufferentries**()

获取当前剩余可撤销次数。

::

    >>> while undobufferentries():
    ...     undo()

画笔设置
*******************************

* pendown() | pd() | down()   # 按下画笔，移动时绘图
* penup() | pu() | up()   # 抬起画笔，移动时不绘图
* pensize() | width()   # 设置画笔大小（粗细）或返回画笔大小
* pencolor()   # 返回或设置画笔颜色
* pen()   # 画笔的所有状态和设置
* color()   # 返回或设置画笔颜色和填充颜色

turtle.**pendown**()
turtle.**pd**()
turtle.**down**()

按下画笔，移动时绘图。

turtle.**penup**()
turtle.**pu**()
turtle.**up**()

抬起画笔，移动时不绘图。

turtle.**pensize**(width=None)
turtle.**width**(width=None)
width 一个正数

设置画笔大小（粗细）或返回画笔大小。如果没有给出参数，则返回当前的 pensize。

::

    >>> turtle.pensize()
    1
    >>> turtle.pensize(10)

turtle.**pencolor**(\*args)

返回或设置 pencolor。

允许四种输入格式：

pencolor()
返回当前的画笔颜色，作为颜色指定字符串或作为元组（参见示例）。也可以当做 color/pencolor/fillcolor 调用的输入。

pencolor(colorstring)
将画笔颜色设置为 colorstring，这是 Tk 颜色规范字符串（Tkinter 模块是 Python 的标准 Tk GUI 工具包的接口），例如 "red"、"yellow" 或 "#33cc8c"。

pencolor((r, g, b))
将 pencolor 设置为 r、g、b 的元组代表的 RGB 颜色，r、g、b 的值都必须在 0~colormode 范围内。其中 colormode 是 1.0 或 255（参见 colormode()）。

pencolor(r, g, b)
将笔色设置为 r、g、b 代表的 RGB 颜色。

如果海龟绘制一个多边形，那么这个多边形的轮廓是用新设置的笔画画出来的。

::

    >>> colormode()
    1.0
    >>> turtle.pencolor()
    'red'
    >>> turtle.pencolor("brown")
    >>> turtle.pencolor()
    'brown'
    >>> tup = (0.2, 0.8, 0.55)
    >>> turtle.pencolor(tup)
    >>> turtle.pencolor()
    (0.2, 0.8, 0.5490196078431373)
    >>> colormode(255)
    >>> turtle.pencolor()
    (51.0, 204.0, 140.0)
    >>> turtle.pencolor('#32c18f')
    >>> turtle.pencolor()
    (50.0, 193.0, 143.0)

turtle.**pen**(pen=None, \*\*pendict)
pen 返回包含部分或全部设置画笔属性键的字典
pendict 以下列出的关键字作为关键字的一个或多个关键字参数

返回或设置所有的画笔属性。

使用以下键/值对在“笔字典”中设置笔的属性：

* "shown": True/False   # 显示画笔
* "pendown": True/False   # 落笔
* "pencolor": color-string or color-tuple   # 画笔颜色
* "fillcolor": color-string or color-tuple   # 填色
* "pensize": positive number   # 画笔大小
* "speed": number in range 0..10   # 画笔移动速度
* "resizemode": "auto" or "user" or "noresize"   # 海龟大小与画笔大小的对应模式
* "stretchfactor": (positive number, positive number)   # 拉伸因子
* "outline": positive number   # 海龟轮廓（描边宽度）
* "tilt": number   # 海龟角度

这个字典可以用作随后调用 pen() 来恢复前一笔状态的参数。此外，这些属性中的一个或多个可以作为关键字参数提供。这可以用于在一个语句中设置多个笔属性。

::

    >>> turtle.pen(fillcolor="black", pencolor="red", pensize=10)
    >>> sorted(turtle.pen().items())
    [('fillcolor', 'black'), ('outline', 1), ('pencolor', 'red'),
     ('pendown', True), ('pensize', 10), ('resizemode', 'noresize'),
     ('shearfactor', 0.0), ('shown', True), ('speed', 9),
     ('stretchfactor', (1.0, 1.0)), ('tilt', 0.0)]
    >>> penstate=turtle.pen()
    >>> turtle.color("yellow", "")
    >>> turtle.penup()
    >>> sorted(turtle.pen().items())[:3]
    [('fillcolor', ''), ('outline', 1), ('pencolor', 'yellow')]
    >>> turtle.pen(penstate, fillcolor="green")
    >>> sorted(turtle.pen().items())[:3]
    [('fillcolor', 'green'), ('outline', 1), ('pencolor', 'red')]

turtle.**color**(\*args)

返回或设置画笔颜色和画笔的填充颜色。

允许几种输入格式。它们使用 0 到 3 个参数:

color()
返回当前的 pencolor 和 fillcolor 颜色。

color(colorstring), color((r,g,b)), color(r,g,b)
指定一个颜色，将 pencolor 和 fillcolor 的颜色都更改为指定颜色。

color(colorstring1, colorstring2), color((r1,g1,b1), (r2,g2,b2))
指定两个颜色，将分别指定 pencolor 和 fillcolor 的颜色值。

如果 turtleshape 是多边形，则使用新设置的颜色绘制该多边形的轮廓和填充。

::

    >>> turtle.color("red", "green")
    >>> turtle.color()
    ('red', 'green')
    >>> color("#285078", "#a0c8f0")
    >>> color()
    ((40.0, 80.0, 120.0), (160.0, 200.0, 240.0))

另请参阅：屏幕方法 colormode()。

填充颜色
**********************************

* fillcolor()   # 返回或设置填充颜色。
* begin_fill()   # 在绘制要填充的形状之前调用
* end_fill()   # 填充 begin_fill() 和 end_fill() 之间绘制的形状
* filling()   # 返回填充状态（是否在填充模块之间）

turtle.**fillcolor**(\*args)

返回或设置填充颜色。

允许四种输入格式：

fillcolor()
可能以元组格式返回当前的 fillcolor 作为颜色指定字符串（请参示例）。

fillcolor(colorstring)
将 fillcolor 设置为 colorstring，这是 Tk 颜色规范字符串， 例如 "red", "yellow" 或 "#33cc8c"。

fillcolor((r, g, b))
将 fillcolor 设置为 r、g、b 的元组代表的 RGB 颜色，r、g、b 的值都必须在 0~colormode 范围内。其中 colormode 是 1.0 或 255（参见colormode()）。

fillcolor(r, g, b)
将 fillcolor 设置为 r、g、b 代表的 RGB 颜色，r、g、b 的每个颜色都必须在 0~colormode。

::

  >>> turtle.fillcolor("violet")
  >>> turtle.fillcolor()
  'violet'
  >>> col = turtle.pencolor()
  >>> col
  (50.0, 193.0, 143.0)
  >>> turtle.fillcolor(col)
  >>> turtle.fillcolor()
  (50.0, 193.0, 143.0)
  >>> turtle.fillcolor('#ffffff')
  >>> turtle.fillcolor()
  (255.0, 255.0, 255.0)

turtle.**begin_fill**()

在绘制要填充的形状之前调用。

turtle.**end_fill**()

填写最后一次调用 begin_fill() 后绘制的形状。

::

    >>> turtle.color("black", "red")
    >>> turtle.begin_fill()
    >>> turtle.circle(80)
    >>> turtle.end_fill()

turtle.**filling**()

返回填充状态（如果正在绘制填充图形则返回 True，否则为 False）。

::

    >>> turtle.begin_fill()
    >>> if turtle.filling():
    ...    turtle.pensize(5)
    ... else:
    ...    turtle.pensize(3)

撤销与清除
**********************************

* undo()   # 撤销(重复)最后一次海龟的动作
* reset() | clearscreen()    # 清空画布，并将海龟重置为初始状态
* clear() | resetscreen()   # 清空画布，不移动海龟

turtle.**undo**()

撤销(重复)最后一次海龟的动作。可用撤消操作的数量取决于缓冲区的大小。

::

    >>> for i in range(4):
    ...     turtle.fd(50); turtle.lt(80)
    ...
    >>> for i in range(8):
    ...     turtle.undo()

turtle.**reset**()
turtle.**resetscreen**()

清空画布，并将屏幕上的所有海龟重置为其初始状态。

turtle.**clear**()
turtle.**clearscreen**()

清空画布，不移动海龟。

画圆和添加文本
**********************************

* circle()   # 绘制一个圆或多边形
* dot()   # 绘制一个圆点
* write()   # 写入文本
* textinput   # 弹出一个用于输入字符串的对话窗口
* numinput   # 弹出一个用于输入数字的对话窗口

turtle.**circle**(radius, extent=None, steps=None)
radius 一个数字（圆的半径）
extent 一个数字或 None（圆的角度）
steps 一个数字或 None（圆的步长，可用于绘制多边形）

按给定的半径画圆，当前位置为圆的初始端点。extent 一个角度，绘制一个扇形（默认绘制一个整圆）；如果半径为正则逆时针绘制圆，相反半径为负数则顺时针绘制圆。

::

    >>> turtle.home()
    >>> turtle.position()
    (0.00,0.00)
    >>> turtle.heading()
    0.0
    >>> turtle.circle(50)
    >>> turtle.position()
    (-0.00,0.00)
    >>> turtle.heading()
    0.0
    >>> turtle.circle(120, 180)  # draw a semicircle
    >>> turtle.position()
    (0.00,240.00)
    >>> turtle.heading()
    180.0

turtle.**dot**(size=None, \*color)
size 一个整数 >= 1 (如果给出)
color 一个颜色字符串或一个数字颜色元组

用指定直径和颜色绘制圆点。如果没有给出 size，则使用 pensize+4 和 2*pensize 之间的最大值。

::

    >>> turtle.home()
    >>> turtle.dot()
    >>> turtle.fd(50); turtle.dot(20, "blue"); turtle.fd(50)
    >>> turtle.position()
    (100.00,-0.00)
    >>> turtle.heading()
    0.0

turtle.**write**(arg, move=False, align="left", font=("Arial", 8, "normal"))
arg 要写入 TurtleScreen 的文本内容
move – True/False 设置是否绘制
align 设置文本下方初始位置 "left", "center" 或 "right"
font – a triple（fontname，fontsize，fonttype）设置字体

根据对齐方式和给定字体，在当前海龟位置插入文本。如果移动为真，则将海龟移动到文本末尾的右下角。默认情况下，move 是 False。

::

    >>> turtle.write("Home = ", True, align="center")
    >>> turtle.write((0,0), True)
    >>> turtle.write("HomeDelete the turtle’s drawings from the screen. ", True, align="center",font=("Arial", 16, "normal"))

turtle.**textinput**(title, prompt)
title 弹框标题（一个 string 字符串）
prompt 弹框提示（一个 string 字符串）

弹出一个用于输入字符串的对话窗口。参数标题是对话窗口的标题，提示是主要描述要输入什么信息的文本。点击 Cancel 取消按钮则返回 None，点击 Ok 按钮返回输入的字符串。

::

    >>> screen.textinput("NIM", "Name of first player:")

turtle.**numinput**(title, prompt, default=None, minval=None, maxval=None)
title 弹框标题（一个 string 字符串）
prompt 弹框标题（一个 string 字符串）
default 数字（可选）
minval 数字（可选）
maxval 数字（可选）

弹出一个用于输入数字的对话窗口。标题是对话窗口的标题，提示是主要描述输入什么数字信息的文本。default：默认值；minval：输入的最小值；maxval：输入的最大值，输入的数字必须在 minval~maxval 范围内（如果给出）。如果没有，则发出提示并且对话框保持打开状态以进行更正。点击 Cancel 取消按钮则返回 None，点击 Ok 按钮返回输入的 number。

::

    >>> screen.numinput("Poker", "Your stakes:", 1000, minval=10, maxval=10000)

鼠标点击事件
**********************************

* onclick()   # 鼠标左键点击海龟箭头位置，按下时触发绑定函数
* onrelease()   # 鼠标左键在当前海龟箭头位置，按下并弹起时触发绑定函数
* ondrag()   # 鼠标左键在当前海龟箭头位置，按下并拖动时触发绑定函数

turtle.**onclick**(fun, btn=1, add=None)
turtle.**onscreenclick**(fun, btn=1, add=None)
fun 一个带有两个参数的函数，这些参数将与画布上单击点的坐标一起调用
num 鼠标按键的数量，默认为1（鼠标左键）
add – True or False 如果为True，则会添加新的绑定，否则将替换以前的绑定

画布上鼠标左键在当前海龟箭头位置按下时绑定一个函数;如果函数为None,则移除存在的绑定

::

    >>> def turn(x, y):
    ...     left(180)
    ...
    >>> onclick(turn)  # Now clicking into the turtle will turn it.
    >>> onclick(None)  # event-binding will be removed

turtle.**onrelease**(fun, btn=1, add=None)
fun 一个带有两个参数的函数，这些参数将与画布上单击点的坐标一起调用
num 鼠标按钮的数量，默认为1（鼠标左键）
add – True or False 如果为True，则会添加新的绑定，否则将替换以前的绑定

画布上鼠标左键在当前海龟箭头位置弹起时绑定一个函数；如果函数为None,则移除存在的绑定

::

    >>> class MyTurtle(Turtle):
    ...     def glow(self,x,y):
    ...         self.fillcolor("red")
    ...     def unglow(self,x,y):
    ...         self.fillcolor("")
    ...
    >>> turtle = MyTurtle()
    >>> turtle.onclick(turtle.glow)   # clicking on turtle turns fillcolor red,
    >>> turtle.onrelease(turtle.unglow) # releasing turns it to transparent.

turtle.**ondrag**(fun, btn=1, add=None)
fun 一个带有两个参数的函数，这些参数将与画布上单击点的坐标一起调用
num 鼠标按钮的数量，默认为1（鼠标左键）
add – True or False 如果为True，则会添加新的绑定，否则将替换以前的绑定

画布上鼠标左键在当前海龟箭头位置按下并拖动时绑定一个函数;如果函数为None,则移除存在的绑定

备注：在海龟上的每一个鼠标移动事件序列都在该海龟的鼠标点击事件之前。

::

    >>> turtle.ondrag(turtle.goto)

随后，点击并拖动海龟将在屏幕上移动，从而生成手绘图（如果笔落下）。

按键事件
========================

* listen()   # 让海龟屏幕 TurtleScreen 的对象获取焦点
* onkey() | onkeyrelease()   # 按键触发函数（按下并抬起）
* onkeypress()   # 按键触发函数（按下）
* ontimer()   # 开启一个计时器
* mainloop() | done()   # 运行后屏幕自动消失

turtle.**listen**(xdummy=None, ydummy=None)

为了收集关键事件，让海龟屏幕 TurtleScreen 的对象获取焦点。提供虚拟参数是为了能够将 listen() 传递给 onclick 方法。

turtle.**onkey**(fun, key)
turtle.**onkeyrelease**(fun, key)
fun 一个无参函数或 None
key 一个字符串，普通按键（例如："a"）或功能键（例如："space"）

键盘上 key 键 key-release 事件触发时（即按下并抬起）绑定一个无参函数；如果第一个参数 fun 为 None，则移除绑定的函数。备注：前提是海龟屏幕 TurtleScreen 对象需要通过 screen.listen() 方法获取焦点了（请参阅listen()方法）。

::

    >>> def f():
    ...     fd(50)
    ...     lt(60)
    ...
    >>> screen.onkey(f, "Up")
    >>> screen.listen()

turtle.**onkeypress**(fun, key=None)
fun 一个无参函数或 None
key 一个字符串，普通按键（例如："a"）或功能键（例如："space"）

键盘上 key 键（如果 key 为 None 时表示任意按键）按下时即 key-press 事件触发时绑定一个无参函数；如果第一个参数 fun 为 None，则移除绑定的函数。备注：前提是海龟屏幕 TurtleScreen 对象需要通过 screen.listen() 方法获取焦点了（请参阅 listen() 方法）。

::

    >>> def f():
    ...     fd(50)
    ...
    >>> screen.onkey(f, "Up")
    >>> screen.listen()

turtle.**ontimer**(fun, t=0)
fun 一个无参的函数
t 一个数字 >= 0

开启一个计时器，t 毫秒后调用函数 fun。

::

    >>> running = True
    >>> def f():
    ...     if running:
    ...         fd(50)
    ...         lt(60)
    ...         screen.ontimer(f, 250)
    >>> f()   ### makes the turtle march around
    >>> running = False

turtle.**mainloop**()
turtle.**done**()

运行后命令输入将挂起，直到主动关闭当前窗口（点击绘图窗口右上角的关闭按钮或程序调用 screen.bye() 或 turtle.bye() 函数），想使用的话必须作为图形绘制程序的最后一条语句。

::

    >>> screen.mainloop()

TurtleScreen/Screen 方法
################################

窗口控制
**********************************

* bgcolor()   # 设置或返回 TurtleScreen 的背景颜色
* bgpic()   # 设置当前 backgroundimage 的背景图片或返回名称
* screensize()   # 设置或返回窗口大小
* setworldcoordinates()   # 设置用户自定义的坐标系统

turtle.**bgcolor**(\*args)
args 一个颜色字符串或 3 个范围是 0-colormode 的数字（请参考 fillcolor()）

设置或返回 TurtleScreen 的背景颜色。

::

    >>> screen.bgcolor("orange")
    >>> screen.bgcolor()
    'orange'
    >>> screen.bgcolor("#800080")
    >>> screen.bgcolor()
    (128.0, 0.0, 128.0)

turtle.**bgpic**(picname=None)
picname 一个 gif 的字符串名字或 "nopic" 字符串或 None

设置/删除背景图片或返回当前的背景图片名。如果 picname 是 gif 格式的文件名，则设置为背景图像。如果图片名称是 "nopic"，则删除背景图片（如果存在）。如果 picname 为 None，则返回当前 backgroundimage 的文件名。

::

    >>> screen.bgpic()
    'nopic'
    >>> screen.bgpic("landscape.gif")
    >>> screen.bgpic()
    "landscape.gif"

turtle.**screensize**(canvwidth=None, canvheight=None, bg=None)
canvwidth 画布宽度（正整数，以像素为单位）
canvheight 画布高度（正整数，以像素为单位）
bg 背景颜色（颜色字符串或颜色元组）

设置或返回窗口大小。如果没有给出参数，则返回当前值（画布宽度，画布高度），否则会调整画布大小。

::

    >>> screen.screensize()
    (400, 300)
    >>> screen.screensize(2000,1500)
    >>> screen.screensize()
    (2000, 1500)

turtle.**setworldcoordinates**(llx, lly, urx, ury)
llx 一个数字，画布左下角的x坐标
lly 一个数字，画布左下角的y坐标
urx 一个数字，画布右上角的x坐标
ury 一个数字，画布右上角的y坐标

设置用户自定义的坐标系统，如果必要的话需要切换到 "world" 模式，如果 "world" 模式已经是活动的，则会根据新的坐标重绘图纸。

注意：在用户定义的坐标系中，角度可能会出现扭曲。

::

    >>> screen.reset()
    >>> screen.setworldcoordinates(-50,-7.5,50,7.5)
    >>> for _ in range(72):
    ...     left(10)
    ...
    >>> for _ in range(8):
    ...     left(45); fd(2)   # a regular octagon

动画控制
=============================

* delay()   # 设置或返回以毫秒为单位的绘图延迟
* tracer()   # 打开/关闭海龟动画并为更新图纸设置延迟
* update()   # 执行 TurtleScreen 更新

turtle.**delay**(delay=None)
delay 正整数

设置或返回绘制延迟（单位:毫秒）。绘图延迟的时间越长，动画的速度就越慢。

::

    >>> screen.delay()
    10
    >>> screen.delay(5)
    >>> screen.delay()
    5

turtle.**tracer**(n=None, delay=None)
n 非负整数
delay 非负整数

打开/关闭海龟动画，并设置绘制延迟。如果给出 n，则仅实际执行每个第 n 个常规屏幕更新。（可用于加速绘制复杂图形）。当不带参数调用时，返回当前存储的 n 值。第二个参数设置延迟值（参见delay()）。

::

    >>> screen.tracer(8, 25)
    >>> dist = 2
    >>> for i in range(200):
    ...     fd(dist)
    ...     rt(90)
    ...     dist += 2

turtle.**update**()

更新海龟屏幕 TurtleScreen 对象，tracer 关闭时使用。

另见 RawTurtle/Turtle 方法 speed()。

设置与特殊方法
**********************************

* mode()   # 设置或返回海龟模式
* colormode()   # 设置或返回海龟颜色模式
* getcanvas()   # 返回海龟屏幕 TurtleScreen 的画布对象实例
* getshapes()   # 返回所有当前可用海龟形状的名称列表
* register_shape() | addshape()   # 内存中添加注册海龟图形
* turtles()   # 返回海龟屏幕 TurtleScreen 中所有的海龟箭头对象列表
* window_height()   # 返回海龟绘图窗口的高度
* window_width()   # 返回海龟绘图窗口的宽度

turtle.**mode**(mode=None)
mode 其中一个字符串 "standard", "logo" 或 "world"

设置或返回海龟模式，默认是 "standard" 标准模式。

"standard" 模式是兼容旧版本；"logo" 模式兼容大部分海龟图形标志；"world" 模式使用用户自定义的“世界坐标”，该模式下x/y的单位比不为1会出现扭曲。

============  ================  ==============
模式            初始的海龟方向      角度方向
============  ================  ==============
"standard"     向右（东）           逆时针
"world"        向右（东）           逆时针
"logo"         向上（北）           顺时针
============  ================  ==============

::

    >>> mode("logo")   # resets turtle heading to north
    >>> mode()
    'logo'

turtle.**colormode**(cmode=None)
cmode 其中一个值 1.0 或 255

返回或设置 colormode 的值为 1.0 或 255，随后调用 turtle.fillcolor(\*args)、turtle.pencolor(\*args)、turtle.color(\*args) 等方法设置画笔颜色时 R，G，B 三组颜色值范围必须是 0~colormode 值之间的数，否则会报异常。

::

    >>> screen.colormode(1)
    >>> turtle.pencolor(240, 160, 80)
    Traceback (most recent call last):
         ...
    TurtleGraphicsError: bad color sequence: (240, 160, 80)
    >>> screen.colormode()
    1.0
    >>> screen.colormode(255)
    >>> screen.colormode()
    255
    >>> turtle.pencolor(240,160,80)

turtle.**getcanvas**()

返回海龟屏幕 TurtleScreen 的画布对象实例。对于知道如何处理 Tkinter 的内部人士非常有用。

::

    >>> cv = screen.getcanvas()
    >>> cv
    <turtle.ScrolledCanvas object ...>

turtle.**getshapes**()

返回所有当前可用海龟形状的名称列表。

::

    >>> screen.getshapes()
    ['arrow', 'blank', 'circle', ..., 'turtle']

turtle.**register_shape**(name, shape=None)
turtle.**addshape**(name, shape=None)

在内存中添加注册海龟图形。

有三种不同的方法可以调用这个函数：

1. name 是 gif 文件的名称，shape 是 None：安装相应的图像形状。

::

    >>> screen.register_shape("turtle.gif")

注意转动龟时图像形状不旋转，因此它们不显示龟的标题！

2. name 是一个任意字符串，shape 是坐标对的元组：安装相应的多边形形状。

::

    >>> screen.register_shape("triangle", ((5,-3), (0,5), (-5,-3)))

3. 名称是一个任意字符串，形状是一个（复合）形状对象：安装相应的复合形状。

将龟形添加到 TurtleScreen 的形状列表中。只有通过发布命令形状（形状名称）才能使用这样注册的形状。

turtle.**turtles**()

返回海龟屏幕 TurtleScreen 中所有的海龟箭头对象列表。

::

    >>> for turtle in screen.turtles():
    ...     turtle.color("red")

turtle.**window_height**()

返回海龟绘图窗口的高度（单位：像素）。

::

    >>> screen.window_height()
    480

turtle.**window_width**()

返回海龟绘图窗口的宽度（单位：像素）。

::

    >>> screen.window_width()
    640

屏幕特有的方法
**********************************

* bye()   # 关闭海龟图形窗口
* exitonclick()   # 运行后屏幕自动消失,调用这句后屏幕会保持,直到点击屏幕才会关闭海龟图形窗口
* setup()   # 设置默认展现的主窗口的大小和位置
* title()   # 设置海龟窗口标题

turtle.**bye**()

关闭 turtlegraphics 窗口。

turtle.**exitonclick**()

将 bye() 方法绑定到屏幕上的鼠标点击。运行后屏幕自动消失，调用这句后屏幕会保持，直到点击屏幕才会关闭海龟图形窗口。

如果配置字典中使用 IDLE 的值为 False（默认值），也输入 mainloop。注：如果使用 -n 开关（不使用子进程）空闲，则在 turtle.cfg 中此值应该设置为 True。在这种情况下，IDLE 自己的主循环对于客户端脚本也是活动的。

turtle.**setup**(width=\_CFG["width"], height=\_CFG["height"], startx=\_CFG["leftright"], starty=\_CFG["topbottom"])

设置默认展现的主窗口的大小和位置（宽或高比海龟绘图窗口小时对应方向上会出现滚动条）。参数的默认值存储在 turtle.cfg配置文件中，可以通过 turtle 更改 turtle.cfg 文件。

* width 一个整数（单位：像素）或一个小数（表示百分比），默认是屏幕宽的50%
* height 一个整数（单位：像素）或一个小数（表示百分比），默认是屏幕高的75%
* startx 如果是正数，则从屏幕左边缘开始向右（单位：像素）；如果为负数则从屏幕右边缘开始向左；如果为 None 则窗口水平居中
* starty 如果是正数,则从屏幕顶部边缘开始向下（单位：像素）；如果为负数则从屏幕底部边缘开始向上；如果为 None 则窗口垂直居中

::

    >>> screen.setup (width=200, height=200, startx=0, starty=0)
    >>>            # sets window to 200x200 pixels, in upper left of screen
    >>> screen.setup(width=.75, height=0.5, startx=None, starty=None)
    >>>            # sets window to 75% of screen by 50% of screen and centers

turtle.**title**(titlestring)
titlestring 显示在海龟图形窗口标题栏中的字符串

将 turtle 窗口的标题设置为 titlestring。

::

    >>> screen.title("Welcome to the turtle zoo!")
