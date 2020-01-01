设置
=======

目标
^^^^^^^

* 设置 Git 以准备开始工作。


设置姓名和电邮
-----------------------------

如果你以前从未使用过 Git，那么你需要先做一些设置。
执行以下命令以便让 Git 知道你的姓名和电邮。如果你已经设置好了 Git，你可以跳到下一小节。

.. code-block:: shell

    $ git config --global user.name "Your Name"
    $ git config --global user.email "your_email@whatever.com"


设置行尾首选项
------------------------------

Unix/Mac 用户：

.. code-block:: shell

    $ git config --global core.autocrlf input
    $ git config --global core.safecrlf true

Windows 用户：

.. code-block:: shell

    $ git config --global core.autocrlf true
    $ git config --global core.safecrlf true


设置 Ruby
------------

本教程需要一个有用的 Ruby 解释器。如果你还没有安装，现在是时候设置了：

`https://www.ruby-lang.org/en/installation/ <https://www.ruby-lang.org/en/installation/>`_
