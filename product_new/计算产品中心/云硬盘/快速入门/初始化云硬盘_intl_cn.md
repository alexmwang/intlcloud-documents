## 操作场景
本文档将以初始化新挂载至云服务器的空云硬盘，创建文件系统并向其中写入一个名为`qcloud.txt`的文件为例，帮助您了解如何简单地使用云硬盘。关于初始化云硬盘的更多信息请参考 [初始化场景介绍](https://intl.cloud.tencent.com/document/product/362/31596)。

## 前提条件
已成功 [挂载云硬盘](https://intl.cloud.tencent.com/document/product/362/31645)，即云硬盘状态为【已挂载】。

>本文使用 Windows、Linux 云服务器操作系统分别为：
>- Windows Server 2008
>- CentOS 7.5

## 格式化、创建文件系统并写入文件（Windows）
1. 以管理员身份 [登录 Windows 云服务器](https://intl.cloud.tencent.com/document/product/213/5435)。
2. 选择【服务器管理】>【存储】>【磁盘管理】，进入磁盘管理界面。
3. 右键单击目标空磁盘，选择【联机】。
 当磁盘状态变为【没有初始化】时，表示联机完成。
4. （可选）右键单击已完成联机的磁盘，选择【初始化磁盘】，选择【MBR（主启动记录）】，单击【确定】。
 >?MBR（Main Boot Record）格式分区支持的磁盘最大容量为2TB，GPT（GUID Partition Table）分区表最大支持的磁盘容量为18EB。如果您需要使用大于2TB的磁盘容量，请采用 GPT 分区方式。
若磁盘投入使用后，再切换磁盘分区形式，则磁盘上的原有数据将会被清除，因此请在磁盘初始化时谨慎选择磁盘分区形式。
5. 右键单击目标磁盘，选择【新建简单卷】。
6. 输入简单卷大小，单击【下一步】。
7. 选择文件系统，格式化分区，单击【下一步】。
8. 单击【完成】。
 目标磁盘显示正在格式化，需要等待片刻让系统完成初始化操作。当卷状态为【状态良好】时，表示初始化磁盘成功。初始化成功后，在【计算机】界面可以看到新分区的数据盘。
9. 进入新分区的数据盘，新建文件 `qcloud.txt`，输入您需要的内容，选择【文件】>【保存】。

## 格式化、创建文件系统并写入文件（Linux）
>- 本文以使用 EXT4 文件系统为例。
>- Linux 云服务器重启或开机后，不会自动挂载数据盘，详情请参见 [格式化并挂载数据盘](https://intl.cloud.tencent.com/document/product/213/17487)。

1. 以 root 用户 [登录 Linux 云服务器](https://intl.cloud.tencent.com/document/product/213/5436)。
2. 执行以下命令，查看连接到实例的磁盘名称。
 ```
fdisk -l
 ```
本文以 `/dev/vdb`为例。
3. 执行以下命令，格式化该磁盘。
```
mkfs.ext4 /dev/vdb
```
4. 执行以下命令，将该磁盘挂载到 `/data` 挂载点。
```
mount /dev/vdb /data
```
5. 依次执行以下命令，进入该磁盘，并新建文件 `qcloud.txt`。
```
cd /data
vi qcloud.txt
```
6. 在编辑状态下可输入相关内容，例如：“This is my first test”。按 ESC 退出编辑状态，输入 `:wq` 保存并退出文件。
7. 执行 `ls` 命令，可查看到 `qcloud.txt` 文件已写入盘中。
