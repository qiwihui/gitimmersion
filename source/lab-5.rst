做出修改
=========

目标
^^^^^^^^^

* 学习如何监控工作目录的状态。


修改 ``Hello, World`` 程序
---------------------------------

是时候修改我们的 ``hello`` 程序，使它能从命令行读取参数。将 ``hello.rb`` 文件修改为：

文件： ``hello.rb``

.. code-block:: ruby

    puts "Hello, #{ARGV.first}!"


检查状态
--------------

现在检查工作目录的状态。

.. code-block:: shell

    $ git status

你可以看到：

输出：

.. code-block:: shell

    $ git status
    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   hello.rb

    no changes added to commit (use "git add" and/or "git commit -a")

值得注意的第一件事情是 ``hello.rb`` 文件已被修改，但 Git 还没有被通知这些修改。

还要注意的是状态信息提示你接下来需要做什么。
如果你想要添加这些修改到仓库，可以使用 ``git add`` 命令。 否则，使用 ``git checkout`` 命令放弃修改。

.. admonition:: 译者注

    Git 2.23 引入了两个新命令 ``git switch`` 和 ``git restore``，用以替代现在的 ``git checkout``。
    ``git switch`` 用于分支管理，``git restore`` 用于文件的恢复。详细文档可以查看：
    `git switch <https://git-scm.com/docs/git-switch/2.23.0>`_ 和 `git restore <https://git-scm.com/docs/git-restore/2.23.0>`_。


下一步
-----------

让我们暂存更改。

