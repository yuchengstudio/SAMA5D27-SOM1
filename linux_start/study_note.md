
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

