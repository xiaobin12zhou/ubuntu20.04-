# ubuntu20.04-卸载
1、右键此电脑-管理-磁盘管理，删除Ubuntu所在卷（Ubuntu EFI分区无法删除）

2、删除Ubuntu EFI分区

①Win + R 输入cmd打开终端，输入 diskpart 进入磁盘工具

②输入 list disk 查看磁盘，输入 select disk 1 （我的Ubuntu EFI分区在磁盘1，根据自己的情况选择）

③输入 list partition ，输入 select partition * （*为Ubuntu EFI分区号）

④输入delete partition override

3、删除Ubuntu启动引导项（重要，不删除重启会进入GRUB页面）

①Win + R 输入cmd打开终端，输入 diskpart 进入磁盘工具

②输入 list disk 查看磁盘，输入 select disk 0

③输入 list partition ，输入 select partition * （*为Windows EFI分区，一般为260M）

④输入 assign letter=J（分配盘符）

⑤管理员模式打开记事本 记事本选择文件-打开-选中磁盘J 打开 EFI 文件夹，删除Ubuntu文件夹 返回 Distpart 界面，输入 remove letter=J
此时Ubuntu完全从电脑中删除

#安装Ubtuntu双系统
重启y9000p F2  将系统U盘的启动顺序调制第一

分区设置 ：
1、efi系统分区

        大小：2G，

        新分区的类型：逻辑分区

        新分区的位置：空间起始位置

        用于：EFI系统分区

2、swap交换分区

        大小：16G，与电脑内存大小保持一致

        新分区的类型：主分区

        新分区的位置：空间起始位置

        用于：交换空间

3、 /

        大小：剩余空闲空间

        新分区的类型：主分区

        新分区的位置：空间起始位置

        用于：Ext4日志文件系统

        挂载点：/
        
 4. 在下面安装启动引导器的设备，选择刚刚分的efi的那个系统分区
 
 重启，快速拔掉u盘
 
 

