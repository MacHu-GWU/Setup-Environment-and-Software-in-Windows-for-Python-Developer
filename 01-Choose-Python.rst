选择合适的Python版本
====================
请注意: 本文写于2016-03-01, 由于Python版本还在不断开发中, 可能具有2-3年的时效性。具体情况请结合当下的最新动态自行考虑。


不同版本的Python
----------------
Python的版本目前分为2.X和3.X两个分支并行开发。2.X目前的最新版本是2.7.11, 3.X是3.5.1。而在电脑上安装Python时, 我们通常指的是CPython。Python这个编程语言有着多种不同的实现, 有C语言实现的CPython, Java实现的Jython, C#实现的IronPython。而有一些公司将Python的源码编译, 预安装了一些第三方库, 然后内置了IDE, 就成了所谓的"发行版"。市场上比较有名的有: 科学计算发行版Enthought Canopy, 数据分析的发行版Anaconda。

那我们要如何选择呢?

**首先: Python2/Python3**

Python2目前在生产环境中大量使用, 而Python3的特性更为丰富, 写出的代码性能更好。在过去, 有很多第三方库不支持Python3是一个很大的问题, 这导致了生产环境下Python2很流行。而现在(2016年), Python2,3兼容的代码技术已经非常成熟了, 第三方库绝大多数已经全面支持Python3。鉴于Python3是趋势, 而且性能更优越, 个人觉得使用Python3进行开发, 写代码时注意兼容Python2是一个非常不错的选择。

顺带说一句, 建议Python2使用Python2.7.6, Python3使用Python3.4.4。

**其次: CPython vs Jython vs IronPython?**

最经典和广泛使用的是CPython。而Jython和IronPython则是Java后的Oracle公司和C#后的Microsoft公司为了无缝在自家语言的产品中嵌入灵活好用的Python代码, 而开发出的版本。具体内部实现细节和标准库的API可能跟CPython存在不兼容。而市面上的第三方库大多都是用CPython开发的, 所以会如果不是想用Java/C# 和 Python混合编程, 毫无疑问的使用CPython。

CPython下载地址: https://www.python.org/downloads/

**最后: 选择发行版**

发行版的优点在于, 免去了用户配置环境和安装IDE的痛苦, 预装了大量的第三方包, 内置了包管理软件。对于科学研究者来说, 确实是非常的方便。

补充阅读: 版本号命名规则

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.


CPython Interpreter(解释器) 安装和配置
--------------------------------------

Windows
~~~~~~~
Windows并没有自带Python。而Python.org在https://www.python.org/downloads/提供了各个版本的Windows安装包下载, 所以下载下来安装即可。

由于Windows命令行调用Python时, 实在环境变量中的目录中搜索Python的可执行程序。所以确保 ``C:\PythonXX`` 目录已添加到环境变量。(虽然最新的Python2和较新的Python3在安装时都会自动将目录添加到环境变量)

**对于多个Python版本同时存在的情况**, 推荐将各个Python版本的 ``python.exe`` 文件拷贝一份, 重命名为 ``pythonxx.exe``, 例如 ``python34.exe``。然后再命令行中, 使用不同的命令, 例如 ``python34 test.py``, 来区分用不同版本的Python执行你的程序。

补充: 编辑系统环境变量

右击 Computer -> Properties -> Advance system setting -> Environment Variable -> System Variable -> Path

多个目录用分号隔开。

Ubuntu
~~~~~~
Ubuntu自带Python27和Python34, 无需安装。

MacOS
~~~~~
Mac自带Python27。如需安装Python3, 则需要使用Mac系统下的开源软件管理工具Homebrew进行安装。