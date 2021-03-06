<!-- --- tag: faq 网络 网速 延迟 掉包 mtr -->
<!-- --- title: 如何用WinMTR分析/排查网络延迟与掉包? -->
#如何用WinMTR分析/排查网络延迟与掉包?
影响网速延迟/掉包的问题错综复杂，不能一概而论。数据包在网络中传递过程中也会经过多个节点到达目的地，其中数据包通过何种协议或选择何种路径去往目的地都有关系（好比你开车去往目的地有多条路可到达，选择哪条线路，多少红灯，车辆拥堵都会影响到达目的地速度），数据包传递也是如此，整个过程不是谁或某个机构能完全控制的，即使相同地点在不同时间也会有不同的延时与丢包，今天ping反应情况是120ms，明天可能会340ms，所以数据在特定时间和环境才有参考价值。还有些其他因素诸如网页代码不优，被病毒攻击造成服务器负担等也会影响客户端访问速度。


##WinMTR/MTR
WinMTR/MTR这款工具是非常有用的工具，反应当时主机网络的延迟，跳点，丢包等情况。

我们重点关心的是数据包在我们线路上的情况，如果你一直认为网速慢和我们有关，请使用该工具提取数据报表附于工单提交向我们反应，我们工程师来分析是否在可控范围内作出优化线路等调整。

##安装WinMTR/MTR 

###Windows系统

[下载WinMTR/MTR](http://downloads.sourceforge.net/project/winmtr/WinMTR-v092.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fwinmtr%2Ffiles%2F&ts=1353040732&use_mirror=jaist)

###Debian和Ubuntu系统

确认所需安装包已经安装，随后安装WinMTR/MTR

1. apt-get update
2. apt-get upgrade
3. apt-get install mtr-tiny

### CentOS和Fedora系统

确认所需安装包已经安装，随后安装WinMTR/MTR

1. yum update
2. yum install mtr

### Windows版本使用方法
1. 解压文件
2. 在 host输入: 51hosting.com (请用你要测试的网站的域名或者ip地址替换51hosting.com)
3. 点start后等5分钟
4. 选择Export to TEXT
5. 把导出报告提交工单附件中

#### WinMTR测试结果名词解释
1. Copy Text to clipboard   - 将结果以文本形式复制到剪贴板
2. Copy HTML to clipboard - 将结果以HTML形式复制到剪贴板
3. Export TEXT  - 将结果以文本形式导出
4. Export HTML - 将结果以HTML形式导出
5. Options - 设置 
6. Hostname:到目的服务器要经过的每个节点主机IP或名称 。
7. Nr:经过节点的数量;以上图洛杉矶美国机房为例子:一共要经过12个节点,其中第一个是当地宽带商的网关。
8. Loss%:ping 数据包回复失败的百分比;由此可判断那个节点(线路)出现故障,是服务器所在机房还是国际路由干路。 
9. Sent:已经传送的数据包数量 。
10. Recv:成功接收的数据包数量 。
11. Best:回应时间的最小值 。
12. Avrg:平均回应时间 。
13. Worst:回应时间的最大值。 
14. Last:最后一个数据包的回应时间。

##### 举例说明
1. WinMTR的使用方法如下：
双击WinMTR.exe运行，打开后，我们可以看到Host一栏的文本框，在Host文本框内输入您要追踪的IP或者域名，再按 Start ，此时就可以看到如下图所示的 tracert 与 Ping 的结果，图例如下：

<center>![](http://i1.51hosting.com/2013-12-25_12_43_winmtrtest.png)</center>

测试结束后，我们可以将结果导出：

Hostname：到目的服务器要经过的每个节点主机IP或名称 。

Nr：经过节点的数量；以上图洛杉矶美国KT机房为例子：一共要经过12个节点，其中第一个是当地宽带商的网关。

Loss%：ping 数据包回复失败的百分比；由此可判断那个节点（线路）出现故障，是服务器所在机房还是国际路由干路。 (其中图中倒数第2跳显示100%丢失，那是正常的因为有些节点禁ping后是无法取得数据的。

Sent：已经传送的数据包数量

Recv：成功接收的数据包数量

Best：回应时间的最小值

Avrg：平均回应时间

Worst：回应时间的最大值

Last：最后一个数据包的回应时间

不同的网络情况，MTR都会返回不同的结果。您需要对MTR结果做一个正确的分析。

<strong>请阅读[如何分析WinMTR/MTR的报告结果? ](http://kb.51hosting.com/analyzing-mtr-report)</strong>


