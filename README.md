# pwnVM-ovf
> 基于[@leungbless](<https://github.com/leungbless>)的[pwnVM-ovf](<https://github.com/leungbless/pwnVM-ovf>)项目个人再修改版



## 虚拟机基本信息

OS：Ubuntu16.04 64位

虚拟机主机名：skye-virtual-machine

用户名：skye

用户密码&root密码：toor

需要修改主机名、用户名请看[这里](<https://blog.csdn.net/HuLuWa1997/article/details/89919758>)



## 食用方法

首先点击[这里](https://skye231-my.sharepoint.com/:u:/g/personal/skye_mrskye_cn/EYk1Uo5GspdEpXo4DY3lnEYBfE68dLvuRwF41tFn_E0QMA?e=dNUKl9)下载压缩包

解压后，将 ``Ubuntu.ovf``用VMware打开



## 更新日志

### 2019/12/20（自修版@[skyedai910](https://github.com/skyedai910)）

**0x0 安装vim**

```shell
sudo apt install vim
sudo nano pip.conf
```

 

**0x1 关闭ASLR**

```shell
sudo sh -c "echo 0 > /proc/sys/kernel/randomize_va_space"
```



**0x2 安装binwalk**

```shell
git clone https://github.com/devttys0/binwalk
cd binwalk
python setup.py install
```



**0x3 修改系统目录文件名为英文**



**0x4 原汉语输入法替换为系统拼音**



**0x5 安装sublime**

通过Ubuntu Store安装



### 2019/8/7 (原作者@[leungbless](https://github.com/leungbless))

**0x0 Ubandu和pip换源**

```shell
cd ~ && mkdir .pip
cd ~/.pip && touch pip.conf
sudo nano pip.conf
```

**写入下面的内容:**

```
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host=mirrors.aliyun.com
sudo apt-get update
sudo apt-get upgrade
```



**0x1.安装 git，gdb 和 gdb-multiarch，同时安装 binfmt 用来识别文件类型**

```shell
sudo apt-get update
sudo apt-get install git gdb gdb-multiarch
sudo apt-get install "binfmt\*"
```

 

**0x2.安装 gdb 的插件 pwndbg**

```shell
git clone https://github.com/pwndbg/pwndbg
cd pwndbg
./setup.sh
```

 

**0x3.安装pwntools**

```shell
apt-get install python2.7 python-pip python-dev git libssl-dev libffi-dev build-essential
pip install -U setuptools
pip install --upgrade pip
pip install --upgrade pwntools
```

 

**0x4.安装ssh**

```shell
sudo apt-get  install ssh
```

去掉22前面的#



**0x5.安装ROPgadget工具**

```shell
pip install ropgadget
```

 

**0x6.解决了下面的问题(方法来自网上)**

```shell
Traceback (most recent call last):
File "/usr/bin/pip", line 9, in <module>
from pip import main
sudo gedit /usr/bin/pip
```

然后将相应的内容修改为下面的内容：

```shell
from pip import __main__ //修改
if __name__ == '__main__':
sys.exit(__main__._main())//修改
```



**0x7.安装qemu**

```shell
sudo apt-get install qemu-user
```

 

**0x8. 安装LibcSearcher(用处: 用来泄露libc库中函数的偏移的库) **

```shell
git clone https://github.com/lieanu/LibcSearcher.git
cd LibcSearcher
python setup.py develop
```

 

**0x9.安装one_gadget(用处:用来寻找libc库中的execve('/bin/sh', NULL, NULL)可以一个gadget就可以getshell的好东西)**

```shell
sudo apt install ruby
gem install one_gadget
```

 

**0xA.安装peda**

```shell
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit
```

 

**0xB.安装libcdatabase(因为安装时间太长，以后再装)**

```shell
cd ~
git clone https://github.com/niklasb/libc-database.git
cd libc-database
./get
```



**0xC.安装32位程序依赖的环境**

```shell
dpkg --add-architecture i386
sudo apt-get -y install lib32z1 lib32ncurses5
```



## 参考链接

* [pwn enviroment](<https://www.jianshu.com/p/1476f38e3aa3>		)

* [pwn环境搭建](https://carlstar.club/2018/09/03/pwn环境搭建/#安装libcdatabase)

* [ctf wiki](<https://wiki.x10sec.org/>)
* <https://blog.csdn.net/lxlong89940101/article/details/94390393>

*  <https://github.com/giantbranch/pwn-env-init>