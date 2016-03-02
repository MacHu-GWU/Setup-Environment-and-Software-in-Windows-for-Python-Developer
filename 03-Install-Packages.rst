安装第三方包
============
安装Python的第三方库常用的方式主要有以下几种:

**pip install(推荐)**

使用Python社区的Package Control软件, pip。pip支持多种安装方式:

- 从PyPI的安装源在线安装
- 从 ``.tar.gz`` 或 ``.zip`` 源码安装
- 从 ``.whl``, 一种跨平台, 编译好的打包格式 ``wheel``, 进行安装

**easy_install**

使用早期的easy_install安装Python egg包。早期Python社区流行使用setuptools将源码打包成egg安装包, 然后再使用easy_install来安装打包好的egg包。

**windows compiled binary**

使用为windows平台打包编译好的可执行文件, 双击进行安装。

早期的easy_install已经过时; windows compiled binary有平台局限性; 所以目前最佳的方法是使用 ``pip``


"安装"到底是在干什么?
---------------------
我们通常说安装一个Python的扩展, 通常是指能够通过 ``import package_name`` 命令导入模块, 并使用其中的功能。第三方模块在Python中是被放置在 ``site-packages`` 目录下的, 在你执行 ``import`` 的时候, Python会自动搜索 ``site-packages``, 标准库目录, 以及当前 ``.py`` 文件所在的目录。

你可以通过运行下面的代码获得 ``site-packages`` 目录的绝对路径:

.. code-block:: python

	from __future__ import print_function
	import site

	print(site.getsitepackages()[0])

所以, 对于大多数的第三方包(通常是指纯Python实现, 没有调用任何其他第三方库的), 只要将其放在 ``site-packages`` 目录下即可成功被调用。但是有一些包需要安装其他依赖的库, 又或者包含一部分C代码, 需要编译。这时 **简单拷贝就不会奏效了**。所以, 下面我们来介绍

补充阅读:

由于Python是动态语言, 解释器在运行代码时会一行行地将Python代码编译好。
当我们安装时, Python会将 ``.py`` 或 ``.pyd`` (C语言文件)编译成机器码, 使得我们导入已安装的模块时调用的是编译好的代码, 免去了编译的过程。