解决 pip 下载速度太慢
####################################

因为国内网络的原因， pip 的安装有时会出其的慢，尤其是在安装大包时。

其实在安装时可以加入国内的源，解决这个问题。可以使用以下方法：

.. highlight:: none

::

    pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple pyqt5

**常用库链接：**

- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 阿里云：http://mirrors.aliyun.com/pypi/simple/