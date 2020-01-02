9. 聚焦修改，而不是文件
===========================

目标
^^^^^^^^

* 了解 Git 聚焦于修改，而不是文件本身。

大多数源码控制系统都使用文件。你将文件添加到源代码管理中，系统将从该点开始跟踪对该文件的修改。

Git 聚焦于文件的修改而非文件本身。当你使用 Git 添加文件 ``git add file`` 时，你并非在告诉 Git 要添加文件到仓库。
而是说 Git 应当对文件的当前状态做记录以便稍后提交。

我们将尝试在本次实验中探索其中的差异。


初次修改：允许默认名称
------------------------

如果未提供命令行参数，更改 ``Hello, World`` 程序接受一个默认值。

.. code-block:: ruby

    name = ARGV.first || "World"

    puts "Hello, #{name}!"


添加修改
-----------

现在添加此次修改到 Git 的暂存区。

.. code-block:: shell

    $ git add hello.rb


第二次修改：添加注释
-----------------------

现在给 ``Hello, World`` 程序添加一行注释。

.. code-block:: ruby

    # Default is "World"
    name = ARGV.first || "World"

    puts "Hello, #{name}!"

检查当前状态

.. code-block:: shell

    $ git status

你可以看到：

.. code-block:: shell

    $ git status
    On branch master
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        modified:   hello.rb

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   hello.rb

注意 ``hello.rb`` 在状态中被列了两次。第一次修改已被暂存，且准备提交。第二次修改还未暂存。如果你现在提交，那么注释不会保存到仓库中。

让我们试试看。


提交
------

提交暂存的修改，然后重新检查状态。

.. code-block:: shell

    $ git commit -m "Added a default value"
    $ git status

你可以看到：

.. code-block:: shell

    $ git commit -m "Added a default value"
    [master dc1d42f] Added a default value
    1 file changed, 3 insertions(+), 1 deletion(-)
    $ git status
    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   hello.rb

    no changes added to commit (use "git add" and/or "git commit -a")


``status`` 命令告诉你 ``hello.rb`` 还有未记录的更改，且不在暂存区。


添加第二次修改
-----------------

现在添加第二次修改到暂存区，然后执行 ``git status``。

.. code-block:: shell

    $ git add .
    $ git status

**注意**：我们使用当前目录（``.``）作为要添加的文件。这是一种添加当前目录及其子目录下所有修改文件的习惯简写方式。
但因为它添加所有修改，所以在做 ``add .`` 前检查状态是一个好主意，只是为了确定你没有添加不想要的文件。

我想你已经明白了 ``add .`` 这个技巧，但为了安全，在余下的教程中我们将继续直接添加文件。

你可以看到：

.. code-block:: shell

    $ git status
    On branch master
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        modified:   hello.rb

现在第二次修改已经暂存，且准备提交。


提交第二次更改
---------------

.. code-block:: shell

    $ git commit -m "Added a comment"
