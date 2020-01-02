15. 撤销暂存的修改（在提交之前）
================================

目标
^^^^^^^^^^^
* 学习如何还原已经暂存的修改。


修改文件并暂存
-----------------------

修改 ``hello.rb`` 文件来包含一个错误的注释。

.. code-block:: ruby

    # This is an unwanted but staged comment
    name = ARGV.first || "World"

    puts "Hello, #{name}!"

然后暂存它。

.. code-block:: shell

    $ git add hello.rb


检查状态
-------------

检查你不想要的修改的状态。

.. code-block:: shell

    $ git status

输出：

.. code-block:: shell

    $ git status
    On branch master
    Changes to be committed:
    (use "git reset HEAD <file>..." to unstage)

        modified:   hello.rb

``status`` 输出显示修改已被暂存且准备提交。


重置暂存区
--------------

幸运的是 ``status`` 输出告诉我们取消暂存修改时需要做什么。

.. code-block:: shell

    $ git reset HEAD hello.rb

输出：

.. code-block:: shell

    $ git reset HEAD hello.rb
    Unstaged changes after reset:
    M	hello.rb

``reset`` 命令暂存区内容到 ``HEAD`` 中的内容。这将清除我们已经暂存的修改。

``reset`` 命令（默认）不会更改工作目录。所以在工作目录中仍然有不想要的注释。
我们可以使用之前实验中的 ``checkout`` 命令来从工作目录移除不想要的修改。


检出提交的版本
----------------

.. code-block:: shell

    $ git checkout hello.rb
    $ git status

输出：

.. code-block:: shell

    $ git status
    # On branch master
    nothing to commit (working directory clean)

现在我们的工作目录又变干净了。
