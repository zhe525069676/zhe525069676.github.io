
title: Mac下使用抓包工具--Charles进行抓包
date: 2017-08-14 17:20:00

# Mac下使用抓包工具--Charles进行抓包
----

<img src="/assets/images/charles/charles_logo.png" style="width: 50%;">

[官网地址](http://www.charlesproxy.com/)

## 破解教程

破解文件提取地址(4.1.4)：
[https://pan.baidu.com/s/1eRNYPxg](https://pan.baidu.com/s/1c2mz0YW)
密码：4stp

[其他版本看这里](http://charles.iiilab.com/)

#### 步骤

* 打开 Fidder，找到应用程序中的 Charles，右击显示包内容

<img src="/assets/images/charles/charles_step1.png" style="width: 50%;">

* 使用上面提取出来的破解文件替换charles.jar文件即可

<img src="/assets/images/charles/charles_step2.png" style="width: 50%;">

## 抓包原理

[某学姐带你了解抓包原理](http://mouxuejie.com/blog/2017-03-19/capture-package-principle/)

#### HTTP抓包

1、打开Charles；


2、保证手机和Mac在一个局域网，设置->无线网络->“你连接的网络”详情->代理设置->手动->输入Mac的IP地址和端口号8888；

<img src="/assets/images/charles/charles_step4.png" style="width: 50%;">

<img src="/assets/images/charles/charles_step5.png" style="width: 50%;">

3、当设备访问app接口时，在Charles会弹出确认选，选择Allow；

<img src="/assets/images/charles/charles_step3.png" style="width: 50%;">

效果如下:

<img src="/assets/images/charles/charles_step6.png" style="width: 50%;">

#### HTTPS抓包

1、菜单栏 Help -> SSL Proxying -> Install Charles Root Certificate，找到Charles Proxy CA 证书，双击打开证书信息页面，将 加密套接字协议层(SSL) 设置为始终信任；

<img src="/assets/images/charles/charles_step7.png" style="width: 50%;">

2、手机浏览器打开 http://charlesproxy.com/getssl 下载证书，最好使用类似UC之类的浏览器app访问，下载完成之后自动配置；

3、开启SSL代理，Proxy->SSL Proxying Setting，在Locations里面添加要使用SSL代理的网站，端口号输入443，如果需要匹配所有的HTTPS网站则输入 * 号即可。现在即可拦截Https的数据包。

<img src="/assets/images/charles/charles_step9.png" style="width: 50%;">

效果如下：

<img src="/assets/images/charles/charles_step8.png" style="width: 50%;">

#### 关于我 
QQ交流群:496946393 

邮箱: nh_zhe@163.com

[GitHub](https://github.com/zhe525069676)

[简书](http://www.jianshu.com/users/550d52af9d72/latest_articles)

[个人博客](http://www.zheblog.com)




	


