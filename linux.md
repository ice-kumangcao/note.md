[TOC]

##### vi 命令

```shell
vi file
a # 进入append模式
esc # 退出写模式
:wq # w-写,q-退出
```

##### scp:从服务器下载文件

```shell
# -r 为 递归发送
# 下载：服务器test -> 本地test
scp -r root@192.168.1.1:/home/ice/sql/test /home/ice/sql/test
# 上传：本地test -> 服务器test
scp -r /home/ice/sql/test root@192.168.1.1:/home/ice/sql/test
```

##### CentOS/Ubuntu 查看系统CPU信息

```shell
uname -r # 系统内核版本号
lsb_release -a # 查看操作系统版本
getconf LONG_BIT # CPU运行模式，即操作系统安装的是32位还是64位
lscpu # 查看CPU信息
dmidecode -s processor-version # 查看CPU版本
grep 'physical id' /proc/cpuinfo | sort -u |wc -l # 查看物理CPU个数
grep 'core id' /proc/cpuinfo | sort -u | wc -l # 查看CPU核心个数
grep 'processor' /proc/cpuinfo | sort -u | wc -l # 查看线程数
grep MemTotal /proc/meminfo # 查看系统内存大小
# 查看内存个数及大小
sudo dmidecode -t memory | grep -A 16 'Memory Device$' | grep "Size:"
sudo fdisk -l | grep 'Disk /dev/sd' # Ubuntu 查看硬盘容量
sudo hdparm -i /dev/sda | grep "Model" # ubuntu 查看硬盘型号
df -lh # centos 查看硬盘容量
# 可以区分是否进行了磁盘阵列， 如果有的话会有 Vendor 和 Product 
smartctl --all /dev/sda # centos 查看硬盘型号
stat /lost+found/ #查看 lost+found 文件的创建时间推测系统安装大致时间
```

##### Ubuntu 命令行下打开图形化文件夹

```shell
nautilus /home # 打开 /home 图形化文件夹
```

##### Ubuntu 命令行快速打开各类型文件

```shell
xdg-open http://baidu.com
```

##### Ubuntu下查看显卡驱动是否成功安装

```shell
sudo apt-get install mesa-utils
glxinfo | grep rendering # 结果为‘yes’，说明显卡成功安装
```

##### Ubuntu 亮度调节

```shell
cd /sys/class/backlight/acpi_video0
cat max_brightness # 最大亮度
cat brightness # 当前屏幕亮度
```
##### Ubuntu 软件

+ freerdp `连接远程window桌面的工具，支持网络身份认证`

  ```shell
  sudo apt-get install freerdp 会提供几个版本的freerdp，选择其中一个版本下载。
  # freerdp2命令使用规则与普通的不同，具体看帮助文档
  sudo apt-get install freerdp2-x11 
  ```
