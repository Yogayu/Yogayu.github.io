---
title: '将一个分支中特定commit合并另外一个分支上'
ref: physalis-marmelade
image: true
onlineImg: https://git-scm.com/images/reset/reset-soft.png
time: 2
category: Tech
tags: [git]
ingredients:
  -
    name: git log
  -
    name: git checkout
  -
    name: git cherry-pick  
---
有时候团队切了新分支，但是你忘记了，所以你需要将自己的commit合并到新分支上去。此时你的commit却夹杂在其他人的commit之中，所以你可以使用cherry-pick选择commit进行合并。

1. 查看你要合并的commit id
        
        git log 
        
        commit 4d2b29d6e7f1208e7f672998a511c81ac011e22f

2. 切换到将要添加commit的分支,比如你要加到maser分支上
    
        git co master

3. 合并
        
        git cherry-pick 4d2b29d6e7f1208e7f672998a511c81ac011e22f
   
