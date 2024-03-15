---
title: Linux基础
date: 2023-04-13 18:13:29
categories: 大数据
comments: true
cover: 'https://s2.loli.net/2024/03/15/UV7bh68NGP4ATQo.png'
tags:
  - vim
  - shell
  - linux
abbrlink: linuxba
---

# 所需软件的安装和配置

## 1.VMware和远程连接软件（FinalShell、Xshell等）的安装

VMware软件安装简单，激活码查找也方便，FinalShell若不使用专业版内容也是直接安装即可。

下面是FinalShell3.9.5.7及之前版本的高级/专业版激活码获取方式。

打开FinalShell后点击激活，选择离线激活，随便输入账号密码，复制机器码，粘贴即可获取

```php
<?php
    if(!empty($_POST['k'])){
        if($_POST['s'] == 1){
            $a = '激活码为：'.strtolower(substr(md5('2356'.$_POST['k'].'13593'),8,16));
        }
        if($_POST['s'] == 0){
            $a = '激活码为：'.strtolower(substr(md5('61305'.$_POST['k'].'8552'),8,16));
        }
    }
?>
```

substr截取md5的一部分，从第八位开始往后面的16个字符，strtolower()将字符串全部转为小写

```html
<form action="#" method="post">
        <input type="text" name="k" id="k">
        <input type="radio" name="s" id="s" value="1">专业版
        <input type="radio" name="s" id="s" value="0">高级版
        <input type="submit" value="提交">
    </form>
```

php文件内容应为

```php+HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FinalShell激活码计算</title>
</head>

<body>

<form action="#" method="post">
    <input type="text" name="k" id="k">
    <input type="radio" name="s" id="s1" value="1">专业版
    <input type="radio" name="s" id="s2" value="0">高级版
    <input type="submit" value="提交">
</form>

<?php
    $a = '';
    if(!empty($_POST['k'])){
        if($_POST['s'] == 1){
            $a = '激活码为：'.strtolower(substr(md5('2356'.$_POST['k'].'13593'),8,16));
        }
        if($_POST['s'] == 0){
            $a = '激活码为：'.strtolower(substr(md5('61305'.$_POST['k'].'8552'),8,16));
        }
    }
    echo $a;
?>

</body>
</html>
```



Java代码 [附在线运行网站](https://www.json.cn/runcode/run_java/)

```java
import java.io.IOException;
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.util.Scanner;

class Main{
    public static void main(String[] args) throws NoSuchAlgorithmException, IOException {
        System.out.print("请输入FinalShell的离线机器码：");
        @SuppressWarnings("resource")
        //Scanner reader = new Scanner(System.in);
        String machineCode = "aa@6a6c73491cbe6c6e"; // 在此处放置机器码
        generateKey(machineCode);
    }

    public static void generateKey(String hardwareId) throws NoSuchAlgorithmException {
        String proKey = transform(61305 + hardwareId + 8552); //高级版
        String pfKey = transform(2356 + hardwareId + 13593); //专业版
        System.out.println("请将此行复制到离线激活中：" + pfKey);
    }

    public static String transform(String str) throws NoSuchAlgorithmException {

        @SuppressWarnings("unused")
        String md5 = hashMD5(str);

        return hashMD5(str).substring(8, 24);
    }

    public static String hashMD5(String str) throws NoSuchAlgorithmException {
        MessageDigest digest = MessageDigest.getInstance("MD5");
        byte[] hashed = digest.digest(str.getBytes());
        StringBuilder sb = new StringBuilder();
        for (byte b : hashed) {
            int len = b & 0xFF;
            if (len < 16) {
                sb.append("0");
            }
            sb.append(Integer.toHexString(len));
        }
        return sb.toString();
    }
}

```



### 虚拟网络配置

安装好本地虚拟机后，需要对网络进行配置，~~*使用vps可跳过这个步骤*~~ 课程中使用的是CentOS7的系统，不同版本的具体配置可能不尽相同。在虚拟机设置中，将虚拟机的网络模式设置为NAT模式。



在终端界面输入`ifconfig` 查看ens33的ip地址，ip地址为192.168.88.100，然后打开虚拟网络编辑器，选中VMnet8更改配置

![linux01.png](https://s2.loli.net/2024/03/15/lPkyoLge326WTBd.png)

![linux02.png](https://s2.loli.net/2024/03/15/LFHSh8DZvm3cKPo.png)

子网IP更改为192.168.88.0，点击将主机虚拟适配器连接到此网络，点击NAT设置，将网关IP改为192.168.88.2，点击确定，保存。



修改配置文件，IP地址192.168.88.100和网关地址192.168.88.2、DNS192.168.88.2

```
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

![linux03.png](https://s2.loli.net/2024/03/15/atjAwCNBLsIOlWu.png)

然后修改网络适配器

![linux04.png](https://s2.loli.net/2024/03/15/oAz421RPdbOt86q.png)

删除`/etc/sysconfig/network-scripts/` 下的以ifcfg开头除ifcfg-ens33和ifcfg-lo以外的文件（ifcfg-配置_1， ifcfg-ens33.bak），重启网络`systemctl restart network` 此时虚拟机应能正常访问网络。

## 2.Linux命令

Linux是树状存储结构，在一个根节点下存放了系统的不同文件夹，Windows是森林结构

/bin：这个目录存放着最经常使用的命令,ls、cp、rm、chmod 等常用命令都在此目录

/boot 系统启动目录，保存与系统启动相关的文件，如内核文件和启动引导程序；

/dev 设备文件保存位置；

/etc：存放在配置文件

/home：用户的主目录 

/lib：存放程序所需的动态库和静态库文件；

/root ：超级用户 home目录

### 2.1.Linux基础命令

#### 2.1.1.linux命令的构成

linux指令=命令（做什么） +选项（怎么做） +参数（对谁做）

​			-command ：命令名 ：使用英文单词的缩写或者英文单词

​			-options：选项     ，可以对命令进行控制   但是 也可以省略

​			-parameter：给命令传参数， 可以是一个 ，也可以是多个或者零个

**在使用命令时，可以使用man 命令名查看使用说明**

./ ：代表当前目录

../：上一级目录

使用这两种方式可实现绝对路径和相对路径访问文件

**ctrl+r：历史记录中所搜命令（输入命令中的任意一个字符）；**

**ctrl+c：终止当前的命令**

#### 2.1.2 ls命令

ls命令：展示linux系统中指定位置的目录信息   -F 查看目录中的文件

```
-a ：查看所有文件，包括隐藏的文件，Linux下隐藏文件 隐藏目录 名称都是以.开头，图形界面下可以使用ctrl+h切换是否显示隐藏文件

-l ：展示文件的详细信息，包括权限、归属、文件大小、创建修改时间、文件名称，linux内置了ll命令作为ls -l的别名
ls -ld：显示目录和链接信息；

-h ：人性化显示文件大小，赋予最恰当的单位 但是需要和 l一起使用  

ls -R：递归显示子目录结构；

ls [0-9] ：显示包含数字的文件名和目录名
```



#### 2.1.3 cd命令

```
cd ../   返回上一级目录
cd ../.. 返回上两级目录

cd - 返回上一次操作的工作目录

cd / 进入根目录

cd ~ 返回家目录中   ~ 可以省略
```

#### 2.1.4 pwd命令

pwd命令：获取当前所在工作目录的绝对路径

#### 2.1.5 mkdir命令

mkdir命令用来创建空目录的命令，我们可以在指定的路径下厨房间一个空目录

```
mkdir 文件夹名字  ：在当前目录下创建一个文件夹

mkdir -p 文件路径   指定路径下创建一个空目录，同时创建其父目录
```

#### 2.1.6 touch命令

touch命令可以创建一个新的文件，文件的拓展名随意，甚至可以是一个不存在的拓展名，当文件存在的时候，修改文件的创建时间

touch 可以一次性创建多个文件，但是这个文件路径**必须正确**

```
touch -t 0712250000 file1 修改一个文件或目录的时间戳 - (YYMMDDhhmm)
touch * ：将当前下的文件时间修改为系统的当前时间

touch –d 20040210 test：将test文件的日期改为20040210

touch abc　：若abc文件存在，则修改为系统的当前时间；若不存在，则生成一个为当前时间的空文件
```

#### 2.1.7 rm命令

rm 是删除文件的指令，可以删除文件 ，也可以删除文件夹

```
-r  递归删除，删除文件夹的时候使用

-f  强制删除 ，不进行询问

rm  可以删除任意文件，路径可以是相对/绝对的
```

#### 2.1.8 mv命令

mv是一个移动文件的指令，将文件从一个位置移动到另一个位置，在移动的过程中可以修改文件或者目录的**名称**，格式：mv 源文件路径（相对/绝对）   目标路径。移动文件或者目录时，目标路径必须存在，改名只需输入相同的路径不同的文件名即可，可同时改名并移动文件

```
mv dir1 new_dir 重命名/移动 一个目录
```



#### 2.1.9 cp命令

cp命令就是可以复制文件或者目录的命令，在复制的过程中，源文件不会被删除，复制完成后，文件可以修改名称，格式：cp 源文件路径  目标路径

```
cp -r #复制目录时需要- r

cp file1 file2 复制一个文件
cp dir/* . 复制一个目录下的所有文件到当前工作目录
cp -a /tmp/dir1 . 复制一个目录到当前工作目录
cp -a dir1 dir2 复制一个目录
```

mv和cp的使用方式基本一致，只有两个地方不一样：

1：mv移动目录时不需要使用-r，cp需要使用-r

2：cp不会删除源文件，而mv源文件会消失

#### 2.1.10 echo命令

功能：输出内容

语法：`echo 参数`

- 参数：被输出的内容
- 被两个反引号包围的内容，会作为命令执行，echo \`pwd\`，会输出当前工作目录

#### 2.1.11 重定向符

功能：将符号左边的结果，输出到右边指定的文件中去

- `>`，表示覆盖输出
- `>>`，表示追加输出

### 2.2 进阶命令

#### 2.2.1 cat命令

用于查看linux中**小型的**文本文件，cat 文件名

因为他会一次行将所有的文件内容加载终端中，终端显示的数据有限，大的文件会显示不全，且消耗内存

使用生产场景：   大数据框架的运行日志、大数据计算的运行日志

```
cat file1 从第一个字节开始正向查看文件的内容
tac file1 从最后一行开始反向查看一个文件的内容
```



#### 2.2.2 more命令

用于查看linux中中型的文本文件

使用more进行文件的查看可以按页，手动翻页或者回滚，更灵活。但是统一也消耗内存

```
 -回车   向下一行
 -空格    向下一页
 b   向上一页
 q   退出查看
 
more file1 查看一个长文件的内容
less file1 类似于 'more' 命令，但是它允许在文件中和正向操作一样的反向操作
```

cat 和 more 都可用来查看文件内容。不同点在于：cat 指令查看完毕后会自动返回到正常模式而 more 指令则需要用户手动退出查看模式。cat 命令用于显示整个文件的内容，单独使用没有翻页功能。而 more 命令则可以分页显示文件内容，可以向前或向后翻页，可**与cat配合使用**。

#### 2.2.3 head，tail命令

head功能：查看文件头部内容

语法：`head [-n] 参数`

- 参数：被查看的文件
- 选项：-n，查看的行数

tail默认查看该文件的最新10行（如果这个文件发生变动，有新的内容添加到文件的尾部，tail命令会把新添加的内容展示出来，**实时查看** ）

```
tail -f 文件名
head -2 file1 查看一个文件的前两行
tail -2 file1 查看一个文件的最后两行
```

#### 2.2.4 ps命令

查看当前活跃的进程

ps -ef 作用：查看当前所有的进程，查看PID和了解进程cpu资源占比情况

```
UID：表示是哪个一个用户执行的

PPID：进行的父进行标识号

C：cpu使用资源的百分比

Stime：进程开始执行的时间
```

#### 2.2.5 kill命令

用于结束linux中的软件或者服务，格式： kill -9 进程编号  

kill -9 可以快速的杀死进程，但是不安全，因为我们的服务在运行的过程中，可能会需要保存或者某执行完某一个任务在关闭。所以不轻易使用，一般都是用于杀死闲置进程或者不响应的进行。

#### 2.2.6 ifconfig命令

作用：用于查看服务器网络信息

#### 2.2.7 free命令

作用：查看内存的使用情况

```
total：表示总计的物理内存大小

used：表示已经使用的多了

free：表示还可以用多少

shared：表示多个进行共享的内存总额

buff：表示缓存的大小

free -k：以kb为单位来显示内存（默认就是k）

free -m：以m为单位来显示内存信息

free -g ：以m为单位来显示内存信息

free -h ：以用户适合的方式去显示内存

free -t：显示linux全部的内存（total）

free -s：表示每个N秒打印一次内存信息，直到使用crtl+c结束


free -hs  5：生产使用场景：提交大数据计算任务后，动态的查看内存变化情况
```

#### 2.2.8 df命令

作用：查看磁盘的使用情况

```
df -h：以用户方便的单位进行显示
df-Th：显示文件系统的类型
```

#### 2.2.9 clear命令 

清除终端窗口的信息=crlt+l

#### 2.2.10 关机&重启命令

```
1：reboot命令

重启计算机，reboot属于安全重启，不属于强制重启，可以放心的使用

2：shutdown命令

shutdown命令主要用于关机操作，关闭过程中，可以指定关机时间

shutdown -h now 立即关机

shutdown -h 1 一分钟后关机
shutdown -h hours:minutes & 按预定时间关闭系统

shutdown -c 取消按预定时间关闭系统

shutdown -r now 重启

init 0    关闭系统
telinit 0 关闭系统
logout    注销
```

#### 2.2.11 which命令

查看脚本或者终端命令文件所在位置

一般情况下可以使用which命令找到**终端指令**的安装目录

#### 2.2.12 grep命令

grep就是根据一定的规则做全文检索，在文件中查询到满足规则的文本内容

grep是在文件中查询文本，指定的文件中查找特定的字符组合

用法: grep [选项]... 

生产使用场景：从日志中找到错误信息，方便我们分析日志

​	grep ERROR 文件名

​	警告：grep INFO 文件名

##### pgrep 

用于列举进程ID，下面两条命令是等效的

```
pgrep -u hchen2244122444
ps -ef | egrep '^hchen' | awk '{print $2}'
```



#### 2.2.13 hostname命令

查看主机名

#### 2.2.14 | 无名管道命令

管道指令，是连接两个命令的指令，前一个命令的输出，就是下一个命令的输入

```
查找文件：ls -l | grep 创建时间 |grep 文件名

查找进程：ps -ef | grep 进程名 | grep 进程归属
```

#### 2.2.14.1 mkfifo 命名管道

用法：mkfifo [选项] 文件名

命名管道是一种特殊的文件类型，可以用于实现进程间通信（IPC，Inter-Process Communication），允许不同进程之间通过读写同一个文件来传递数据

使用 `mkfifo` 命令创建的命名管道可以像普通文件一样被读取和写入。一个进程可以将数据写入命名管道，而另一个进程可以从同一个命名管道中读取这些数据，从而实现了进程间的通信。命名管道通常用于在不同的进程之间传递数据，例如在Shell脚本中用于管道操作、在不同的程序之间传递数据等

命名管道在使用时需要注意同步和阻塞的问题，因为命名管道是基于文件系统的，读写操作可能会阻塞，导致进程在没有数据可读或可写时被阻塞。此外，命名管道在使用完毕后需要手动删除，可以使用 `rm` 命令删除对应的文件

```
# mkfifo /tmp/aapipe           创建命名管道
# ls -l /tmp
输出 prw-rw-r-- 1 aa  aa  0 05-10 18:58 aapipe
# ls -al > /tmp/aapipe         在一个shell中运行此命令，命令不会返回，除非有人从这个有名管道中把信息读走
# head /tmp/aapipe             在另一命令窗口读取管道中的信息，同时上一命令会返回
输出 drwx------ 8 aa aa    4096 05-10 18:27 .
    drwxr-xr-x 7 root  root     4096 03-05 00:06 ..
    drwxr-xr-x 3 aa aa    4096 03-01 18:13 backup
    -rw------- 1 aa aa     721 05-05 22:12 .bash_history
    -rw-r--r-- 1 aa aa      24 02-28 22:20 .bash_logout
    -rw-r--r-- 1 aa aa     176 02-28 22:20 .bash_profile
    -rw-r--r-- 1 aa aa     124 02-28 22:20 .bashrc
    -rw-r--r-- 1 root  root    14002 03-07 00:29 index.htm
    -rw-r--r-- 1 aa aa   31465 03-01 23:48 index.php
```



#### 2.2.15 tar命令

tar命令是进行打包，解包，压缩和解压的命令

打包：将多个文件归档为一个文件，文件大小不会减少	

解包（拆包）：将一个包文件分拆多个实体的文件

压缩：将文件按照一定的算法减少体积，但是文件的内容和信息不会发送改变

解压缩：将一个压缩文件还原到正常的状态

```
参数：
c：打包选项
x：解包选项
z：压缩或者解压缩选项
v：展示过程
f：指定文件名
一般情况tar -cxvf压缩 tar -zxvf解压
```

**其它压缩指令**

```
bunzip2 file1.bz2           解压一个叫做 'file1.bz2'的文件
bzip2 file1                 压缩一个叫做 'file1' 的文件
gunzip file1.gz             解压一个叫做 'file1.gz'的文件
gzip file1                  压缩一个叫做 'file1'的文件
gzip -9 file1               最大程度压缩
rar a file1.rar test_file          创建一个叫做 'file1.rar' 的包
rar a file1.rar file1 file2 dir1   同时压缩 'file1', 'file2' 以及目录 'dir1'
rar x file1.rar     压缩rar包
unrar x file1.rar   解压rar包
tar -cvf archive.tar file1     创建一个非压缩的 tarball
tar -tf archive.tar            显示一个包中的内容
tar -xvf archive.tar           释放一个包
tar -xvf archive.tar -C /tmp   将压缩包释放到 /tmp目录下
tar -cvfj archive.tar.bz2 dir1 创建一个bzip2格式的压缩包
tar -xvfj archive.tar.bz2      解压一个bzip2格式的压缩包
tar -cvfz archive.tar.gz dir1  创建一个gzip格式的压缩包
tar -xvfz archive.tar.gz       解压一个gzip格式的压缩包
zip file1.zip file1            创建一个zip格式的压缩包
zip -r file1.zip file1 file2 dir1   将几个文件和目录同时压缩成一个zip格式的压缩包
unzip file1.zip                     解压一个zip格式压缩包
```



#### 2.2.16 useradd，groupadd命令

useradd 可以添加一个linux用户，/home目录会创建一个该用户的家目录 

```
groupmod -n new_group_name old_group_name                              重命名一个用户组
useradd -c "Name Surname " -g admin -d /home/user1 -s /bin/bash user1  创建一个属于 "admin" 用户组的用户
```



#### 2.2.17 userdel，groupdel命令

删除用户同时会删除用户的家目录

```
userdel -r user1              删除一个用户 ( '-r' 排除主目录)
usermod -c "User FTP" -g system -d /ftp/user1 -s /bin/nologin user1   修改用户属性
newgrp group_name             登陆进一个新的群组以改变新创建文件的预设群组
```



#### 2.2.18 passwd命令

格式：passwd 用户名 更改指定用户的密码，不可使用数字小键盘

```
passwd user1               修改一个用户的密码 (只允许root执行)
chage -E 2023-04-10 user1  设置用户密码的失效期限

pwck                       检查 '/etc/passwd' 的文件格式和语法修正以及存在的用户
grpck                      检查 '/etc/passwd' 的文件格式和语法修正以及存在的群组
```



#### 2.2.19 chmod，chown命令

inux的文件**权限**

|           |         | 权值 |
| --------- | ------- | ---- |
| 读：r     | read    | 4    |
| 写：w     | write   | 2    |
| 执行： x  | excuter | 1    |
| 无权限：- |         | 0    |

linux文件**归属**

属主：文件拥有者，一般是创建者 u   –user

属组：文件拥有者所在的用户组   g    -group

其他用户： 除了 属主和数组的其他用户 o -other

ls -l 可以查看文件的详细信息，包含文件权限其中d ：代表目录，-：普通文件

```
chmod 777 文件名                #表示给当前用户，用户所在组，其他用户都给予全部权限
chmod u+x,g+x,o+x 文件名        #增加权限，-则为删除权限
chmod u=rwx, g=wx, o=r 文件名   #同时编辑多个权限

chmod go-rwx directory1        删除群组(g)与其他人(o)对目录的读写执行权限

chown [-R] [用户][:][用户组] 文件或文件夹
chown -R user1 directory1      改变一个目录的所有人属性并同时改变改目录下所有文件的属性
chgrp group1 file1             改变文件的群组

chmod u+s /bin/file1       设置一个二进制文件的 SUID 位 - 运行该文件的用户也被赋予和所有者同样的权限
chmod u-s /bin/file1       禁用一个二进制文件的 SUID位
chmod g+s /home/public     设置一个目录的 SGID 位 - 类似SUID ，不过这是针对目录的
chmod g-s /home/public     禁用一个目录的 SGID 位
chmod o+t /home/public     设置一个文件的 STIKY 位 - 只允许合法所有人删除文件
chmod o-t /home/public     禁用一个目录的 STIKY 位
```

#### 2.2.20 tree命令（需安装）

tree    显示文件和目录由根目录开始的树形结构
        lstree 显示文件和目录由根目录开始的树形结构

#### 2.2.21 ln命令

功能：在文件和目录之间建立链接

格式：ln [参数] <源文件或目录> <目标文件或目录>

```
ln -s file1 lnk1 创建一个指向文件或目录的软链接
ln file1 lnk1    创建一个指向文件或目录的物理链接
```

#### 2.2.22 chattr命令

```
chattr +a file1    只允许以追加方式读写文件
chattr +c file1    允许这个文件能被内核自动压缩/解压
chattr +d file1    在进行文件系统备份时，dump程序将忽略这个文件
chattr +i file1    设置成不可变的文件，不能被删除、修改、重命名或者链接
chattr +s file1    允许一个文件被安全地删除
chattr +S file1    一旦应用程序对这个文件执行了写操作，使系统立刻把修改的结果写到磁盘
chattr +u file1    若文件被删除，系统会允许你在以后恢复这个被删除的文件
lsattr             显示特殊的属性
```

#### 2.2.23 wc命令

功能：统计

语法：`wc [-c -m -l -w] 文件路径`

- 选项，-c，统计bytes数量
- 选项，-m，统计字符数量
- 选项，-l，统计行数
- 选项，-w，统计单词数量
- 参数，文件路径，被统计的文件，可作为内容输入端口

### 2.3 系统指令

#### 2.3.1 系统信息查看

```
uname -m         显示机器的处理器架构
uname -r         显示正在使用的内核版本
hdparm -tT /dev/sda                在磁盘上执行测试性读取操作系统信息
(SMBIOS / DMI) hdparm -i /dev/hda  罗列一个磁盘的架构特性
hdparm -i /dev/hda   罗列一个磁盘的架构特性
arch                 显示机器的处理器架构
dmidecode -q         显示硬件系统部件 - (SMBIOS / DMI)
cat /proc/cpuinfo    显示CPU info的信息
cat /proc/interrupts 显示中断
cat /proc/meminfo    校验内存使用
cat /proc/swaps      显示哪些swap被使用
cat /proc/version    显示内核的版本
cat /proc/net/dev    显示网络适配器及统计
cat /proc/mounts     显示已加载的文件系统
lspci -tv            罗列 PCI 设备
lsusb -tv            显示 USB 设备
lsmod                查看加载的模块(驱动)
date                 显示系统日期
cal 2007             显示2007年的日历表
date 041217002007.00 设置日期和时间 - 月日时分年.秒
clock -w             将时间修改保存到 BIOS
iconv -l             列出已知的编码
```

#### 2.3.2 文件查找

```
find / -name file1                          从 '/' 开始进入根文件系统搜索文件和目录
find / -user user1                          搜索属于用户 'user1' 的文件和目录
find /home/user1 -name \.bin                在目录 '/ home/user1' 中搜索带有'.bin' 结尾的文件
find /usr/bin -type f -atime +100           搜索在过去100天内未被使用过的执行文件
find /usr/bin -type f -mtime -10            搜索在10天内被创建或者修改过的文件
find / -name \.rpm -exec chmod 755 '{}' \;  搜索以 '.rpm' 结尾的文件并定义其权限
find / -xdev -name \.rpm                    搜索以 '.rpm' 结尾的文件，忽略光驱等可移动设备
find / -perm -u+s                           罗列一个系统中所有使用了SUID控制的文件
locate \.ps                                 寻找以 '.ps' 结尾的文件 - 先运行 'updatedb' 命令
whereis halt                                显示一个二进制文件、源码或man的位置
which halt                                  显示一个二进制文件或可执行文件的完整路径
```

#### 2.3.3 文件系统挂载

```
mount /dev/hda2 /mnt/hda2                挂载一个叫做hda2的盘 - 确定目录 '/ mnt/hda2' 已经存在
umount /dev/hda2                         卸载一个叫做hda2的盘 - 先从挂载点 '/ mnt/hda2' 退出
fuser -km /mnt/hda2                      当设备繁忙时强制卸载
umount -n /mnt/hda2                      运行卸载操作而不写入 /etc/mtab 文件- 当文件为只读或当磁盘写满时非常有用
mount /dev/fd0 /mnt/floppy               挂载一个软盘
mount /dev/cdrom /mnt/cdrom              挂载一个cdrom或dvdrom
mount /dev/hdb /mnt/cdrecorder           挂载一个cdrw或dvdrom
mount -o loop file.iso /mnt/cdrom        挂载一个文件或ISO镜像文件
mount -t vfat /dev/hda5 /mnt/hda5        挂载一个Windows FAT32文件系统
mount /dev/sda1 /mnt/usbdisk             挂载一个usb 捷盘或闪存设备
mount -t smbfs -o username=user,password=pass //WinClient/share /mnt/share 挂载一个windows网络共享
```

#### 2.3.4 磁盘查看

```
df -h                                               显示已经挂载的分区列表
ls -lSr |more                                       以尺寸大小排列文件和目录
du -sh dir1                                         估算目录 'dir1' 已经使用的磁盘空间'
du -sk * | sort -rn                                 以容量大小为依据依次显示文件和目录的大小
dmesg                                               显示系统诊断信息、操作系统版本号、物理内存的大小以及其它信息
rpm -q -a --qf '%10{SIZE}t%{NAME}n' | sort -k1,1n   以大小为依据依次显示已安装的rpm包所使用的空间 (fedora, redhat类系统)
dpkg-query -W -f='${Installed-Size;10}t${Package}n' | sort -k1,1n   以大小为依据显示已安装的deb包所使用的空间 (ubuntu, debian类系统)
```

#### 2.3.5 软件安装命令

##### rpm

```
rpm -ivh package.rpm             安装一个rpm包
rpm -ivh --nodeeps package.rpm   安装一个rpm包而忽略依赖关系警告
rpm -U package.rpm               更新一个rpm包但不改变其配置文件
rpm -F package.rpm               更新一个确定已经安装的rpm包
rpm -e package_name.rpm          删除一个rpm包
rpm -qa                          显示系统中所有已经安装的rpm包
rpm -qa | grep httpd             显示所有名称中包含 "httpd" 字样的rpm包
rpm -qi package_name             获取一个已安装包的特殊信息
rpm -qg "System Environment/Daemons"     显示一个组件的rpm包
rpm -ql package_name                     显示一个已经安装的rpm包提供的文件列表
rpm -qc package_name                     显示一个已经安装的rpm包提供的配置文件列表
rpm -q package_name --whatrequires       显示与一个rpm包存在依赖关系的列表
rpm -q package_name --whatprovides       显示一个rpm包所占的体积
rpm -q package_name --scripts            显示在安装/删除期间所执行的脚本l
rpm -q package_name --changelog          显示一个rpm包的修改历史
rpm -qf /etc/httpd/conf/httpd.conf       确认所给的文件由哪个rpm包所提供
rpm -qp package.rpm -l                   显示由一个尚未安装的rpm包提供的文件列表
rpm --import /media/cdrom/RPM-GPG-KEY    导入公钥数字证书
rpm --checksig package.rpm               确认一个rpm包的完整性
rpm -qa gpg-pubkey                       确认已安装的所有rpm包的完整性
rpm -V package_name                      检查文件尺寸、 许可、类型、所有者、群组、MD5检查以及最后修改时间
rpm -Va                                  检查系统中所有已安装的rpm包- 小心使用
rpm -Vp package.rpm                      确认一个rpm包还未安装
rpm2cpio package.rpm | cpio --extract --make-directories *bin* 从一个rpm包运行可执行文件
rpm -ivh /usr/src/redhat/RPMS/`arch`/package.rpm               从一个rpm源码安装一个构建好的包
rpmbuild --rebuild package_name.src.rpm                        从一个rpm源码构建一个 rpm 包
```

##### yum[-y 自动确认] [install / remove / search] 软件名称

```
yum install package_name            下载并安装一个rpm包
yum localinstall package_name.rpm   将安装一个rpm包，使用你自己的软件仓库为你解决所有依赖关系
yum update package_name.rpm         更新当前系统中所有安装的rpm包
yum update package_name             更新一个rpm包
yum remove package_name             删除一个rpm包
yum list                            列出当前系统中安装的所有包
yum search package_name             在rpm仓库中搜寻软件包
yum clean packages                  清理rpm缓存删除下载的包
yum clean headers                   删除所有头文件
yum clean all                       删除所有缓存的包和头文件
```

##### deb

```
dpkg -i package.deb         安装/更新一个 deb 包
dpkg -r package_name        从系统删除一个 deb 包
dpkg -l                     显示系统中所有已经安装的 deb 包
dpkg -l | grep httpd        显示所有名称中包含 "httpd" 字样的deb包
dpkg -s package_name        获得已经安装在系统中一个特殊包的信息
dpkg -L package_name        显示系统中已经安装的一个deb包所提供的文件列表
dpkg --contents package.deb 显示尚未安装的一个包所提供的文件列表
dpkg -S /bin/ping           确认所给的文件由哪个deb包提供
```

##### apt(用于Debian, Ubuntu 以及类似系统)[-y 自动确认] [install / remove / search] 软件名称

```
apt-get install package_name       安装/更新一个 deb 包
apt-cdrom install package_name     从光盘安装/更新一个 deb 包
apt-get update                     升级列表中的软件包
apt-get upgrade                    升级所有已安装的软件
apt-get remove package_name        从系统删除一个deb包
apt-get check                      确认依赖的软件仓库正确
apt-get clean                      从下载的软件包中清理缓存
apt-cache search searched-package  返回包含所要搜索字符串的软件包名称
```

#### 2.3.6 文本处理

```
cat file1 file2 ... | command <> file1_in.txt_or_file1_out.txt general syntax for text manipulation using PIPE, STDIN and STDOUT
cat file1 | command( sed, grep, awk, grep, etc...) > result.txt  合并一个文件的详细说明文本，并将简介写入一个新文件中
cat file1 | command( sed, grep, awk, grep, etc...) >> result.txt 合并一个文件的详细说明文本，并将简介写入一个已有的文件中
grep Aug /var/log/messages    在文件 '/var/log/messages'中查找关键词"Aug"
grep ^Aug /var/log/messages   在文件 '/var/log/messages'中查找以"Aug"开始的词汇
grep [0-9] /var/log/messages  选择 '/var/log/messages' 文件中所有包含数字的行
grep Aug -R /var/log/         在目录 '/var/log' 及随后的目录中搜索字符串"Aug"
sed 's/stringa1/stringa2/g' example.txt     将example.txt文件中的 "string1" 替换成 "string2"
sed '/^$/d' example.txt                     从example.txt文件中删除所有空白行
sed '/ *#/d; /^$/d' example.txt             从example.txt文件中删除所有注释和空白行
echo 'esempio' | tr '[:lower:]' '[:upper:]' 合并上下单元格内容
sed -e '1d' result.txt                      从文件example.txt 中排除第一行
sed -n '/stringa1/p'                        查看只包含词汇 "string1"的行
sed -e 's/ *$//' example.txt                删除每一行最后的空白字符
sed -e 's/stringa1//g' example.txt          从文档中只删除词汇 "string1" 并保留剩余全部
sed -n '1,5p;5q' example.txt                查看从第一行到第5行内容
sed -n '5p;5q' example.txt                  查看第5行
sed -e 's/00*/0/g' example.txt              用单个零替换多个零
cat -n file1                                标示文件的行数
cat example.txt | awk 'NR%2==1'             删除example.txt文件中的所有偶数行
echo a b c | awk '{print $1}'               查看一行第一栏
echo a b c | awk '{print $1,$3}'            查看一行的第一和第三栏
paste file1 file2                           合并两个文件或两栏的内容
paste -d '+' file1 file2                    合并两个文件或两栏的内容，中间用"+"区分
sort file1 file2                            排序两个文件的内容
sort file1 file2 | uniq                     取出两个文件的并集(重复的行只保留一份)
sort file1 file2 | uniq -u                  删除交集，留下其他的行
sort file1 file2 | uniq -d                  取出两个文件的交集(只留下同时存在于两个文件中的文件)
comm -1 file1 file2                         比较两个文件的内容只删除 'file1' 所包含的内容
comm -2 file1 file2                         比较两个文件的内容只删除 'file2' 所包含的内容
comm -3 file1 file2                         比较两个文件的内容只删除两个文件共有的部分
```

#### 2.3.7 字符/文件格式转换

```
dos2unix filedos.txt fileunix.txt     将一个文本文件的格式从MSDOS转换成UNIX
unix2dos fileunix.txt filedos.txt     将一个文本文件的格式从UNIX转换成MSDOS
recode ..HTML < page.txt > page.html  将一个文本文件转换成html
recode -l | more                      显示所有允许的转换格式
```

#### 2.3.8 文件系统操作

```
badblocks -v /dev/hda1    检查磁盘hda1上的坏磁块
fsck /dev/hda1            修复/检查hda1磁盘上linux文件系统的完整性
fsck.ext2 /dev/hda1       修复/检查hda1磁盘上ext2文件系统的完整性
e2fsck /dev/hda1          修复/检查hda1磁盘上ext2文件系统的完整性
e2fsck -j /dev/hda1       修复/检查hda1磁盘上ext3文件系统的完整性
fsck.ext3 /dev/hda1       修复/检查hda1磁盘上ext3文件系统的完整性
fsck.vfat /dev/hda1       修复/检查hda1磁盘上fat文件系统的完整性
fsck.msdos /dev/hda1      修复/检查hda1磁盘上dos文件系统的完整性
dosfsck /dev/hda1         修复/检查hda1磁盘上dos文件系统的完整性

mkfs /dev/hda1         在hda1分区创建一个文件系统
mke2fs /dev/hda1       在hda1分区创建一个linux ext2的文件系统
mke2fs -j /dev/hda1    在hda1分区创建一个linux ext3(日志型)的文件系统
mkfs -t vfat 32 -F /dev/hda1  创建一个 FAT32 文件系统
fdformat -n /dev/fd0          格式化一个软盘
mkswap /dev/hda3              创建一个swap文件系统
swapon /dev/hda3              启用一个新的swap文件系统
swapon /dev/hda2 /dev/hdb3    启用两个swap分区
```

#### 2.3.9 备份

```
dump -0aj -f /tmp/home0.bak /home    制作一个 '/home' 目录的完整备份
dump -1aj -f /tmp/home0.bak /home    制作一个 '/home' 目录的交互式备份
restore -if /tmp/home0.bak           还原一个交互式备份
rsync -rogpav --delete /home /tmp    同步两边的目录
rsync -rogpav -e ssh --delete /home ip_address:/tmp           通过SSH通道rsync
rsync -az -e ssh --delete ip_addr:/home/public /home/local    通过ssh和压缩将一个远程目录同步到本地目录
rsync -az -e ssh --delete /home/local ip_addr:/home/public    通过ssh和压缩将本地目录同步到远程目录
dd bs=1M if=/dev/hda | gzip | ssh user@ip_addr 'dd of=hda.gz' 通过ssh在远程主机上执行一次备份本地磁盘的操作
dd if=/dev/sda of=/tmp/file1     备份磁盘内容到一个文件
tar -Puf backup.tar /home/user   执行一次对 '/home/user' 目录的交互式备份操作
( cd /tmp/local/ && tar c . ) | ssh -C user@ip_addr 'cd /home/share/ && tar x -p'  通过ssh在远程目录中复制一个目录内容
( tar c /home ) | ssh -C user@ip_addr 'cd /home/backup-home && tar x -p'           通过ssh在远程目录中复制一个本地目录
tar cf - . | (cd /tmp/backup ; tar xf - )      本地将一个目录复制到另一个地方，保留原有权限及链接
find /home/user1 -name '*.txt' | xargs cp -av --target-directory=/home/backup/ --parents 从一个目录查找并复制所有以 '.txt' 结尾的文件到另一个目录
find /var/log -name '*.log' | tar cv --files-from=- | bzip2 > log.tar.bz2          查找所有以 '.log' 结尾的文件并做成一个bzip包
dd if=/dev/hda of=/dev/fd0 bs=512 count=1      做一个将 MBR (Master Boot Record)内容复制到软盘的动作
dd if=/dev/fd0 of=/dev/hda bs=512 count=1 从已经保存到软盘的备份中恢复MBR内容
```

#### 2.3.10 光盘

```
cdrecord -v gracetime=2 dev=/dev/cdrom -eject blank=fast -force 清空一个可复写的光盘内容
mkisofs /dev/cdrom > cd.iso            在磁盘上创建一个光盘的iso镜像文件
mkisofs /dev/cdrom | gzip > cd_iso.gz  在磁盘上创建一个压缩了的光盘iso镜像文件
mkisofs -J -allow-leading-dots -R -V "Label CD" -iso-level 4 -o ./cd.iso data_cd 创建一个目录的iso镜像文件
cdrecord -v dev=/dev/cdrom cd.iso  刻录一个ISO镜像文件
gzip -dc cd_iso.gz | cdrecord dev=/dev/cdrom - 刻录一个压缩了的ISO镜像文件
mount -o loop cd.iso /mnt/iso      挂载一个ISO镜像文件
cd-paranoia -B           从一个CD光盘转录音轨到 wav 文件中
cd-paranoia -- "-3"      从一个CD光盘转录音轨到 wav 文件中（参数-3）
cdrecord --scanbus       扫描总线以识别scsi通道
dd if=/dev/hdc | md5sum  校验一个设备的md5sum编码，例如一张 CD
```

#### 2.3.11 网络

```
ifconfig eth0：显示网络接口“eth0”的配置详细信息，例如IP地址、子网掩码和其他网络设置

ifup eth0：    启动网络接口“eth0”，使其能够发送和接收网络流量

ifdown eth0：  关闭网络接口“eth0”，禁止其发送或接收网络流量

ifconfig eth0 192.168.1.1 netmask 255.255.255.0：将网络接口“eth0”的IP地址和子网掩码配置为分别为“192.168.1.1”和“255.255.255.0”

ifconfig eth0 promisc：      将网络接口“eth0”设置为混杂模式，允许其捕获所有网络流量，包括不是发送到其MAC地址的数据包。

dhclient eth0：              请求网络接口“eth0”从DHCP服务器获取IP地址租约。

route -n show routing table：显示当前系统的路由表，显示当前的路由配置。

route add -net 0/0 gw IP_Gateway：  为系统添加默认网关，其中网关IP地址设置为“IP_Gateway”。

route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.1.1：通过网关“192.168.1.1”添加静态路由，以便通过该网关访问网络“192.168.0.0/16”。

route del 0/0 gw IP_gateway：删除之前添加的默认网关。

echo "1" > /proc/sys/net/ipv4/ip_forward：激活IP转发，允许系统在不同的网络接口之间进行IP数据包路由。

hostname：显示系统的主机名，即在网络上标识系统的名称。

host www.example.com：    执行DNS查找，将主机名“www.example.com”解析为IP地址，反之亦然。

nslookup www.example.com：同样执行DNS查找，将主机名“www.example.com”解析为IP地址，反之亦然。

ip link show： 显示所有网络接口的状态，包括其链路状态（已启用或已禁用）和其他信息。

mii-tool eth0：使用Media Independent Interface（MII）工具显示网络接口“eth0”的链路状态。

ethtool eth0： 显示网络卡“eth0”的统计信息和详细信息，例如速度、双工模式和错误计数器。

netstat -tup： 显示使用TCP和UDP协议的所有活动网络连接及其关联的进程（通过PID标识）。

netstat -tupl：显示系统上所有监听的网络服务及其关联的进程（通过PID标识）使用TCP和UDP协议。

`tcpdump tcp port 80`：显示所有在端口80上使用TCP协议的网络流量，通常用于监控HTTP（超文本传输协议）流量。

iwlist scan：  显示无线网络接口的扫描结果，列出可用的无线网络。

iwconfig eth1：显示无线网络接口“eth1”的配置信息，包括SSID、信号强度和加密设置等。

hostname：     显示系统的主机名，即在网络上标识系统的名称。

host www.example.com：    执行DNS查找，将主机名“www.example.com”解析为IP地址，反之亦然。

nslookup www.example.com：同样执行DNS查找，将主机名“www.example.com”解析为IP地址，反之亦然。

whois www.example.com：   在Whois数据库中查找主机名“www.example.com”的注册信息，包括域名所有者、注册商、联系信息等。
```

#### 2.3.12 其它命令

**bc**  用于编写脚本进行高精度数学运算

编写如下sqrt脚本，可使用`./sqrt 数字` 进行平方根运算

```
#!/bin/bash
if [ $# -ne 1 ]
then
    echo 'Usage: sqrt number'
    exit 1else
    echo -e "sqrt($1)\nquit\n" | bc -q -i
fi
```

**split** 用于分割大型文件

用法：split [选项] [输入文件] [输出文件前缀]

```
-b：指定每个输出文件的大小，后面跟着的参数可以是以字节（B）、千字节（K）、兆字节（M）等为单位的数值。例如 

-b 1M 表示每个输出文件的大小为1兆字节

-l：指定每个输出文件的行数，后面跟着的参数为整数。例如 -l 1000 表示每个输出文件包含1000行

-d：设置输出文件的后缀数字的长度，默认为2

-a：设置输出文件的后缀字符，默认为字母 "a"
```

```
# ls -l largefile.tar.gz
输出-rw-r--r-- 1 aa aa 436774774 04-17 02:00 largefile.tar.gz
# split -b 50m largefile.tar.gz LF_
# ls -l LF_*-rw-r--r-- 1 aa aa 52428800 05-10 18:34 LF_aa
输出-rw-r--r-- 1 aa aa 52428800 05-10 18:34 LF_ab
   -rw-r--r-- 1 aa aa 52428800 05-10 18:34 LF_ac
   -rw-r--r-- 1 aa aa 52428800 05-10 18:34 LF_ad
   -rw-r--r-- 1 aa aa 52428800 05-10 18:34 LF_ae
   -rw-r--r-- 1 aa aa 52428800 05-10 18:35 LF_af
   -rw-r--r-- 1 aa aa 52428800 05-10 18:35 LF_ag
   -rw-r--r-- 1 aa aa 52428800 05-10 18:35 LF_ah
   -rw-r--r-- 1 aa aa 17344374 05-10 18:35 LF_ai
```

拆分后合并

```
cat LF_* >largefile.tar.gz
```

**nl** nl命令其它和cat命令很像，只不过它会打上行号

**ldd** 查看一个可执行文件所使用的动态链接库 ldd+文件目录/文件名

**col** 把man文件转成纯文本文件

```
# PAGER=cat# man less | col -b > less.txt
```

**xmlwf** 检查一个XML文档是否是所有的tag都是正常的

```
# curl 'https://coolshell.cn/?feed=rss2' > cocre.xml
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 64882    0 64882    0     0  86455      0 --:--:-- --:--:-- --:--:-- 2073k
# xmlwf cocre.xml
# perl -i -pe 's@<link>@<br>@g' cocre.xml
# xmlwf cocre.xmlcocre.xml:13:23: mismatched tag
```

**lsof** 可以列出打开了的文件

```
# lsof | grep TCPhttpd       548    apache    4u     IPv6   14300967    TCP *:http (LISTEN)
httpd       548    apache    6u     IPv6   14300972    TCP *:https (LISTEN)
httpd       561    apache    4u     IPv6   14300967    TCP *:http (LISTEN)
httpd       561    apache    6u     IPv6   14300972    TCP *:https (LISTEN)
sshd       1764      root    3u     IPv6       4993    TCP *:ssh (LISTEN)
tcpserver  8965      root    3u     IPv4  153795500    TCP *:pop3 (LISTEN)
mysqld    10202     mysql   10u     IPv4   73819697    TCP *:mysql (LISTEN)
sshd      10735      root    3u     IPv6  160731956    TCP 210.51.0.232:ssh->123.117.239.68:31810 (ESTABLISHED)
sshd      10767     hchen    3u     IPv6  160731956    TCP 210.51.0.232:ssh->123.117.239.68:31810 (ESTABLISHED)
vsftpd    11095      root    3u     IPv4  152157957    TCP *:ftp (LISTEN)
```



### 2.4 vim的使用

vim有三种模式

![linux_vim3.png](https://s2.loli.net/2024/03/15/OGYkAc25yVW4brl.png)

**<u>使用技巧</u>**帮助系统（内容收集于vimtutor）

```
- 按下 <HELP> 键 (如果键盘上有的话)
- 按下 <F1> 键 (如果键盘上有的话)
- 输入 :help <回车>
输入 CTRL-W CTRL-W   可以在窗口之间跳转。
输入 :q <回车> 可以关闭帮助窗口

Vim 的功能特性要比 Vi 多得多，但其中大部分都没有缺省启用，创建一个vimrc文件以启用更多特性
1. 开始编辑 vimrc 文件
 :edit ~/.vimrc		这是 Unix 系统所使用的命令
 :edit $VIM/_vimrc	这是 MS-Windows 系统所使用的命令
2. 接着读取 vimrc 示例文件的内容：
 :r $VIMRUNTIME/vimrc_example.vim

3. 保存文件，命令为：
 :write
  下次您启动 Vim 时，编辑器就会有了语法高亮的功能，要了解更多信息，添加设置请输入 :help vimrc-intro
```

#### 2.4.1基本插入删除，保存退出

h、j、k、l 键分别对应光标键的左、下、上、右

按<ESC>键。然后输入`:q!` <回车>   表示不保存退出，使用 `:wq` 可以保存文件并退出

命令模式下按`x`即可删除字符

命令模式下按`i`即可进入插入模式，按`a`键可在光标之后插入文本

命令模式输入 `o` 将在光标的**下方**打开新的一行并进入插入模式

命令模式输入 `O` 将在光标的**上方**打开新的一行并进入插入模式

#### 2.4.2删除与撤销

输入 `dw` 可以从光标处删除至一个单词的末尾

输入 `d$` 从当前光标删除到行末

输入 `dd` 可以删除整一个当前行

```
    d      - 删除操作符。
    motion - 操作符的操作对象。

    w - 从当前光标当前位置直到下一个单词起始处，不包括它的第一个字符。
    e - 从当前光标当前位置直到单词末尾，包括最后一个字符。
    $ - 从当前光标当前位置直到当前行末。
    
    在动作前输入数字会使它重复那么多次，如输入 2w 使光标向前移动两个单词，输入 3e 使光标向前移动到第三个单词的末尾，因此输入 d2w 可以删除两个大写字母单词，输入 2dd 可以删除两行
```

```
输入 u 来撤消最后执行的命令，输入 U 来撤消对整行的修改，输入 CTRL+R 可以重做被撤消的命令
```

#### 2.4.3更改与替换

输入 `p` 可以将最后一次删除的内容置入光标之后

```
输入 dd 删除整行，这样会将该行保存到 Vim 的一个寄存器中
接着将光标移动到 准备置入的位置的上方，然后在命令模式下输入 p 将该行粘贴置入
```

输入 `r` 和**一个字符**替换光标所在位置的字符

输入 `R` 可连续替换多个字符

输入  `ce` 可以改变文本直到一个单词的末尾

改类操作符的工作方式跟删除类是一致的，动作参数（motion）也是相同的。

#### 2.4.4查找与定位

1.输入 `CTRL-G` 显示当前编辑文件中当前**光标所在行**位置以及文件状态信息

输入 `CTRL-O` 可以回到之前的位置

`CTRL-I` 会跳转到较新的位置

```
输入大写 G 可以使得当前光标直接跳转到文件最后一行，行号+G跳转到指定行
输入 gg 可以使得当前光标直接跳转到文件第一行
```

2.在命令模式下输入`/ 想查找的字符` 可以实现查找操作，按n键可以查找同上一次的字符串，N向相反方向查找同上一次的字符串`？ 想查找的字符` 可以逆向查找字符串

3.输入 `%` 可以查找配对的括号 )、]、}，当光标在括号上时按`%` 即可跳转到与之匹配的括号处，再按则返回原来位置，可用于程序调试

4.输入 :s/old/new 可以替换第一个匹配到的字符串 old 为 new

```
     输入   :s/old/new/g      可以替换整行 old 为 new
     输入   :#,#s/old/new/g   其中 #,# 代表的是替换操作的若干行中首尾两行的行号。
     输入   :%s/old/new/g     则是替换整个文件中的每个匹配串。
     输入   :%s/old/new/gc    会找到整个文件中的每个匹配串，并且对每个匹配串提示是否进行替换。
```

#### 2.4.5移动与批量操作

输入 `:!` 然后紧接着输入一个外部命令+<回车>即可执行该外部命令

输入 `:w FILENAME`可以把对当前文件的改动保存到FILENAME文件中

```
部分保存：
按 v 键，将光标从第一个想保存的字符移动至最后一个，这之间的文本被高亮了，按 : 字符。屏幕底部会出现 :'<,'> 
输入 w TEST， TEST 应是一个未被使用的文件名。在出现:'<,'>w TEST 之后按 <回车> 键
```

插入

```
输入 :r FILENAME向当前文件中插入另外的文件的内容，提取进来的文件将从光标所在位置处开始置入
```

复制

```
按 v 键，将光标从第一个想保存的字符移动至最后一个，这之间的文本被高亮了，输入y复制，接着输入 p 粘贴。
y 可以当作操作符来使用，如yw复制一个单词
```

```
输入 :set xxx 可以设置 xxx 选项。一些有用的选项如下：
    'ic' 'ignorecase'   查找时忽略字母大小写
    'is' 'incsearch'    查找短语时显示部分匹配
    'hls' 'hlsearch'    高亮显示所有的匹配短语
    :set nu             显示行号
    :set nonu           不显示行号
     选项名可以用完整版本，也可以用缩略版本，在选项前加上 no 可以关闭选项：  :set noic
```

#### 2.4.6补全功能

使用 CTRL+D 和 <TAB> 可以进行命令行补全

```
  1. 确保 Vim 不是在以兼容模式运行： :set nocp
  2. 查看一下当前目录下已经存在哪些文件，输入： :!ls   或者  :!dir
  3. 现在输入一个目录的起始部分，例如输入： :e
  4. 接着按 CTRL+D 键，Vim 会显示以 e 开始的命令的列表。
  5. 然后按 <TAB> 键，Vim 会补全命令为 :edit 。
  6. 现在添加一个空格，以及一个已有文件的文件名的起始部分，例如： :edit FIL
  7. 接着按 <TAB> 键，Vim 会补全文件名(如果它是唯一匹配的)。
```