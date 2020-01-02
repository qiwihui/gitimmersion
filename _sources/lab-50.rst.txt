50. 托管你的 Git 仓库
=======================

目标
^^^^^^^^^^^

* 学习如何设置 Git 服务器以共享仓库。

有很多方法可以通过网络共享 Git 仓库。以下是一种快速的方法。


启动 Git 服务器
------------------

.. code-block:: shell

    $ # (From the work directory)
    $ git daemon --verbose --export-all --base-path=.

现在，在另一个终端窗口中，切换到你的工作目录中。

.. code-block:: shell

    $ # (From the work directory)
    $ git clone git://localhost/hello.git network_hello
    $ cd network_hello
    $ ls

你可以看到 hello 项目的拷贝。


推送到 Git Daemon
----------------------

如果你想要推送到 Git daemon 仓库，添加 ``--enable=receive-pack`` 到 ``git daemon`` 命令。
小心，因为此服务器没有身份验证，任何人都能推送到你的仓库。
