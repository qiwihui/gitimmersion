7. 暂存与提交
==============

Git 中单独的暂存步骤符合在你需要处理源代码控制之前不进行干预的理念哲学。
你可以继续对工作目录做出修改，当你想要与源码控制交互时，Git 允许你使用精确地记录你所做的小提交来记录你的修改。

例如，假设你编辑了三个文件（``a.rb``、``b.rb`` 及 ``c.rb``）。
现在你想提交所有修改，但你想要 ``a.rb`` 和 ``b.rb`` 中的修改作为单个的提交，
而 ``c.rb`` 的更改与前两个文件在逻辑上不相关，那么应该分开提交。

你可以执行下列命令：

.. code-block:: shell

    $ git add a.rb
    $ git add b.rb
    $ git commit -m "Changes for a and b"

    $ git add c.rb
    $ git commit -m "Unrelated change to c"

通过分开暂存和提交，你能够更加容易地调优每一个提交。
