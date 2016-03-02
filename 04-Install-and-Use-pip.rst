安装和使用Python社区包管理工具pip
=================================
Python社区的Package Control工具pip, 功能强大, 更新快速, 跨平台, 是当下用来管理Python第三方包的最佳选择, 适用于全平台。

pip的官方文档主页: https://pip.pypa.io/en/latest/installing/


安装pip
-------
在pip官方主页下载安装文件 ``get-pip.py``, 然后你想给你的哪个Python版本安装pip, 就用哪个版本的Python运行这个文件。这个文件的原理是将pip的二进制内容编码成了字符串, 然后解压安装。如果你用的是旧的 ``get-pip.py`` 文件, 那么你最终安装好的可能也是旧版本的pip。所以建议在使用 ``get-pip.py`` 安装完之后, 在命令行运行一次这里(https://pip.pypa.io/en/latest/installing/#upgrading-pip)的命令将pip升级到最新版。


使用pip安装第三方包
-------------------
我们常用的几种安装模式如下:

1. 从PyPI下载在线安装: ``pip install SomePackage``, 需要联网, 在线安装, 对包的名字的大小写不敏感。
2. 安装指定的某个版本: ``pip install requests==2.6.1``
3. 安装符合条件的最低的版本: ``pip install requests>=2.6.0``
4. 安装符合条件的最高的版本: ``pip install requests<=2.9.1``
5. 从源码安装: ``pip install SomePackage.zip`` 或 ``pip install SomePackage.tar.gz``, 等效于: Extract archive, Build, Install, Clean up的全过程。
6. 从Wheel包安装: ``pip install SomePackage-1.0-py2.py3-none-any.whl``。


理解并使用 ``requirements.txt`` 文件
----------------------------------
``requirements.txt`` 文件是一种包含Python第三方包需求的信息的特殊格式的文件。可以用来将一个项目中用到的所有的Python第三方包的信息保存在此文件中。以后就能使用pip直接根据文件中的记录, 自动安装所需的所有第三方包。requirements文件的格式请参考: https://pip.pypa.io/en/latest/reference/pip_install/#requirements-file-format