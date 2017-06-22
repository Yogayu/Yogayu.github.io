---
title: '基本Linux操作'
ref: physalis-salad
image: true
time: 5
category: Tech
tags: [Linux]
ingredients:
  -
    name: Linux
  -
    name: ls
  -
    name: pwd
  -
    name: cd
  -
    name: touch
  -
    name: cp
  -
    name: rm
  -
    name: man
    
--- 

一直都听说着Linux，却从未系统的去了解。

慢慢的才知道之前接触到的很多命令都是Linux中常见的，比如sed和awk。

1. `ls` 列出当然目录下所有文件，`ls -l`显示详细，搜写为`ll`。
2. `pwd` 列出当前所在目录。
3. `cd` 进入目录，`.`代表当前目录，`..`代表上一级，`/.`代表根目录。
4. 新建目录(文件夹)`mkdir`。
5. 新建文件 `touch` newFileName。
6. 复制文件 `cp` SOURCE DEST ， DEST为目录时表示将SOURCE文件复制到该目录。
7. 删除文件 'rm' fileName。
7. 查询`man` + 命令名，如需退出，请按`q` ，如需帮助请按`h`。

打开终端，试一试上面的命令吧。
比如做一个小练习，新建两个目录：一个目录A，一个目录B。并在目录A中新建文件newfile，再将newfile复制到目录B中，最后删除目录A中文件。


如果不知道具体如何使用，或者想学习新的命令，只需要能灵活的使用man就好了。一开始可以尝试`man man`。



grep 搜索
awk sed

