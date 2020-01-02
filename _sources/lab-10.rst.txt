10. 历史
==============

目标
^^^^^^^^^^^

* 学习如何查看项目的历史。

获得已经做过的修改列表是 ``git log`` 命令的功能。

.. code-block:: shell

    $ git log

你可以看到：

.. code-block:: shell

    $ git log
    commit 4d578d47c426d4d94fcb3c645fe29c27138f3900
    Author: Jim Weirich <jim (at) edgecase.com>
    Date:   Fri Nov 1 10:47:28 2019 -0700

        Added a comment

    commit dc1d42fa6deb8a5c0abc8694b9f48604ce70d998
    Author: Jim Weirich <jim (at) edgecase.com>
    Date:   Fri Nov 1 10:47:28 2019 -0700

        Added a default value

    commit 9a1c494d033bf09a20ac0b10c32048e89ec5fe3b
    Author: Jim Weirich <jim (at) edgecase.com>
    Date:   Fri Nov 1 10:47:28 2019 -0700

        Using ARGV

    commit 063b40ead4efa2dce10ca893772c83483f0b546b
    Author: Jim Weirich <jim (at) edgecase.com>
    Date:   Fri Nov 1 10:47:28 2019 -0700

        First Commit

这份列表是迄今为止我们对仓库所作的所有四次提交。


单行历史
---------

你可以很好的控制处理 ``log`` 命令要精确显示的内容。我喜欢单行格式：

.. code-block:: shell

    $ git log --pretty=oneline

你可以看到：

.. code-block:: shell

    $ git log --pretty=oneline
    4d578d47c426d4d94fcb3c645fe29c27138f3900 Added a comment
    dc1d42fa6deb8a5c0abc8694b9f48604ce70d998 Added a default value
    9a1c494d033bf09a20ac0b10c32048e89ec5fe3b Using ARGV
    063b40ead4efa2dce10ca893772c83483f0b546b First Commit


控制显示哪个条目
-----------------

``log`` 命令有许多选项用来选择显示哪些条目。尝试下面的选项：

.. code-block:: shell

    $ git log --pretty=oneline --max-count=2
    $ git log --pretty=oneline --since='5 minutes ago'
    $ git log --pretty=oneline --until='5 minutes ago'
    $ git log --pretty=oneline --author=<your name>
    $ git log --pretty=oneline --all

参阅 ``man git-log`` 了解更多细节。


更加漂亮
----------

这是我用来复查上周所做更改的命令。如果我只想看自己所作的更改，那么我将添加 ``--author=jim``。

.. code-block:: shell

    $ git log --all --pretty=format:'%h %cd %s (%an)' --since='7 days ago'


终极日志格式
-------------

随着时间的推移，我发现在工作时最喜欢下列日志格式。

.. code-block:: shell

    $ git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short'

它看起来像这样：

.. code-block:: shell

    $ git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
    * 4d578d4 2019-11-01 | Added a comment (HEAD -> master) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

让我们看一下细节：

* ``--pretty="..."`` 定义输出的格式
* ``%h`` 是提交 hash 的缩写
* ``%d`` 是提交的装饰（如分支头或标签）
* ``%ad`` 是提交日期
* ``%s`` 是注释
* ``%an`` 是作者姓名
* ``--graph`` 使用 ASCII 图形布局显示提交树
* ``--date=short`` 使日期格式显示更好且更短


其它工具
------------

``gitx`` (Mac) 和 ``gitk`` (任意平台) 在浏览日志历史时十分有用。
