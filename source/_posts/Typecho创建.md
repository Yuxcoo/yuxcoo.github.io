---
title: Typecho创建
categories: 旧日
comments: true
cover: 'https://s2.loli.net/2024/03/15/9qFZQXx34PULH2K.png'
tags:
  - blog
  - nginx
  - vps
date: 2023-03-12 14:32:39
abbrlink: typechocreate
---
在写完Halo博客搭建后，决定再记录一下主站typecho博客的搭建过程。typecho是一款轻量化博客程序，系统内存占用少，性能良好，搭建方便，操作简单。在多年前就是口碑良好的博客程序。~~遗憾的是在2017年就已经停止更新了~~（似乎又恢复更新了），并且缺点是所有插件需要自己安装，主题切换不保存设置数据，且不支持在博客页面编辑主题信息，编写文章时没有预览功能等。但是非常节省内存资源，加上宝塔面板占用才200-300M，相比之下Halo就需要800M左右的空间来保证运行，在[Haxio][1]白嫖的Kvm的机器内存非常(~~没~~)好用(~~钱~~)，只是内存只有可怜的450M，用来做typecho再合适不过（随便玩玩，随时寄），毕竟是原生IP，只是用来做节点有点浪费。
注意，虚拟化方式为Openvz的vps**建议**先开启tun，以hax为例（*hax账号注册需要tg账号，搜索HAX_bot得到id，在登录页面输入id后，bot会发送一串校验码，复制到登录页内重置密码即可，这里不过多赘述*），登录后点击**Poweroff & Restart VPS**
![tun.png][2]
点击Enable TUN，然后在终端输入 cat /dev/net/tun，显示in bad state或者Finalshell显示文件处于错误的描述阶段就表示开启成功（halo博客文中已提及）
# 安装宝塔面板
请保证是纯净的系统，未安装任何环境
```
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```
typecho博客之所以简单在于基本只需要这一行代码即可完成博客部署
具体步骤[Halo文中已经写过][3]
安装LNMP套件，PHP版本请选择7.2（typecho最高支持7.2）![LNMP套件.png][4]
# 一键部署
在软件商店-宝塔插件内安装宝塔一键部署源码
![一键部署源码.png][5]
点击设置，选择博客，点击typecho一键部署
![一键部署源码设置.png][6]
输入域名之后很快，会弹出MySQL的账号和密码,复制好保存备用（halo博客使用的是H2 Database，所以LNMP套件可以不安装MySQL及其相关）
![域名部署.png][7]
点击网站，在创建好的域名后点击设置，设置伪静态，选择typecho模板并保存
![伪静态.png][8]
# 主题和插件上传
保存完点击网站目录-usr-themes，上传自己喜欢的主题，网站目录-usr-plugins上传插件。这里提供两个typecho主题和插件的下载网站[1站][10]和[2站][11]，建议上传压缩包上传后解压，不然上传速度很慢
![主题上传.png][9]
使用域名访问博客并进行初始化，输入之前保存的数据库信息，设置后台访问的账号密码，安装成功
![typecho初始化.png][12]
![安装成功.png][13]
进入主页即可撰写文章，更换主题，安装插件
![博客主页.png][14]
这里提供一个有众多[live2d看板娘][15]模型的网站，推荐的其他插件有代码高亮，动态线条聚合等，需要数学公式的请在footer.php中手动添加mathjax（或Katex），具体方式自行搜索
```
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
      extensions: ["tex2jax.js"],
      jax: ["input/TeX", "output/HTML-CSS"],
      tex2jax: {
        inlineMath:  [ ["$", "$"],  ["\(","\)"] ],
        displayMath: [ ["$$","$$"], ["\[","\]"] ],
        processEscapes: true
      },
      "HTML-CSS": { availableFonts: ["TeX"] }
    });
  </script>
  <script type="text/javascript"
     src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
  </script>
```
# 开启ssl
详情请见[Halo][17]
lets encrypt申请失败的话可以自行去阿里云/腾讯云申请后粘贴到其他证书内
# 关于开启代理后的问题
开启cf代理的目的是使只有IPv6地址的服务器能够被纯IPv4访问
[cf代理开启方式][16]
typecho在开启代理后请不要在宝塔面板打开强制https，第二点是打开代理后博客后台可能会出现无法登录的情况，点登录后仍然返回登录界面，因为本地没有开启强制https导致cf cdn重定向错误无法登录typecho后台
这时候需要在网站目录的config.inc.php的代码注释过后（大约第9-10行）加入
```
define('__TYPECHO_SECURE__',true);
```

</br>
更多功能还请读者自行探索，文章若有错误还望大佬评论区告知谢谢

[1]:https://hax.co.id/create-vps/
[2]: https://s2.loli.net/2024/03/15/Y5mX6WuEOMt8cF4.png
[3]:https://blog.icjlu.eu.org/post/halocreate.html
[4]:https://s2.loli.net/2024/03/15/cUGb2MkhZoiVSQO.png
[5]:https://s2.loli.net/2024/03/15/ok3buY2rLvtScU5.png
[6]:https://s2.loli.net/2024/03/15/UKMGBaCTe6osJqb.png
[7]:https://s2.loli.net/2024/03/15/TumMf3S7k1qYNIh.png
[8]:https://s2.loli.net/2024/03/15/XPSMFwkOfZzxjHT.png
[9]:https://s2.loli.net/2024/03/15/hfqKUeFMlJQi84s.png
[10]:https://typecho.me/page-2.html
[11]:https://store.ijkxs.com/ztmb/typecho/typecho_themes/page/4?price_type=1
[12]:https://s2.loli.net/2024/03/15/j39DozG1sYJX7fO.png
[13]:https://s2.loli.net/2024/03/15/qslgN8OuyZh7Sow.png
[14]:https://s2.loli.net/2024/03/15/8w1dAiehEN4ORzU.png
[15]:https://mx.paul.ren
[16]:https://blog.icjlu.eu.org/post/halocreate.html
[17]:https://blog.icjlu.eu.org/post/halocreate.html