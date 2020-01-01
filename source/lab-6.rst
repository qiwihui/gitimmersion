暂存修改
==========

目标
^^^^^^

* 学习如何暂存修改用于之后提交。


添加修改
------------

现在告诉 Git 暂存修改，并检查状态。

.. code-block:: shell

    $ git add hello.rb
    $ git status

你可以看到：

.. code-block:: shell

    $ git add hello.rb
    $ git status
    On branch master
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        modified:   hello.rb

对 ``hello.rb`` 文件的修改已被暂存。这意味着 Git 现在已经知道这些修改，但还没有 **永久** 记录到仓库中。
下面的提交操作将包括暂存的修改。

如果你决定 **不** 提交修改，``status`` 命令提醒你可以使用 ``git reset`` 命令取消暂存修改。
