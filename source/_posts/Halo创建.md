---
title: Halo创建
categories: 旧日
comments: true
cover: 'https://s2.loli.net/2024/03/15/Loeuy4xS3JkOjTi.png'
tags:
  - blog
  - nginx
  - vps
date: 2023-03-09 18:54:39
abbrlink: halocreate
---

本文将对VPS使用Docker容器搭建Halo博客的一般方式作简述（小白的逐步操作），大致分为

1. 安装Docker引擎
2.  创建容器
3.  拉取Halo镜像
4.  安装nginx并配置反向代理
5.  开启SSL
6.  创建，美化博客页面

 

搭建Halo博客需要VPS服务器一台（最低配置要求1C1G，docker本身占用就接近400M的Ram，至于核心一般来说1核就够了），域名1个，~~搭建完就吃灰的决心~~。

~~如果购买的是虚拟化方式为Openvz的服务器请先前往运营商处开启tun，然后在终端输入 cat /dev/net/tun，显示in bad state或者Finalshell显示文件处于错误的描述阶段就表示开启成功了，不过应该没人买Ovz的机器，除了像我这样从Hax白嫖的~~

首先使用Finalshell/Xshell或者命令行（ssh root@）连接上购买服务器的IP地址

# 依赖安装与配置

## 安装Docker引擎

参考：[Docker官方文档][2]

![docker官方文档][1]

*常见系统的安装都有，本文只介绍最简单的安装过程，可选步骤请移步官方文档*

1.安装utils包

```
yum install -y yum-utils
```

2.设置仓库

```
yum-config-manager \

    --add-repo \

    https://download.docker.com/linux/centos/docker-ce.repo
```

3.安装docker引擎

```
yum install docker-ce docker-ce-cli containerd.io
```

4.启动docker

systemctl start docker

systemctl enable docker.service//设置docker开机自启动

docker自启动的设置可选择不执行，博主的服务器在执行自启动后nginx会出现异常导致网站无法正常访问，如果执行后无法使用域名访问博客可以关闭自启动（enable改为disable)reboot可解决

*5.拉取测试镜像(可选)

```
docker run hello-world//拉取hello-world测试docker是否正常运行，一般都是正常，可以不用操作
```

安装过程出现的询问操作输入y即可，第三步安装引擎时有个指纹校对可以对比一下，一般都是吻合的

```
060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35
```

## 使用 Docker 部署 Halo

参考：[官方文档][3]

安装完毕就可以使用docker部署halo了，按照官方文档操作

1.创建工作目录

```
mkdir ~/.halo && cd ~/.halo
```

2.下载示例配置文件到工作目录

```
wget https://dl.halo.run/config/application-template.yaml -O ./application.yaml
```

*3.编辑配置文件，配置数据库或者端口等，如需配置请参考官方文档(可选)

```
vim application.yaml
```

4.拉取最新的 Halo 镜像

```
docker pull halohub/halo:1.4.17//截至本文发布halo的最新版本为1.4.17，访客可自行前往官网查询最新版本或者将版本号改为latest
```



```
纯IPv6机器请先修改DNS否则无法解析

echo "nameserver 2a00:1098:2b::1" > /etc/resolv.conf
```



5.创建容器

```
docker run -it -d --name halo -p 8090:8090 -v ~/.halo:/root/.halo --restart=unless-stopped halohub/halo:1.4.17//注意版本号
```

*对创建容器的部分代码作解释*

第一个8090表示本地的端口映射到第二个halo上的8090端口，第一个可以更改为任意没有被占用的端口，第二个不可更改。更改端口可以在一台服务器上安装多个halo博客，阿里云/腾讯云等开启了安全组的云服务器商请先在服务商控制面板处开启端口放行80，443等常用端口以及halo映射的端口

```
-it： 开启输入功能并连接伪终端

-d： 后台运行容器

-name： 为容器指定一个名称

-p： 端口映射，格式为 主机(宿主)端口:容器端口 ，可在 application.yaml 配置。

-v： 工作目录映射。形式为：-v 宿主机路径:/root/.halo，后者不能修改。

-restart： 建议设置为 unless-stopped，在 Docker 启动的时候自动启动 Halo 容器。其它设置：

 no	       不自动重启容器. (默认value)

 on-failure    容器发生error而退出(容器退出状态不为0)重启容器

 unless-stopped 	在容器已经stop掉或Docker stoped/restarted的时候才重启容器

 always     在容器已经stop掉或Docker stoped/restarted的时候才重启容器

完成后等待片刻（finalshell中cpu占有降低时），halo博客就部署完成了，此时就可以使用http://ip:端口号 的形式即可看到安装引导界面，不过建议配置好反向代理后再初始化博客。
```

 

# 安装nginx并配置反向代理

## 源码安装

方法1使用的是源码安装nginx，目录/etc/nginx如果有需要LNMP套件的可以使用以下代码安装

```
wget http://soft.vpser.net/lnmp/lnmp1.8.tar.gz -cO lnmp1.8.tar.gz && tar zxf lnmp1.8.tar.gz && cd lnmp1.8 && ./install.sh lnmp
```

```
安装目录

Nginx 目录: /usr/local/nginx/

MySQL 目录 : /usr/local/mysql/

MySQL数据库所在目录：/usr/local/mysql/var/

PHP目录 : /usr/local/php/

默认网站目录 : /home/wwwroot/default/

Nginx日志目录：/home/wwwlogs/

LNMP软件配置文件路径

Nginx主配置(默认虚拟主机)文件：/usr/local/nginx/conf/nginx.conf

添加的虚拟主机配置文件：/usr/local/nginx/conf/vhost/域名.conf

MySQL配置文件：/etc/my.cnf

PHP配置文件：/usr/local/php/etc/php.ini

php-fpm配置文件：/usr/local/php/etc/php-fpm.conf

\#重启服务让配置生效

lnmp {nginx|mysql|mariadb|php-fpm|pureftpd} restart

\#或者直接重启LNMP：

lnmp restart
```

1.添加 Nginx 源

```
rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
```

2.安装 Nginx（CentOS）

```
yum install -y nginx
```

3.启动 Nginx

```
systemctl start nginx.service
```

4.设置开机自启 Nginx

```
systemctl enable nginx.service
```

Ubuntu系统nginx安装方式

```
sudo update

sudo apt install nginx
```

5.下载 Halo 官方的 Nginx 配置模板到本地

```
curl -o /etc/nginx/conf.d/halo.conf --create-dirs https://dl.halo.run/config/nginx.conf
```

nginx若出现启动失败，通常是80端口被占用，查看与80相关的端口

```
netstat -lnp|grep 80

\# 命令无法使用请先输入下面代码安装

yum -y install net-tools
```

在找到80端口的占用后杀死对应的进程号，如果仍然启动失败可尝试多杀几次

```
kill -9 进程号

systemctl restart nginx//重启nginx
```



如果使用yum拉取镜像安装nginx，nginx一般安装在/usr/local/nginx/conf/nginx.conf文件夹中，宝塔面板则是在/www/server/panel/vhost/nginx/conf/nginx.conf使用下面的代码无法直接配置nginx，而是会创建一个新的目录存放halo.conf，需要建立软连接（请自行搜索方法）或在nginx安装目录中找到nginx.conf，在http{}中添加

```
include /etc/nginx/conf.d/halo.conf
```

或者其他自定义的路径，保证正确即可

6.使用vi/vim编辑halo.conf应用nginx配置，或者使用finalshell等其他工具对文件进行编辑

```
vim /etc/nginx/conf.d/halo.conf//如果vim提示命令不存在可使用vi,配置完毕后按下esc键输入 :wq 退出并保存
```

模板文件打开后格式为

```
upstream halo {

  server 127.0.0.1:8090;//更改为你的服务器ip以及设置的端口

}

server {

  listen 80;

  listen [::]:80;

  server_name xxx.xx;//你的域名

  client_max_body_size 1024m;

  location / {

    proxy_pass http://halo;

    proxy_set_header HOST $host;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

  }

}
```

 

配置完后使用nginx检查是否含有错误

```
nginx -t
```

出现successfully时，表示配置文件无误，重新载入nginx即可使用域名访问博客

```
nginx -s reload
```

至此，源码安装的方式部署完成。

## 使用宝塔面板安装nginx

方法2是使用宝塔帮助安装web服务器，优点是可视化，操作简单，首先安装宝塔面板

```
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```

期间出现的询问都输入y

安装完毕后会提示默认端口8888和用户名密码，没有弹出的话输入bt default

```
外网面板地址: http://*****:****/*****

内网面板地址: http://***.**.**.**:****/*****

*以下仅为初始默认账户密码，若无法登录请执行bt命令重置账户/密码登录

username: ******

password: ****
```

 

此时访问外网面板登录会提示绑定宝塔账号，博主个人不太接受这种强制绑定的方式（不介意的跳过下面这步），~~所以在网上搜集了解除的方法。目前宝塔面板最新版为7.8，暂时还没有破解方式，现在的思路是降级到7.7。~~

**最新消息，使用破解版宝塔面板7.8的服务器都将被查封，并且拉黑IP，即该服务器将永远无法安装宝塔面板，读者请量力而行，7.7暂时安全**

```
curl -sSO https://raw.githubusercontent.com/zhucaidan/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh

sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|"/www/server/panel/BTPanel/static/js/index.js

rm -f /www/server/panel/data/bind.pl
```

此时访问已不再提示登录，并在首页弹出Linux套件安装，选择LNMP推荐的（nginx-php-mysql-apache）一键安装即可，经过漫长的等待（约20-30min）依赖环境都安装完毕。



点击网站添加站点，填上主域名（不可泛解析），次域名（选填），网站备注

![bt][4]

然后点击设置，选择反向代理，根据面板的提示键入信息即可完成反向代理

![创建反向代理][5]

或者选择配置文件，按照方法1中配置的方式，在配置文件49-61使用ctrl+/注释掉，然后在62行{}添加相应的信息（使用面板的反向代理只能反代一个halo博客，添加新的反向代理会覆盖之前的配置--貌似）

使用宝塔辅助nginx反代配置完成

```
 location / {

  proxy_pass http://127.0.0.1:8090/;

  rewrite ^/(.*)$ /$1 break;

  proxy_redirect off;

  proxy_set_header Host $host;

  proxy_set_header X-Forwarded-Proto $scheme;

  proxy_set_header X-Real-IP $remote_addr;

  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

  proxy_set_header Upgrade-Insecure-Requests 1;

  proxy_set_header X-Forwarded-Proto https;

}
```

# 开启SSL，启用https访问

配置完反向代理后，已经可以使用域名访问博客，但浏览器显示的是网站不安全，因为没有受信任的证书，此时是http明文与主机传输数据，需要申请ssl证书上传并验证通过才能启用https。

ssl证书可以在阿里云、腾讯云，Cloudflare，acme.sh、certbot申请，

其中阿里云和腾讯云免费申请的是1年有效的亚洲诚信颁发的证书，Cloudflare免费申请的是一年有效的边缘证书或最高15年有效的cf自签名证书，acme.sh和certbot免费申请的是3个月Let's Encrypt证书（可自动续期，但可能失败），有需要也可以在这些平台购买付费证书，安全性更高，并且有专人帮你安装（价格不菲）



如果上一步使用的是宝塔面板辅助安装的，可以直接在网站页面点击ssl部署，选中域名一键申请，宝塔就会自动申请证书并帮你完成部署，再点击右上角的强制https就实现了https访问，此时网站已变成受信任状态（如果在DNS服务商处已经开启了强制https请不要点击，会导致重定向次数过多无法正常访问），或者已经拥有其他平台的证书，点击其他证书，把公钥和私钥内容粘贴进去即可

![lets-encrypt][6]

阿里云和腾讯云请在控制台搜索ssl申请证书，关于其他平台证书的申请方式请自行搜索，本文只介绍证书的导入和安装，其中cf的自签名证书只会显示一次，没有保存就找不到了，证书的格式为.pem，腾讯云的为.crt（貌似也有pem），密钥格式为.key

证书下载到本地后，使用FTP上传到服务器（不知道怎么使用的自行搜索）或者使用Finalshell进行上传，上传完成后打开之前配置的halo.conf，启用ssl，打开443端口监听

```
upstream halo {

  server 127.0.0.1:8090;

}

server {

  listen 80;

  listen [::]:80;

  listen 443 ssl;

  server_name ****.**;//多个域名请加 , 后继续输入

  client_max_body_size 1024m;

ssl_certificate /crt/certificate.pem;//证书上传的存放路径

ssl_certificate_key /crt/privatekey.key;//密钥上传的存放路径

ssl_session_timeout 5m;

ssl_protocols TLSv1 TLSv1.1 TLSv1.2;//启用的tls版本，建议不要开启tls v1，存在漏洞，最新版本为v1.3

ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;//加密方式

ssl_prefer_server_ciphers on;//开启加密

  location / {

     proxy_pass http://halo;

     proxy_set_header HOST $host;

     proxy_set_header X-Forwarded-Proto $scheme;

     proxy_set_header X-Real-IP $remote_addr;

     proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

  }

}
```

检查规则，重新加载nginx

```
nginx -t

nginx -s reload
```

检查ssl是否正常开启，出现ssl xxx的就代表开启成功

```
echo|openssl s_client -connect 127.0.0.1:443 -servername sslconfigure.certqa.cn 2>/dev/null
```

如果没有请检查防火墙是否拦截，宝塔面板用户请进入安全页面放行443端口

```
firewall-cmd --state//检查防火墙开启状态

firewall-cmd –zone=public –add-port=443/tcp –permanent//放行443端口
```

完成以上步骤，就可以使用https访问博客了

### *IPV6 Only的服务器如何能让IPV4 Only的网络访问

一些廉价服务器只提供IPV6的公网地址（IPV4公网地址太少了得加钱），导致只有IPV4网络的用户无法访问。而IPV 4 to 6的隧道部署又相对较为繁琐，这里博主采用cf的CDN代理来解决

![cf代理][7]

打开[cloudflare][8]，添加站点,将cf提供的两个地址填入域名注册商的名称服务器，等待生效后打开添加的站点，点击DNS输入IP地址以及解析形式，小云朵代理状态选择开启

![cf ssl证书设置][9]

打开始终使用https（宝塔面板的记得关闭），最低tls版本选择1.1，打开随机加密，此时只有IPV4的网络经过cf代理也能成功访问博客（貌似不上传证书和配置ssl，只打开代理也能实现https访问，感兴趣的读者可自行尝试），但服务器仍然无法访问仅IPV4的资源，需要IPV 6 to 4隧道/NAT地址转换或者安装warp以实现，这里不再赘述。

 

# 博客美化

使用 域名/admin 访问博客，完成初始化操作并登录后台

![halo登录][10]

![halo面板][11]

打开面板后可以看到各种博客数据，非常简洁，而且面板样式也很简约但又没有过分固化，个人是挺喜欢的，非常适合只想安心写博客的朋友，不过默认的网站外观不太好看，可以前往Halo官方的[主题仓库][12]选择自己喜欢的外观，点击面板的外观页面，点击安装选择安装包安装或远程安装（推荐安装包安装），~~本人使用的是大佬移植Wordpress的Sakura主题，如有使用该主题的，~~博客外观设置可以参考[LIlGG的操作指南][13]

![halo外观][14]

外观设置完毕后可以在页面栏选择新建页面用于在博客内分栏展示，在外观的菜单栏中可以添加独立页面的小图标，Sakura主题支持Font Awesome图标，各图标样式可以[点击查看][17]和[Font Awesome v6][19]，另外可以对图标增加的动态效果代码可以[查看][18]。具体使用方法实示例

```
fa fa-bank faa-tada//银行图标，放大旋转特效
```

 ![font awesome动态特效][15]

然后点击用户栏，设置个人资料包括用户名，昵称，邮箱，以及更改密码都在这个页面

最后点击系统栏-博客设置添加网站的logo和favicon（浏览器标签页图标）还有页脚信息，可用于添加统计代码（访客数量，网站运行时间等，但貌似只能添加一个）如有需要添加api服务的可以点击高级选项进行设置

[自建的一言api][20]

![博客设置][16]

仍然有改造主题需要的可以点击外观栏的主题编辑进行修改][16]

 一般对footer和header进行更改即可，具体方式和更多有趣的内容还请自行探索



以上就是halo博客从创建到美化的全过程了，本人小白，折腾这个博客也是花了不少时间，故理清流程后将其记录，如本文有错漏之处，还请大佬可以在评论区留言谢谢!

 

 

 

 

 

 

 

[1]: https://s2.loli.net/2024/03/15/3imgwh74HxETj6S.png
[2]: https://docs.docker.com/engine/install/centos/
[3]: https://docs.halo.run/getting-started/install/docker/
[4]: https://s2.loli.net/2024/03/15/LcqzPkjlWD8Zar9.png
[5]: https://s2.loli.net/2024/03/15/3kX45sWq7IEU82N.png
[6]: https://s2.loli.net/2024/03/15/kizmlBZqnUHN6Qw.png
[7]: https://s2.loli.net/2024/03/15/pgVao6rilPOYvsQ.png
[8]: https://dash.cloudflare.com/
[9]: https://s2.loli.net/2024/03/15/QMOJte7yj5NCUgh.png
[10]: https://s2.loli.net/2024/03/15/dXnB4ATQacojS9P.png
[11]: https://s2.loli.net/2024/03/15/wmrUS2CTIuYJb1H.png
[12]: https://halo.run/themes.html
[13]: https://lixingyong.com/2021/01/05/halo%E4%B8%BB%E9%A2%98sakura%E9%A3%9F%E7%94%A8%E8%AF%B4%E6%98%8E
[14]: https://s2.loli.net/2024/03/15/3iA95eEzjRyISfW.png
[15]: https://s2.loli.net/2024/03/15/bIpgQX286mKCeV3.png
[16]: https://s2.loli.net/2024/03/15/ZqfTQiO8H29pwjA.png
[17]: https://www.runoob.com/font-awesome/fontawesome-reference.html
[18]: https://www.51qianduan.com/article/view/4111.html

[19]: https://fontawesome.com/icons
[20]: https://weus.cjlus.eu.org/hitokoto-api/?format=js&amp;amp;charset=utf-8

