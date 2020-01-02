18. 移除 ``oops`` 标签
=============================

目标
^^^^^^^^^^^

* 移除 oops 标签（清理）。


移除 ``oops`` 标签
----------------------

``oops`` 标签已经完成其目的了。让我们移除它，以使它引用的提交被作为垃圾回收。

.. code-block:: shell

    $ git tag -d oops
    $ git hist --all

输出：

.. code-block:: shell

    $ git tag -d oops
    Deleted tag 'oops' (was 8c2f695)
    $ git hist --all
    * 4d578d4 2019-11-01 | Added a comment (HEAD -> master, tag: v1) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value (tag: v1-beta) [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

在仓库中不再列出 ``oops`` 标签了。
