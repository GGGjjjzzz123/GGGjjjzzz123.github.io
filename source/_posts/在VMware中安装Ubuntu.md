
---
title: 在VMware中安装Ubuntu
date: 2025-03-20
categories: [技术文章]
tags: [VMware, Ubuntu, 虚拟机]
---

## 配置Ubuntu
1. 打开“VMware Workstation”软件，选择创建虚拟机，随后进入新建虚拟机向导
2. 选择第一个“典型”，点击“下一步”

<!-- 这是一张图片，ocr 内容为：VMWARE WORKSTATION 园回回名包口 查看(V) 虚拟机(M)选项卡(T)帮助(H) 文件(F)编辑(E) 库 X 主页 我的计算机 在此处键入内容进行搜索 我的计算机 其他LINUX5.X内核64位 WORKSTATIONPRO17 CENTOS764位 卫 连接远程服务器 打开虚拟机 创建新的虚拟机 VMWARE -->
![](/images/vmware-ubuntu/image_001_1748605416332-bae73e42-00b3-4dd0-8d3b-abcd315976d3.png)

3. 选择“稍后安装操作系统”，点击下一步

<!-- 这是一张图片，ocr 内容为：新建虚拟机向导 安装客户机操作系统 虚拟机如同物理机,需要操作系统.您将如何安装客户机操作系统? INSTALL FROM: INSTALLER DISC: 无可用驱动器 INSTALLER DISC IMAGE FILE(ISO): D:\LINUXLCENTOS-7-X86_64-DVD-2003.ISO BROWSE... I WILL INSTALL THE OPERATING SYSTEM LATER. THE VIRTUAL MACHINE WILL BE CREATED WITH A BLANK HARD DISK. 下一步(N) 取消 帮助 <上一步(B) -->
![](/images/vmware-ubuntu/image_002_1748605525354-99e28adf-4fdd-4e74-9e26-eb85e926accd.png)

4. 选择客户机操作系统为“Linux”，版本为“Ubuntu 64位”，点击下一步

<!-- 这是一张图片，ocr 内容为：新建虚拟机向导 选择客户机操作系统 此虚拟机中将安装哪种操作系统? GUEST OPERATING SYSTEM MICROSOFT WINDOWS LINUX VMWARE ESX OTHER VERSION UBUNTU64位 下一步(N) <上一步(B) 帮助 取消 -->
![](/images/vmware-ubuntu/image_003_1748607297930-89fde686-1b69-43c8-acbc-c033f14f3746.png)

5. 虚拟机名称默认即可，选择虚拟机文件存储位置（注意：一定要单独新建一个文件夹来存）

<!-- 这是一张图片，ocr 内容为：新建虚拟机向导 命名虚拟机 您希望该虚拟机使用什么名称? VIRTUAL MACHINE NAME: UBUNTU64位 LOCATION: D://LINUX\UBUNTU BROWSE... THE DEFAULT LOCATION CAN BE CHANGED AT EDIT > PREFERENCES. 下一步(N) <上一步(B) 取消 -->
![](/images/vmware-ubuntu/image_004_1748607283503-a9f5f6c1-4070-4dd4-8f5b-d71e5de327b2.png)

6. 设置最大磁盘大小20G（默认），选择“将虚拟磁盘存储为单个文件”

<!-- 这是一张图片，ocr 内容为：新建虚拟机向导 指定磁盘容量 磁盘大小为多少? 虚拟机的硬盘作为一个或多个文件存储在主机的物理磁盘中.这些文件最初很小,随着 您向虚拟机中添加应用程序,文件和数据而逐渐变大. 20.0 最大磁盘大小(GB)(S): 针对UBUNTU 64位的建议大小:20 GB 将虚拟磁盘存储为单个文件(O) 将虚拟磁盘拆分成多个文件(M) 拆分磁盘后,可以更轻松地在计算机之间移动虚拟机,但可能会降低大容量磁盘的 性能. 上一步(B) 下一步(N)> 取消 帮助 -->
![](/images/vmware-ubuntu/image_005_1748607579897-b085dc47-7454-47c7-ba9a-cc9ec4605521.png)

7. 点击“自定义硬件”

<!-- 这是一张图片，ocr 内容为：新建虚拟机向导 已准备好创建虚拟机 单击'完成创建虚拟机.然后可以安装UE 安装UBUNTU64位. THE VIRTUAL MACHINE WILL BE CREATED WITH THE FOLLOWING SETTINGS: 名称: UBUNTU64位 位置: D:\LINUX|UBUNTU 版本: WORKSTATION 17.5.X 操作系统: UBUNTU64位 硬盘: 20 GB 内存: 4096 MB 网络适配器: NAT 2个CPU内核,CD/DVD,USB控制器,声卡 其他设备: SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS CUSTOMIZE HARDWARE... <上一步(B) 完成 取消 -->
![](/images/vmware-ubuntu/image_006_1748607608217-038062ef-f04c-42e1-9007-99a16a4810bc.png)

8. 选中“新CD/DVD”，在连接中选择“使用ISO映像文件”，在浏览中选择存放Ubuntu映像文件的地址，点击关闭，再点击完成

<!-- 这是一张图片，ocr 内容为：硬件 设备状态 摘要 设备 已连接(C) 4 GB 处理器 2 启动时连接(O) 自动检测 新CD/DVD(SATA) 网络适配器 连接 NAT USB控制器 存在 使用物理驱动器(P): 自动检测 声卡 自动检测 显示器 自动检测 使用ISO映像文件(M): D:\LINUX/UBUNTU-22.04.5-DES 浏览(B)... 高级(V)... 移除(R) 添加(A)... 帮助 关闭 -->
![](/images/vmware-ubuntu/image_007_1748607721896-1794f1d5-5a68-4cf1-aaff-2477fc4bf4e4.png)

9. Ubuntu已经配置好了

<!-- 这是一张图片，ocr 内容为：向 UBUNTU 64 - VMWARE WORKSTATION 编辑(E) 查看(V) 虚拟机(M)选项卡(T) 帮助(H) 文件(F) 库 UBUNTU 64位 主页 我的计算机 在此处键入内容进行搜索 UBUNTU64位 我的计算机 向句句 其他LINUX5.X内核64位 开启此虚拟机 CENTOS764位 编辑虚拟机设置 UBUNTU64位 设备 内存 4 GB 2 处理器 硬盘(SCSI) 20 GB 正在使用文件D:... CD/DVD(SATA) NAT 网络适配器 存在 USB控制器 自动检测 声卡 显示器 自动检测 虚拟机详细信息 状态:已关机 描述 配置文件:D://LINUX\UBUNTU/UBUNT 在此处键入对该虚拟机的描述. 64位.VMX 硬件兼容性:WORKSTATION 17.5.X虚拟 机 主IP地址:网络信息不可用 -->
![](/images/vmware-ubuntu/image_008_1748607780468-92195de4-61d8-4bba-8f84-045ce2551670.png)

## 安装Ubuntu
1. 选中刚刚配置的CentOS7，然后点击右边控制台中的“开启次虚拟机”。（开机失败可能是因为权限不够，关闭VMware，重新以管理员的身份运行）

<!-- 这是一张图片，ocr 内容为：UBUNTU 64 - VMWARE WORKSTATION 文件(F)编辑(E) 查看(V) 虚拟机(M)选项卡(T) 帮助(H) 库 UBUNTU 64位 主页 我的计算机 在此处键入内容进行搜索 UBUNTU64位 我的计算机 包包包 其他LINUX5.X内核64位 开启此虚拟机 CENTOS764位 编辑虚拟机设置 UBUNTU64位 设备 4 GB 圈内存 处理器 2 硬盘(SCSI) 20 GB 正在使用文件D:... CD/DVD(SATA) 网络适配器 NAT 存在 USB控制器 自动检测 声卡 自动检测 显示器 虚拟机详细信息 状态:已关机 描述 配置文件:D:\LINUX\UBUNTU/UBUNT 在此处键入对该虚拟机的描述. 64位.VMX 硬件兼容性:WORKSTATION 17.5.X虚拟 机 主IP地址:网络信息不可用 -->
![](/images/vmware-ubuntu/image_009_1748607846673-0cd0a5e3-88c6-4eb7-96e6-38be0768b98f.png)

2. 选择第一个选项

<!-- 这是一张图片，ocr 内容为：我的计算机 介主页 UBUNTU 64位 GNUGRUB VERSION 2.06 TRY OR INSTALL UBUNTU UBUNTU (SAFE GRAPHICS) OEM INSTALL (FOR MANUFACTURERS) TEST MEMORY USE THE T AND - KEYS TO SELECT WHICH ENTRY IS HIGHLIGHTED. 'E' TO EDIT THE COMMANDS THE SELECTED OS, PRESS ENTER TO BOOT TH BEFORE BOOTING OR 'C' -LINE. FOR A COMMAND-LI THE HIGHLIGHTED ENTRY WILL BE A AUTOMATICALLY IN 21S. EXECUTED -->
![](/images/vmware-ubuntu/image_010_1748607936163-bf8539f1-2284-45c9-92a3-1d9e4cdf572d.png)

3. 启动之后出现安装界面

<!-- 这是一张图片，ocr 内容为：我的计算机 主页 UBUNTU 64位 MAY 30 20:26 SAJAIDUHTE BURES BOAHTIN HRVATSKI ISLENSKA LTALIANO KURDI LATVISKI LIETUVISKAI MAGYAR NEDERLANDS NO LOCALIZATION(UTF-8) SAJAIDUHTTIT UBUNTU GEAHCCALUBUNTU NORSK BOKMAL NORSK NYNORSK OCCITAN YOU CAN TRY UBUNTU WITHOUT MAKING ANY CHANGES TO YOUR COMPUTER, DIRECTLY FROM THIS CD. POLSKI OR IF YOU'READY.YOU CANINSTALL UBUNTU ALONGSIDE (OR INSTEAD OF YOUR CURRENT OPERATING PORTUGUES SYSTEM. THIS SHOULDN'T TAKE TOO LONG. PORTUGUES DO BRASIL ROMANA SAMEGILLII 机内部单击或按CTRL+G. -->
![](/images/vmware-ubuntu/image_011_1748608000677-2626f792-4512-42d4-a956-28f229239e4c.png)

4. 语言选择“简体中文”，选择“安装Ubuntu”

<!-- 这是一张图片，ocr 内容为：我的计算机 UBUNTU64位X 主页 MAY 30 20:29 U 安装 欢迎 SLLY BEUK GGGOLOM BOUC BWILALU CLC 试用UBUNTU 安装UBUNTU 的只 COCAGRI 您可以直接从此CD尝试UBUNTU,而不用对您的电脑作任何更改. 10号原 中文(简体) 如果您已经准备完毕,您可以与现有系统并存(或者替代)方式将UBUNTU安装到您的电脑上. 此过程无需耗时太久. 中文(繁体) 日本语 标移动性,视频和性能.请答灵客户机操作系统,单击'安 单击虚拟屏暮 VMWARE -->
![](/images/vmware-ubuntu/image_012_1748609716441-c276047f-e0cd-40e5-9aa1-711fe3462338.png)

5. 键盘布局默认选择“Chinese”，点击继续

<!-- 这是一张图片，ocr 内容为：UBUNTU64位 我的计算机 主页 U MAY 30 20:32 安装 键盘布局 选择您的键盘布局: BELARUSIAN CHINESE CHINESE-HANYU PINYIN(WITH ALTGR DEAD KEYS) BELGIAN CHINESE-MONGOLIAN(BICHIG) BERBER(ALGERIA,LATIN) CHINESE-MONGOLIAN(GALIK) BOSNIAN CHINESE-MONGOLIAN(MANCHU GALIK) BRAILLE CHINESE-MONGOLIAN(MANCHU) BULGARIAN CHINESE-MONGOLIAN(TODO GALIK) BURMESE CHINESE CHINESE-MONGOLIAN(TODO) CHINESE-MONGOLIAN(XIBE) CROATIAN CHINESE-TIBETAN CZECH CHINESE-TIBETAN(WITH ASCIL NUMERALS) DANISH CHINESE-UYGHUR DHIVEHI DUTCH DZONGKHA ENGLISH(AUSTRALIAN) 在这里输入以测试您的键盘 探测键盘布局 后退(B) 继续 退出(Q) VMWARETOOLS具有很多功能,能改善鼠标移动性,视须和性能.请登录客户机操作系统,单击"安装 单击虚拟屏幕 不要提醒我 安装TOOLS 以后提醒我 可发送按键 TOOLS" -->
![](/images/vmware-ubuntu/image_013_1748609773193-9541ee58-e38d-4a11-bd2e-3aec96ac3585.png)

6. 选择“正常安装”，其他选项选择“为图形或...”，点击继续

<!-- 这是一张图片，ocr 内容为：我的计算机 介主页 UBUNTU 64位 X MAY 30 20:34 安装 更新和其他软件 您希望先安装哪些应用? 正常安装 网络浏览器,工具,办公软件,游戏和媒体播放器. 最小安装 网络浏览器和基本工具 其他选项 安装UBUNTU时下载更新 这能节约安装后的时间. 为图形或无线硬件,以及其它媒体格式安装第三方软件 此软件及其文档遵循许可条款.其中一些是专有的. 退出(O) 后退(B) 继续 -->
![](/images/vmware-ubuntu/image_014_1748609904923-d3bbd18f-83a0-49db-a3a8-29c29248d313.png)

7. 安装类型，记得勾选“清除...”，点击现在安装，再点击继续

<!-- 这是一张图片，ocr 内容为：安装 安装类型 这台计算机似乎没有安装操作系统.您准备怎么做? 清除整个磁盘并安装UBUNTU 注意:这会删除所有系统里面的全部程序,文档,照片,音乐和其他文件. 高级特性... 尚未选择任何项目 其他选项 您可以自己创建,调整分区,或者为UBUNTU选择多个分区. 后退(B) 退出(Q) 现在安装(1) -->
![](/images/vmware-ubuntu/image_015_1748609968267-45542283-9077-42e7-9de1-f1b0e29a422e.png)

8. 地区选择上海，点击继续

<!-- 这是一张图片，ocr 内容为：安装 您在什么地方? SHANGHAI 后退(B) 继续 -->
![](/images/vmware-ubuntu/image_016_1748610013167-c67ac2c9-1266-4729-a3ac-0fe7aab2f5fa.png)

9. 输入相关信息，点击继续（密码：gjz）

<!-- 这是一张图片，ocr 内容为：安装 您是谁? 您的姓名: GJZ GJZ-VIRTUAL-MACHINE 您的计算机名: 与其他计算机联络时使用的名称. 选择一个用户名: GJZ 选择一个密码: 密码强度:合理 确认您的密码: 自动登录 登录时需要密码 使用ACTIVEDIRECTORY 您将在下一步中输入域和其他详细信息. 继续 后退(B) -->
![](/images/vmware-ubuntu/image_017_1748610076458-02b93f23-6fb5-444b-8f79-503fff6173b3.png)

10. 进行安装（过程巨慢）

<!-- 这是一张图片，ocr 内容为：安装 SKIP 正在完成文件复制... -->
![](/images/vmware-ubuntu/image_018_1748610100399-8cd95150-f12b-49ec-bec1-8d8f2b0d297a.png)

11. 完成！

<!-- 这是一张图片，ocr 内容为：我的计算机 UBUNTU64位 主页 X X 活动 5月31日04:55 ZH 主目录 .内部单击或按CTRL+G. -->
![](/images/vmware-ubuntu/image_019_1748611186899-d9e719ea-ec3b-423c-8a4f-5b2b167a06a2.png)

换源

<!-- 这是一张图片，ocr 内容为：软件和更新 活动 10月25日03:07 软件和更新 X 身份验证 开发者选项 其它软件 附加驱动 更新 UBUNTU软件 UBUNTUPRO 可从互联网下载 CANONICAL支持的自由和开源软件(MAIN) 选择下载服务器 社区 设备 MIRRORS.HUST.EDU.CN 选择最佳服务器(S) O 因版 MIRRORS.JCUT.EDU.CN MIRRORS.JLU.EDU.CN 源代 MIRRORS.JXUST.EDU.CN 下载自: MIRRORS.SDU.EDU.CN MIRRORS.SOHU.COM MIRRORS.TUNA.TSINGHUA.EDU.CN 可从光驱车 MIRRORS.XITU.EDU.CN INST MIRRORS.YUN-IDC.COM 官方 版权 协议: HTTPS 选择服务器(S) 取消(C) 六 还原(V) 关闭(C) -->
![](/images/vmware-ubuntu/image_020_1761305476128-7a06ac15-f8a9-4de8-bb7a-8ca6ebb676d2.png)

Ubuntu粘贴复制

1、更换国内源（阿里）

2、sudo apt-get update

3、sudo apt-get upgrade

4、sudo apt-get  install open-vm-tools

5、sudo apt-get install open-vm-tools-desktop

