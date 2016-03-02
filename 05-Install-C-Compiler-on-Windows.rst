在Windows下安装C++编译器
========================
在使用源码安装, 或pip安装那些包含有C代码的第三方库时, 通常会出现如下错误:

.. code-block:: console

    Unable to find vcvarsall.bat

这是因为Python标准库中用于安装Python包的 ``distutils\msvc9compiler.py`` 模块中有一套默认的搜索C编译器的机制, 而这套机制在Windows系统下缺并不能成功找到。


Windows下的解决方法
-------------------
1. 下载微软的Python专用C++编译器: http://www.microsoft.com/en-us/download/confirmation.aspx?id=44266
2. 安装下载好的编译器。
3. 打开 ``C:\PythonXX\Lib\distutils\msvc9compiler.py``。
4. 搜索 ``def find_vcvarsall()`` 找到这个关键的方法。这个方法默认的方式是通过读取windows注册表来尝试寻找vcvarsall.
5. 把函数的全部内容注释掉, 增加一行 ``return r"C:\Users\<your user name>\AppData\Local\Programs\Common\Microsoft\Visual C++ for Python\9.0"``。(各个机器上微软C++编译器的安装目标路径可能不同, 请根据情况自行修改)

这样所有包含C代码的包就可以被顺利安装了。


Linux下的解决方法
-----------------
TODO


MacOS下的解决方法
-----------------
TODO