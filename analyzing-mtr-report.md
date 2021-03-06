<!-- --- tag: faq 网络 网速 延迟 掉包 mtr 云主机 -->
<!-- --- title: 如何分析WinMTR/MTR的报告结果? -->

# 如何分析WinMTR/MTR的报告结果?

如果您第一次使用WinMTR/MTR或者您还没有下载WinMTR/MTR工具，请先点击[如何用WinMTR分析/排查网络延迟与掉包](http://kb.51hosting.com/2012-11-16-why-is-my-site-slow) 了解WinMTR。 或直接点击[下载WinMTR/MTR](http://downloads.sourceforge.net/project/winmtr/WinMTR-v092.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fwinmtr%2Ffiles%2F&ts=1353040732&use_mirror=jaist)

## 验证数据包丢失

在分析WinMTR/MTR输出结果时，您需要查看两件事情：丢包和延迟。首先，我们来讨论丢包。如果您在任何一个节点看到有掉包，这可能表示这个特定的路由节点有问题。然而，有些服务提供商会限制WINMTR/MTR工具发送的ICMP传输。这会对数据包丢失造成错觉，但事实上并未丢包。要确认您看到的数据包丢失是否是由于服务提供商限制造成的，您可以查看随后的一跳路由节点。如果该跳显示丢失0%，那么您可以肯定
是ICMP限制，实际未丢包。
看下面的例子：

![](http://i1.51hosting.com/2014-10-24_10_38_MTR1.png)

在这种情况下，从第一跳到第二跳的丢包可能是由于第二跳路由ICMP限制导致的。因为剩余的8个路由节点都没有丢包。这种情况下，采取掉包最少的节点作为它实际的丢包率。

再考虑一个例子：

![](http://i1.51hosting.com/2014-10-24_11_18_mtr2.png)


在这种情况下，你会看到第三跳和第四跳之间有60%的丢包。您可以假设这是由于路由设备限制导致的丢包。然而，您可以看到最后一跳是显示40%的丢包。但产生不同的丢包结果时，始终采用最后一跳的丢包率。

有些丢包可能产生在路由返回的时候。数据包可以正确无误地到达目的地，但未正常返回。这也会计算在丢包率中，但您从WinMTR/MTR结果报告中很难分辨。<strong>因此，在任何时候您都需要同时收集两个方向的WinMTR/MTR结果报告。</strong>