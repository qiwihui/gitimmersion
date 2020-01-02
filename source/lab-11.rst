11. 设置别名
===============

目标
^^^^^^^^^^^

* 学习如何设置别名及简写 Git 命令。


常用别名
-----------

``git status``、``git add``、``git commit``、``git checkout`` 是非常常用的命令，
因此对它们进行缩写十分有用。

添加以下内容到你的 ``$HOME`` 目录的 ``.gitconfig`` 文件中：

::

    [alias]
      co = checkout
      ci = commit
      st = status
      br = branch
      hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
      type = cat-file -t
      dump = cat-file -p

我们已经介绍了 ``commit`` 和 ``status`` 命令。并且在上一实验中也介绍了 ``log`` 命令。
接下来将介绍 ``checkout`` 命令。

使用这些在 ``.gitconfig`` 中定义的别名，你可以通过输入 ``git co`` 来表示 ``git checkout``。
同时，``git st`` 表示 ``git status``，而 ``git ci`` 表示 ``git commit``。
并且，最好的是 ``git hist`` 将使你避免很长的 ``log`` 命令。

去试试新命令吧。


在 ``.gitconfig`` 文件中定义 ``hist`` 别名
-----------------------------------------------

在本教程中的大多数部分中，我将继续输入完整的命令。唯一的例外是，当我需要看 ``git log`` 的输出时，我将使用上面定义的 ``hist`` 别名。
如果你想要和本教程保持一致，那么在继续阅读前，设置你的 ``.gitconfig`` 文件。


先写下来
-----------

我们已经添加了几个还没有介绍的命令别名。``git branch`` 命令很快会介绍，``git cat-file`` 命令对于浏览 Git 很有用。


Shell 别名（可选）
---------------------

**注意**：本小节是为那些运行 POSIX 类 Shell 的同学写的。Windows 用户及其他非 POSIX Shell 用户可以跳到下一个实验。

如果你的 Shell 支持别名或简写，那么你可以添加一些别名。下面是我使用的：

文件：``.profile``

::

    alias gs='git status '
    alias ga='git add '
    alias gb='git branch '
    alias gc='git commit'
    alias gd='git diff'
    alias go='git checkout '
    alias gk='gitk --all&'
    alias gx='gitx --all'

    alias got='git '
    alias get='git '

``git checkout`` 的缩写 go 尤其好，它允许我输入：

.. code-block:: shell

    $ go <branch>

来检出一个特定的分支。

另外，我也经常通过创建足够的别名来避免打错 Git 命令，比如 ``get`` 或者 ``got`` 表示 ``git``。
