---
title: '一块移动硬盘，三种分区，用于Mac、Windows和TimeMachine'
image: true
onlineImg: http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023490080571.png
time: 3
category: Tech
tags: [Mac]
keywords: Mac分区, 磁盘工具
description: 使用磁盘工具给Mac分区
ingredients:
  -
    name: disk
--- 

## 1. 修改格式

插入移动硬盘，打开磁盘管理工具。
抹掉之前的格式，设定格式`Mac OS扩展（日志式）`，选择方案Guide分区图，如图所示：
	
![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023475991559.png)

确认抹掉：

![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023476174655.png)

**提示：**
如果抹掉之后你发现，选择左侧移动硬盘之后，分区按钮还是为灰。那么就代表你选择错了。
可以这样设置以显示：

![](http://7xle3b.com1.z0.glb.clouddn.com/2017-10-14-%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-10-14%20%E4%B8%8B%E5%8D%884.40.52.png)

选择移动硬盘根目录抹掉之后，就能看到分区选项了。

## 2. 分区

### 2.1 点击分区：
![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023472734705.png)
### 2.2 Time Machine 分区
因为我Mac是128G的，所以我分了300G作为Time Machine已经足够。
格式选择为`Mac OS扩展（日志式）`，名称命名为Time Machine。

![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023480505018.png)

### 2.2 Mac分区
点击未分区区域，之后设置同2.1，只是名称和大小设定不同。

### 2.3 Windows分区
点击最后剩余的未分区区域，设置格式为`ExFAT`即可。

![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023482815223.png)

至此，你已设定完成三种分区，可以在不同的设备上使用。

![](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-15023490080571.png)

## Time Machine
进入Time Machine 偏好设置，选择磁盘，选择之前分区为Time Machine的磁盘，耐心等待备份完成（通常需要很久，建议晚上备份）。

![屏幕快照 2017-08-10 下午3.12.48](http://7xle3b.com1.z0.glb.clouddn.com/2017-08-10-屏幕快照 2017-08-10 下午3.12.48.png)



感谢阅读，希望对你有帮助。

Thanks for reading!

