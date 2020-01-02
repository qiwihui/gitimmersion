17. 从分支移除提交
======================

目标
^^^^^^^^^^^

* 学习如何从分支移除最近的提交。

上一小节的 ``revert`` 是一个让我们撤销仓库中的任意提交的强大命令。
然而，原始提交和“撤销”提交在分支历史中都可见（使用 ``git log`` 命令）。

经常我们提交代码，然后很快意识到犯了错误。如果有一个“收回”命令能允许我们假装不正确的提交从未发生过该多好啊。
“收回”命令甚至还会阻止错误的提交在 ``git log`` 历史中的显示。这就像错误的提交从未发生过一样。


重置命令
-------------

我们已经介绍过 ``reset`` 命令，并用它来设置暂存区以便与特定的提交保持一致（我们在之前的实验中使用 ``HEAD`` 提交）。

当给定提交引用（如哈希值、分支或标签名）时，``reset`` 命令将：

1. 重写当前分支到指向的特定提交
2. 重置暂存区到匹配特定的提交（可选）
3. 重置工作目录到匹配特定的提交（可选）


检查历史
------------

让我们快速地查看我们的提交历史。

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

我们看到在该分支中的最后两个提交为 “Oops” 和 “Revert Oops”。让我们使用 ``reset`` 来移除它们。


首先，标记分支
---------------

但在我们移除提交前，让我们使用一个标签来标记最新的提交以便能够再次找到它。

.. code-block:: shell

    $ git tag oops


重置到 “Oops” 前
----------------

看看上面的日志历史，我们可以知道标记为“v1”的提交是错误提交之前的正确提交。
让我们重置分支到该位置。因为分支已经标记，所以我们可以在 ``reset`` 命令中使用标签名（ 如果它没有被标记，那么我们只能使用哈希值）。

.. code-block:: shell

    $ git reset --hard v1
    $ git hist

输出：

.. code-block:: shell

    $ git reset --hard v1
    HEAD is now at 4d578d4 Added a comment
    $ git hist
    * 4d578d4 2019-11-01 | Added a comment (HEAD -> master, tag: v1) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value (tag: v1-beta) [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

我们的 ``master`` 分支现在指到 ``v1`` 提交，并且 “Oops” 和 “Revert Oops” 提交已经不在分支中。
``--hard`` 参数表示应当更新工作目录以便与新的分支头保持一致。


什么也没丢
-------------

但错误的提交发生了什么？结果是提交仍然在仓库中。事实上，我们仍然能够引用它们。
记得在本实验开始我们使用标签 ``oops`` 标记了还原的提交。 让我们看看所有的提交。

.. code-block:: shell

    $ git hist --all

输出：

.. code-block:: shell

    $ git hist --all
    * 8c2f695 2019-11-01 | Revert "Oops, we didn't want this commit" (tag: oops) [Jim Weirich]
    * d5723b3 2019-11-01 | Oops, we didn't want this commit [Jim Weirich]
    * 4d578d4 2019-11-01 | Added a comment (HEAD -> master, tag: v1) [Jim Weirich]
    * dc1d42f 2019-11-01 | Added a default value (tag: v1-beta) [Jim Weirich]
    * 9a1c494 2019-11-01 | Using ARGV [Jim Weirich]
    * 063b40e 2019-11-01 | First Commit [Jim Weirich]

在这儿我们看到错误的提交并没有消失。它们仍然在仓库中。它们只是不再列到 master 分支中。
如果我们没有标记它们，它们依然在仓库中，但除了使用哈希值外没有别的方法引用它们。
未引用的提交保留在仓库中，一直到系统运行垃圾回收时。


重置的危险性
---------------

在本地分支上重置一般是安全的。任何“事故”通常都能通过重置到想要的提交来恢复。

然而，如果分支在共享的远程仓库上，那么重置可能使其他用户共享的分支混乱。
