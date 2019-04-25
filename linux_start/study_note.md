
# 1.环境搭建
<br/>请参考如下链接文档
https://github.com/yuchengstudio/SAMA5D27-SOM1/blob/master/reference/HowTo_AT91_Buildroot_Setup_Based_on_Ubuntu.pdf

# 2.GPIO实验
## 2.1请参考如下链接文档
<br/> https://github.com/yuchengstudio/SAMA5D27-SOM1/blob/master/reference/How_to_use_MCHP_Linux_on_GPIO.pdf

```
补充说明
文档中提及的“Copy gpio_test app to target” 可通过如下步骤进行
1.通过PC将gpio_test 复制到SD卡中，与boot.bin在同一个一个目录下。
2.拔下SD卡插入SOM-EK板的SD卡槽中，重启板子。
3.用户名为root,无密码，登录板子的linux系统。
4.可以使用pwd命令看当前目录有哪些文件。
5.通过cd /dev 命令定位到dev盘。
6.在当前盘符下敲入ls命令，可以看到 dev盘符下的所有的文件，其中mmcblk0p1就是我们需要的设备驱动。
7.使用“mount -t vfat /dev/mmcblk0p1 /mnt”命令将驱动挂载到系统。（可以在/mnt这个目录下看到mmcblk0p1这个文件）【这一步是最为关键地方】
8.通过mkdir user在根文件目录下创建了一个user文件夹【user这个名字可以是任意其他字符】
9.使用cp /mnt/gpio_test /user.(可以使用cd /user 定位到user文件夹，然后用ls命令看文件下的文件，应该有gpio_test这个文件了)
10.“chmod +x gpio_test”命令。
11.最后使用"./gpio_test"执行命令。
可以看到最终PB2口会有相应的波形输出。
```
https://github.com/yuchengstudio/SAMA5D27-SOM1/blob/master/reference/c7ff0148d641d549ef0e60814fe54c11.mp4

## 2.2逻辑示意图
![image](https://github.com/yuchengstudio/SAMA5D27-SOM1/blob/master/reference/linux_start_with_SAMA5D27-SOM1-EK1_001.jpg)

## 2.3.Q&A
<br/>Q1.为什么要使用“mount”挂载步骤。
<br/>A1:mount 是挂载的意思，就如Windows系统下插入U盘，会自动挂载识别系统创建访问盘符，Linux不会主动挂载你的设备，会注册设备，而挂载需要手动，所以mount就是挂载你的存储设备用以文件交流.
<br/>Q2.为什么要将可执行文件copy到用户文件目录下。
<br/>A2： Linux 讲究的就是用户权限，系统级别的目录和文件都是受限制的，user folder是有全权的处理权限，所以把要处理的文件copy到你的工作目录下，你可以自由使用.
<br/>Q3. 为什么要使用“chmod”指令
<br/>A3：chmod更改文件属性，包括是否可读，可写还有可执行，然后就是可以访问的用户组，什么人可以访问。这个可以在网上搜索chmod的命令说明，有很好的解释，这个命令可以扩展出很多Linux的权限知识，这也是Linux的文件访问的精髓.

