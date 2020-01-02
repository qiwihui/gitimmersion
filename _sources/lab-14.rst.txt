14. 撤销本地修改（在暂存之前）
==============================

目标
^^^^^^^^^^^

* 学习如何还原工作目录中的修改。


检出 Master
-------------

在处理之前确认你在 ``master`` 中的最新提交上。

.. code-block:: shell

    $ git checkout master


修改 ``hello.rb``
-------------------

有时候你修改了本地工作目录中的文件，这时你想要还原到已经提交的内容。``checkout`` 命令可以用来处理这种情况。

更改 ``hello.rb`` 让其具有错误的注释。

.. code-block:: ruby

    # This is a bad comment.  We want to revert it.
    name = ARGV.first || "World"

    puts "Hello, #{name}!"


检查状态
-------------

首先，检查工作目录的状态。

.. code-block:: shell

    $ git status

输出：

.. code-block:: shell

    $ git status
    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   hello.rb

    no changes added to commit (use "git add" and/or "git commit -a")

我们看到 ``hello.rb`` 已被修改，但还没有暂存。


还原工作目录中的修改
----------------------

使用 ``checkout`` 命令来检出 ``hello.rb`` 在仓库中的版本。

.. code-block:: shell

    $ git checkout hello.rb
    $ git status
    $ cat hello.rb

输出：

.. code-block:: shell

    $ git checkout hello.rb
    $ git status
    On branch master
    nothing to commit, working tree clean
    $ cat hello.rb
    # Default is "World"
    name = ARGV.first || "World"

    puts "Hello, #{name}!"

``status`` 命令显示在工作目录中没有未完成的更改。而且“错误的注释”也不是文件内容的一部分。
