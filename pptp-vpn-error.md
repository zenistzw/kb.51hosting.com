<!-- --- tag: faq windows vpn -->
<!-- --- title: VPN无法登录：错误741 本地计算机不支持所要求的数据加密 -->
# VPN无法登录：错误741 - 本地计算机不支持所要求的数据加密

使用vpn服务，登录后直接提示：错误741 - 本地计算机不支持所要求的数据加密类型

![](http://i1.51hosting.com/2014-09-01_18_01_vpn-error1.png)

###问题分析： 
遇到类似这样的问题，先查看反馈的信息，从返回的信息中可以看出来客户端设置的数据加密类型不支持服务端的加密类型。而在客户端建立vpn客户端的时候，会有一个安全选项，设置客户端连接服务端时候的加密类型。 

###问题解决： 
先双击打开vpn客户连接，点击“属性”按钮，进入vpn连接属性。

![](http://i1.51hosting.com/2014-09-01_18_01_vpn-error2.png)


在安全选项卡中，数据加密这类目中，选择“可选加密”即可。

![](http://i1.51hosting.com/2014-09-01_18_01_vpn-error3.png)