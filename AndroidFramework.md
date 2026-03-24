#  AndroidFramework

## 04 android开机动画BootAnimation结束流程分析

![image-20260315145908134](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315145908134.png)

![image-20260315150728773](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315150728773.png)

![image-20260315150932917](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315150932917.png)

![image-20260315151456446](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315151456446.png)

![image-20260315152153184](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315152153184.png)

![image-20260315152332347](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315152332347.png)

![image-20260315152412095](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315152412095.png)

![image-20260315152719498](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315152719498.png)

android的方法就是画一个android的字体在屏幕上，movie，就是画我们放的动画

![image-20260315155807176](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315155807176.png)

在checkExit()上的内容就是播放动画，每次循环播放，会检测checkExit()这个方法

![image-20260315155957026](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315155957026.png)

上面是属性的值，因此，接下来只需要找到哪里设置了这个属性的值，当设置为1后，就推出动画了

![image-20260315160131945](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315160131945.png)

通过搜索可以看到，主要是在SurfaceFlinger和WindowManagerService里面都设置为1了

![image-20260315161021315](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161021315.png)

上面就是wms里关闭的方法，然后通过堆栈查看一下调用

![image-20260315161124232](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161124232.png)

可以看到WMS调用了SurfaceFilenger

![image-20260315161248145](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161248145.png)

于是我们查询谁调用了bootFinished这个方法

![image-20260315161531160](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161531160.png)

![image-20260315161625122](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161625122.png)

![image-20260315161831562](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315161831562.png)

从这里就彻底明了了，wms最后会调用SufaceFlinger的onTransact，然后调用BnSurfaceComposer的onTransact方法

在这个方法里面，执行停止开机动画的操作

![image-20260315162255405](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315162255405.png)



总体的内容

![image-20260315155536277](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315155536277.png)





## 05 android开机动画BootAnimation的opengl绘制源码分析

![image-20260315162358487](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260315162358487.png)

![image-20260316223309106](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260316223309106.png)

![image-20260316223557782](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260316223557782.png)

![image-20260316223608512](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260316223608512.png)

## 06 android开机动画BootAnimation实战使用opengl绘制实战

![image-20260316225302964](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260316225302964.png)

![image-20260316225320902](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260316225320902.png)





## 07 android开机动画BootAnimation源码分析zip包的运行原理

位置位于：

![image-20260324212553343](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324212553343.png)

下面是格式

![image-20260318222753080](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260318222753080.png)

![image-20260324210448342](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324210448342.png)



![image-20260324210539588](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324210539588.png)

![image-20260324211024736](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324211024736.png)

![image-20260324211154588](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324211154588.png)

![image-20260324211629704](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324211629704.png)

![image-20260324211857418](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324211857418.png)

![image-20260324212020952](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324212020952.png)

![image-20260324212139849](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324212139849.png)

![image-20260324212341011](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324212341011.png)



## 08 android开机动画BootAnimation的实战制作不一样的zip包动画

![image-20260324212750647](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324212750647.png)

![image-20260324230111894](C:\Users\hewei\AppData\Roaming\Typora\typora-user-images\image-20260324230111894.png)

desc的文件内容：

1080 360 60
c 1 0 part0 #ffee00 c c
c 0 0 part1 #ffee00 c c
c 1 0 part2 #ffee00 c c
c 1 1 part3 #ffee00 c c
c 1 0 part4 #ffee00 c c

将制作的bootanimation.zip集成到/system/media/目录下，这需要在Android.mk进行cp操作

```
$(shell cp $(LOCAL_PATH)/bootanimation.zip $(ANDROID_PRODUCT_OUT)/system/media/bootanimation.zip)
```

