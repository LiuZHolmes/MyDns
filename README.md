# MyDns
//在自己的电脑上搭建DNS服务器并使用  
//环境：SYSU-E，需要IPv6(ISATAP)

&emsp;由于之前一个师兄租的一个服务器挂了，想上谷歌的心又按耐不住，就试试查了查一些科学上网的资料，幸好在贴吧上有大佬指导，自己搭建了一个DNS服务器，成功完成目标。  

&emsp;首先要了解的是无法科学上网的原因：[域名服务器缓存污染](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%BC%93%E5%AD%98%E6%B1%A1%E6%9F%93 "维基百科")

&emsp;简单的说，就是GFW通过将域名解析为无法访问的不正确的IP地址，使一般用户无法直接访问某些相应的网站。一般的域名解析的服务器（即DNS服务器）均无法正确解析我们要访问的网站的正确IP地址，而我们要做的就是自己搭建一个DNS服务器，让本机上网时自己来做域名解析，成功访问正确的IP地址。（对IP地址和网关等不知道如何查看可以在命令行输入ipconfig或ipconfig/all）

&emsp;在这里要介绍一个忽略投毒的工具[Pcap_DNSProxy](https://github.com/chengr28/Pcap_DNSProxy "Github")。它是chengr28用C++开发的工具，非常方便。  

&emsp;首先要安装[WinCap](http://www.winpcap.org/install/default.htm)，然后再安装Pcap_DNSProxy。

&emsp;装好后这个工具以后按照对应系统和位数选择不同的版本，打开后有这样的画面（以管理员身份运行ServiceControl.bat）：

&emsp;![image](https://github.com/LiuZHolmes/MyDns/blob/master/ReadmePictures/Pcap_DNSProxy.jpg)

&emsp;运行之前建议先将本机的IP地址设成127.0.01（有IPv6的话也建议同时改成::1）。

&emsp;然后先按1安装服务，以后改动了目录下的配置文件需要重启服务按5。

&emsp;安装好服务应该就可以上Google了。

&emsp;如果对同一局域网中的设备也要以此为DNS服务器，将设备的DNS服务器改成本机在局域网中的IP地址，同时将修改Config.ini文件中的一个参数（如下图）即可。

&emsp;![image](https://github.com/LiuZHolmes/MyDns/blob/master/ReadmePictures/Config.jpg)

&emsp;若是要将本机DNS服务器共享，则需要路由器的端口转发功能。以本人使用的JI路由（据说是最方便的）为例：将外网的53号端口与内部的53号端口建立转发UDP协议。其他设备所要设置的DNS服务器地址即为你的WAN口地址。
	
PS：科学上网的IPv6相关

&emsp;由于当前使用的是SYSU的教育网，它有提供IPv6的服务，而一些IPv6的地址并没有受到DNS投毒的污染，故在使用IPv6的时候会自带一部分的科学上网属性。

&emsp;对于SYSU，要使用IPv6的话只需要选择教育网IPv6的双栈接入（DHCPv6）方式即可。

&emsp;[点这里测试IPv6](http://www.test-ipv6.com/)

Enjoy!

　　
