---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# 复原 BMR 系统卷映像

如果需要从 {{site.data.keyword.backup_full}} 复原裸机映像备份，可以从 BMR 急救内核系统快速进行复原。通过 BMR，无需可引导的操作系统即可复原系统。这对于操作系统不再可用或系统中的驱动器已更换的情况非常有用。

## 启动 BMR 急救内核系统

可通过 {{site.data.keyword.slportal}} 访问 BMR 急救内核系统。
1. 登录到 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}/catalog/){:new_window}，然后单击左上角的**菜单**图标。选择**经典基础架构**。

   或者，可以登录到 [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}。
2. 单击**存储** > **备份**以显示具有备份服务的服务器。
3. 单击保险库旁边的**箭头**。
4. 单击**启动裸机复原**。此操作会启动一个事务，其需要几分钟时间来完成。之后，您可以通过执行此处详细描述的步骤来访问服务器。系统完成引导过程时，会向您发送电子邮件。


## 从 BMR 急救内核复原

1. BMR 急救内核事务装入后，您可以选择通过两种不同的方式对其进行访问。
  - VNC 客户机、您的服务器的公共/专用 IP 地址，以及 {{site.data.keyword.slportal}} 中列出的密码
  - 您的 IPMI 卡的 KVM 控制台。这两种方式都很好用。
2. 首次登录到 BMR 急救内核时，您会看到语言选择屏幕。选择您的首选语言，然后单击**下一步**。
<br/>![图 1 - BMR 语言选择](/images/bmr1.png)<br/> 这将显示软件的许可协议。
3. 如果您接受这些条款，请选中相应的复选框，然后单击**下一步**以继续。<br/> 这将显示 {{site.data.keyword.backup_notm}} 系统复原主菜单。
4. 选择**复原我的系统**。
<br/>![图 2 - BMR 主菜单](/images/bmr2.png)
5. 此时将显示系统复原向导。选择**下一步**以继续。
<br/>![图 3 - BMR 向导](/images/bmr3.png)
6. 选择要从其进行复原的备份类型。选择 **EVault 软件**，然后单击**下一步**以继续。
7. 在**备份位置**屏幕上，选择保险库并输入保险库地址、帐号、用户名和密码。然后，单击**下一步**以继续。
<br/>![图 4 - 选择备份位置](/images/bmr4.png)
8. 下一个屏幕将在列表中显示您的系统。确保您的系统已突出显示，然后单击**下一步**。
<br/>![图 5 - 选择您的系统](/images/bmr5.png)
9. 在**备份作业选择**屏幕上，选择要从其进行复原的作业，然后单击**下一步**。
<br/>![图 6 - 选择复原点](/images/bmr6.png)
10. 从**选择复原点**菜单中，选择所需的复原点，然后单击**下一步**。
<br/>![图 8 - 选择复原点](/images/bmr8.png)
11. 选择源卷和目标卷。要将源复原到目标，请将源卷拖动到目标卷上。
<br/>![图 9 - 选择源卷和目标卷](/images/bmr9.png)
12. 在数据格式化或数据合并确认框上，可以从两个选项中进行选择。选择**格式化**来格式化磁盘以进行干净复原。如果要合并目标卷上的数据，请选择**合并**。
<br/>![图 10 - 选择合并](/images/bmr10.png)
13. 在源卷和目标卷主屏幕上，单击**下一步**。
14. 在复原计划摘要屏幕上，选中相应的复选框以接受计划，然后单击**下一步**。
<br/>![图 11 - 启动复原](/images/bmr11.png)
15. 此时将显示复原进度屏幕，其会显示复原期间的复原进度。
<br/>![图 12 - 复原进度](/images/bmr12.png)
16. 完成后，会显示一个通知窗口，告诉您复原已成功完成。单击**确定**。
17. 在复原进度屏幕上，单击**下一步**。
18. 在最终屏幕上，选中重新启动系统的复选框，然后选择**完成**，此时服务器会装入所复原的卷映像。现在，复原已完成。<br/>

  第一次执行此操作时，您可能会看到意外关机消息。对于此备份类型，这种情况完全正常，在首次引导后此问题即会消失。
  {:tip}
