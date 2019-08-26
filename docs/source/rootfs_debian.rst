烧写 Debian 文件系统
*********************

需要的文件
==============
文件系统压缩包： rootfs_debian.tar.gz

烧录文件系统
==============
1）进入文件系统压缩包所在目录，解压缩文件系统
::

	tar -zxvf rootfs_debian.tar.gz

2）将 SD 卡的第二个分区（ext4 分区）重命名为“rootfs”
::

	sudo e2label /dev/sdb2 rootfs

3）烧写文件系统（将 rootfs_debian 文件夹的内容复制到 SD 卡的第二个分区）

	3.1）挂载 SD 卡的第二个分区
	::
	
		sudo mkdir /mnt/test
		sudo mount /dev/sdb2 /mnt/test
	
	3.2）复制文件系统到 SD 卡
	::
	
		sudo cp -rp rootfs_debian/* /mnt/test/
	
	3.3）复制完成后，进行同步操作
	::
	
		sync
	
	3.4）卸载 SD 卡
	::
	
		sudo umount /dev/sdb2
		sudo rm -r /mnt/test

