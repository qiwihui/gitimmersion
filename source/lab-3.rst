3. 创建项目
============

目标
^^^^^^^^^^^^

* 学习如何从零开始创建 Git 仓库。


创建 ``Hello, World`` 程序
--------------------------------

在空的工作目录中创建一个名为 ``hello`` 的空目录，然后创建一个名为 ``hello.rb`` 的文件，包含如下内容：

.. code-block:: shell

    $ mkdir hello
    $ cd hello

文件：hello.rb

.. code-block:: ruby

    puts "Hello, World"


创建仓库
------------

你现在有一个包含单个文件的目录。要从该目录创建 Git 仓库，执行 ``git init`` 命令。

.. code-block:: shell

    $ git init

输出：

.. code-block:: shell

    $ git init
    Initialized empty Git repository in /Users/jerrynummi/Projects/git-immersion-edgecase/auto/hello/.git/


添加程序到仓库
---------------

现在让我们添加 ``Hello, World`` 程序到仓库。

.. code-block:: shell

    $ git add hello.rb
    $ git commit -m "First Commit"

你可以看到：

输出：

.. code-block:: shell

    $ git add hello.rb
    $ git commit -m "First Commit"
    [master (root-commit) 063b40e] First Commit
    1 file changed, 1 insertion(+)
    create mode 100644 hello.rb
