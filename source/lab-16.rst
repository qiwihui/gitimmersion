16. 撤销提交的修改
=======================

目标
^^^^^^^^^^^

* 学习如何还原已经提交到本地仓库的修改。


撤销提交
-----------

有时候你意识到已经提交修改不正确，想撤销该提交。有几种方式可以处理这种问题，我们在本实验中所用的方式总是安全的。

实际上我们将通过创建新的提交来撤销原来不想要修改的提交。


修改文件并提交
------------------

更改 ``hello.rb`` 文件成下列内容：

.. code-block:: ruby

    # This is an unwanted but committed change
    name = ARGV.first || "World"

    puts "Hello, #{name}!"

.. code-block:: shell

    $ git add hello.rb
    $ git commit -m "Oops, we didn't want this commit"


创建还原提交
--------------

要撤销已提交的更改，我们需要创建一个提交来移除由不想要的提交所引入的修改。

.. code-block:: shell

    $ git revert HEAD

这将带你进入编辑器中。你可以编辑默认的提交信息，或直接保存并关闭文件。你可以看到：

.. code-block:: shell

    $ git revert HEAD --no-edit
    [master 8c2f695] Revert "Oops, we didn't want this commit"
    1 file changed, 1 insertion(+), 1 deletion(-)

因为我们将撤销我们做的最后提交，所以我们可以使用 ``HEAD`` 作为还原的参数。
通过简单的指定哈希值，我们可以撤销早期历史中的任意提交。

**注意**：命令中的 ``--no-edit`` 可被忽略。在不打开编辑器生成输出时需要它。


检查日志
---------

检查日志来显示我们仓库中不想要提交和还原的提交。

.. code-block:: shell

    $ git hist

输出：

.. code-block:: shell

    $ git hist
    * 8c2f695 2019-11-01 | Revert "Oops, we didn't want this commit" (HEAD -> master) [Jim Weirich]
    * d5723b3 2019-11-01 | Oops, we didn't want this commit [Jim Weirich]
    * 4d578d4 2019-11-01 | Added a comment (tag: v1) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value (tag: v1-beta) [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

这种技术将处理任何提交（虽然你可能必须解决冲突）。在公开分享的远程仓库分支上使用更加安全。


下一步
----------

接下来，让我们看看从仓库历史中移除最近提交所用的技术。
