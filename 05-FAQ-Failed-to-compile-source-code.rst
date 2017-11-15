FAQ: Failed to Compile Source Code
==============================================================================

(`这篇文档当然有中文版 <https://github.com/MacHu-GWU/Setup-Environment-for-Python-Developer/blob/master/05-%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%EF%BC%9A%E6%97%A0%E6%B3%95%E4%BB%8E%E6%BA%90%E4%BB%A3%E7%A0%81%E5%AE%89%E8%A3%85%E9%9C%80%E8%A6%81%E7%BC%96%E8%AF%91%E7%9A%84%E5%8C%85.rst>`_)

Some package only provides source code archive, when it has C code, (for example: https://pypi.python.org/pypi/backports.lzma), your ``pip install`` could failed with:

.. code-block:: console

    # Windows
    Unable to find vcvarsall.bat

or

.. code-block:: console

    # MacOS or Linux
    error: command 'gcc' failed with exit status 1

This is because Python can't find C compiler in your computer.


For Windows
------------------------------------------------------------------------------
Because there's a module ``distutils\msvc9compiler.py`` defines the logic finding C compiler. Even if you have installed it in Visual Studio Developer Toolkits, but python still not able to find it.

1. Download MicroSoft Python C++ Compiler: http://www.microsoft.com/en-us/download/confirmation.aspx?id=44266 (Python2.7 version also works for all)
2. Download and install it.
3. Open ``C:\PythonXX\Lib\distutils\msvc9compiler.py``.
4. Search ``def find_vcvarsall()``. The default behavior is to read regedit, but it not working.
5. Comment out everything, and add a new line ``return r"C:\Users\<your user name>\AppData\Local\Programs\Common\Microsoft\Visual C++ for Python\9.0"``. (It may varies in different machine, basically it is where did you install the MicroSoft Python C++ Compiler to)

Now the ``pip install`` command should have not problem.


For Linux
------------------------------------------------------------------------------

Use system built-in package control software, its apt-get in ubuntu, yum for redhat, install gcc compiler. When you see successful feedback when you type ``gcc`` in command line, it means OK.


For MacOS
------------------------------------------------------------------------------

Use HomeBrew to install gcc compiler. When you see successful feedback when you type ``gcc`` in command line, it means OK.