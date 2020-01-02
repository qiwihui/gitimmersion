13. 给版本打标签
====================

目标
^^^^^^^^^^^

* 学习如何使用名称给提交打标签以供将来引用。

让我们称 ``hello`` 程序的当前版本为 version 1 (``v1``)。


标记 version 1
-----------------

.. code-block:: shell

    $ git tag v1

现在你可以引用程序的当前版本为 ``v1``。


标记先前的版本
-----------------

让我们标记当前版本之前的版本为 ``v1-beta``。首先我们需要检出先前的版本。除了使用哈希值，我们可以使用 ``^`` 来表示“v1 的父提交”。

.. admonition:: **注意**

    如果使用 ``v1^`` 表示法遇到问题，你还可以试试 ``v1~1``， 这将引用相同的版本。该表示法意为“v1 的第一个祖先提交”。

.. code-block:: shell

    $ git checkout v1^
    $ cat hello.rb

输出：

.. code-block:: shell

    $ git checkout v1^
    Note: checking out 'v1^'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by performing another checkout.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -b with the checkout command again. Example:

    git checkout -b <new-branch-name>

    HEAD is now at dc1d42f... Added a default value
    $ cat hello.rb
    name = ARGV.first || "World"

    puts "Hello, #{name}!"


看，这是我们添加注释 *之前* 的默认值版本。让我们把它变成 ``v1-beta``。

.. code-block:: shell

    $ git tag v1-beta


按标签名检出
-----------------

现在试试在两个标签版本之间切换。

.. code-block:: shell

    $ git checkout v1
    $ git checkout v1-beta

输出：

.. code-block:: shell

    $ git checkout v1
    Previous HEAD position was dc1d42f... Added a default value
    HEAD is now at 4d578d4... Added a comment
    $ git checkout v1-beta
    Previous HEAD position was 4d578d4... Added a comment
    HEAD is now at dc1d42f... Added a default value


使用 ``tag`` 命令查看标签
----------------------------

你可以使用 ``git tag`` 命令来查看可用的标签。

.. code-block:: shell

    $ git tag

输出：

.. code-block:: shell

    $ git tag
    v1
    v1-beta


查看日志中的标签
-------------------

你也可以查看日志中的标签。

.. code-block:: shell

    $ git hist master --all

输出：

.. code-block:: shell

    $ git hist master --all
    * 4d578d4 2019-11-01 | Added a comment (tag: v1, master) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value (HEAD, tag: v1-beta) [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

你可以在日志输出中看到与分支名称（``master``）一起列出了两个标签（``v1`` 和 ``v1-beta``）。
``HEAD`` 显示的是你当前检出的提交 （此刻是 ``v1-beta``）。
