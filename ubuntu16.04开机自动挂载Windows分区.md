# ubuntu16.04开机自动挂载Windows分区
- 查看系统磁盘号  
```sudo fdisk -l```  
- 查看磁盘类型   
```sudo blkid```   
如图：图中的sda1,5，6,7是对应windows下的C,D,E,F盘，文件系统是ntfs，Linux分区一般为ext4，Windows分区一般为ntfs
![](https://github.com/YQ1724555319/ComputerSkill/blob/master/2016-08-25%2013-43-27%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png?raw=true)  
- 修改配置文件  
```sudo gedit /etc/fstab```  
配置文件包含以下几项：
<file system> <mount point>   <type>  <options>       <dump>  <pass>  
<file system> ：分区定位，可以给磁盘号，UUID或LABEL，例如：/dev/sda2，UUID=6E9ADAC29ADA85CD或LABEL=software  
<mount point> : 具体挂载点的位置，例如：/media/C  
<type> : 挂载磁盘类型，linux分区一般为ext4，windows分区一般为ntfs  
<options> : 挂载参数，一般为defaults  
<dump> : 磁盘备份，默认为0，不备份   
<pass> : 磁盘检查，默认为0，不检查  
配置图：  
![](https://github.com/YQ1724555319/ComputerSkill/blob/master/2016-08-25%2014-07-45%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png?raw=true)  
- 检查并挂载新添项：  
```sudo mount -a```  
mount -a会/etc/fstab中的项全部挂载，如果有错，则会提示错误，然后根据错误找出原因修改。

注意：千万不要挂载到当前用户的根目录，因为挂载的分区会覆盖当前分区内容  
参考：http://www.linuxidc.com/Linux/2013-02/79679.htm
