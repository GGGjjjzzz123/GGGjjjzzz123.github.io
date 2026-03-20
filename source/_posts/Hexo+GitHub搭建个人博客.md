---
title: Hexo+GitHub搭建个人博客
date: 2025-03-20  # 发布日期
categories: [技术文章]  # 分类
tags: [Hexo, GitHub]  # 标签
---

### 一、前期知识
#### 什么是Hexo
+ Hexo 是一个用 JavaScript 编写、运行在 Node.js 环境中的静态博客框架

#### 为什么用Hexo必须要用到Node.js
+ 因为 Hexo 不是一个独立的 exe 软件，也不是一个编译好的 Windows 桌面程序。它本质上是一套用 JavaScript 编写的程序。既然是 JavaScript 写的，而且不是浏览器里运行的前端页面代码，那它就需要一个"浏览器之外的 JavaScript 运行环境"来执行。这个运行环境就是 Node.js。Hexo 这个具体工具本身，就是用 Node.js 技术栈写出来并发布在 npm 生态里的。
+ Hexo 在工作时并不只是简单显示几篇文章，它会做一系列处理，这些处理都依赖 Node.js 环境来完成。比如：

你写的 Markdown 文章要被读取。  
	主题模板要被解析。  
	配置文件要被加载。  
	文章内容要被渲染成 HTML。  
	静态资源要被整理复制。  
	本地预览服务器要被启动。  
	插件系统要被加载。

这些动作本质上都是本地程序行为，不是浏览器自动帮你做的。Hexo 本身就是负责做这些事情的程序，而 Node.js 就是让这个程序能跑起来的底层运行环境。

#### 为什么要部署到GitHub
#### 什么是JavaScript
+ JavaScript 是一种编程语言。最直接地说，它是让计算机按照你写的规则去处理数据、执行逻辑、响应用户操作的一套语言体系。
+ HTML 负责页面有什么内容，CSS 负责页面长什么样，JavaScript 负责页面动起来、能交互、能处理逻辑。
+ 现在的 JavaScript 早就不只是在网页里用了。它还能写服务器程序、命令行工具、桌面应用、移动端应用，甚至能做一些自动化脚本和工程化工具。
+ 程序语言不是写出来就自动能跑，必须有一个执行环境。JavaScript 最经典的执行环境有两种。
    - 第一种是浏览器
        * 比如 Chrome、Edge、Firefox。这些浏览器内部都带有 JavaScript 引擎。你打开网页时，浏览器会读取网页里的 JavaScript 代码并执行它。所以网页中的点击事件、动画、表单校验之类的功能，都是浏览器在执行 JavaScript。
    - 第二种是 Node.js
        * Node.js 可以理解成一个让 JavaScript 脱离浏览器也能运行的环境。这样 JavaScript 就不再只能控制网页，还能在本地电脑或服务器上读写文件、启动服务、处理命令行参数、搭建后端程序。前面说 Hexo 依赖 Node.js，本质上就是因为 Hexo 是用 JavaScript 写的，但它不是在浏览器里运行，而是在本地命令行环境里运行，所以需要 Node.js 来执行。

#### 什么是Node.js
+ Node.js 让 JavaScript 不只在浏览器里运行，也能在本地和服务器运行。

#### 什么是Git
+ Git是与GitHub仓库进行交互的终端

### 二、环境准备
#### 下载Node.js、vscode、git
#### 检查node是否安装成功，并修改npm源（以管理员身份打开命令提示符）
<!-- 这是一张图片，ocr 内容为：C:\USERS\GJZ>NODE -V V18.19.0 C:\USERS\GJZ>NPM -V 10.2.3 C:\USERS\GJZ>GIT -V 2.49.0.WINDOWS.1 GIT VERSION C:\USERS\GJZ> -->
![](/images/hexo-github-blog/node-install.png)

> npm：是Node Package Manager的缩写，是Node.js生态里最核心的包管理工具。
>
> 修改npm源：把npm下载软件包时默认连接的服务器地址，改成另一个镜像地址
>

+ 下面查看npm源为官方源

<!-- 这是一张图片，ocr 内容为：C:\USERS\GJZ>NPM CONFIG GET REGISTRY HTTPS://REGISTRY.NPMJS.ORG/ -->
![](/images/hexo-github-blog/npm-registry.png)

+ 修改为淘宝镜像源，并验证

<!-- 这是一张图片，ocr 内容为：C:\USERS\GJZ>NPM CONFIG : T REGISTRY HTTPS://REGISTRY.NPMMIRROR.COM/ SET RE C:\USERS\GJZ>NPM CONFIG GET REGISTRY HTTPS://REGISTRY.NPMMIRROR.COM/ -->
![](/images/hexo-github-blog/npm-taobao.png)

> 之前常用的淘宝镜像源地址改为[https://registry.npmmirror.com/](https://registry.npmmirror.com/)
>

#### 安装hexo-cli
<!-- 这是一张图片，ocr 内容为：C:\USERS\GJZ>NPM INSTALL HEXO-CLI -G ADDED 53 PACKAGES IN 30S 14 PACKAGES ARE LOOKING FOR FUNDING NPM FUND FOR DETAILS RUN NPM NOTICE NPM NOTICE NEW MAJOR VERSION OF NPM AVAL 1 AVAILABLE! 10.2.3 -> 11.11.1 NPM NOTICE CHANGELOG: HTTPS://GITHUB.COM/NPM/CLI/RELEASES/TAG/V11.11. UNPM NOTICE RUN NPM INSTALL -G NPM@11.1 TO UPDATE! NOTICE NPM -->
![](/images/hexo-github-blog/hexo-cli-install.png)

> -g：为全局安装，hexo-cli被安装在npm的全局目录里，安装的目录如下
>
> <!-- 这是一张图片，ocr 内容为：@> ... GJZ > APPDATA > R 在NPM中搜索 ROAMING>NPM GJZ 排序 三查看 预览 大小 类型 修改日期 名称 文件夹 2026/3/16 14:28 NODE MODULES 1 KB 文件 2026/3/16 14:28 HEXO 1 KB WINDOWS命令脚本 2026/3/16 14:28 HEXO.CMD 1 KB 2026/3/16 14:28 WINDOWS POWERSHE... HEXO.PS1 -->
![](/images/hexo-github-blog/hexo-cli-dir.png)
>
> hexo-cli：是Hexo的命令行工具（cli是Command Line Interface的缩写，意思是命令行界面），让系统识别"hexo"这个命令
>

+ 验证是否安装成功

<!-- 这是一张图片，ocr 内容为：C:\USERS\GJZ>HEXO 一V HEXO-CLI:4.3.2 UNDEFINED OS:WIN32 10.0.26200 NODE:18.19.0 8.10.0 ACORN: ADA: 2.7.2 ARES:1.20.1 BASE64:0.5.0 BROTLI:1.0.9 CJS_MODULE_LEXER:1.2.2 CLDR:43.1 ICU:73.2 LLHTTP:6.011 MODULES:108 NAPI:9 NGHTTP2:1.57.0 NGHTTP3:0.7.0 NGTCP2:0.8.1 OPENSSL:3.0.12+QUIC SIMDUTF:3.2.18 TZ:2023C UNDICI:5.26.4 UNICODE:15.0 UV:1.44.2 UVWASI:0.0.19 V8: 10.2.154.26-NODE.28 ZLIB: 1.2.13.1-MOTLEY -->
![](/images/hexo-github-blog/hexo-version.png)

### 二、连接GitHub
#### 创建github仓库，用来存放博客编译后的静态代码，仓库必须设置公共，这样才能访问到博客
<!-- 这是一张图片，ocr 内容为：白 O GGG JZZ123 / GGGGILIZZ123.GITHUBIO + 请键入(门去搜索 田 您设置 安全 0 68 洞察 操作 代码 R 议题 项目 拉取请求 WIKI 星标 0 GGGIIIZZZ123.QITHUB.IO 公共 取消关注 关于 京 0标签 添加文件 代码 30 1分支( 转到文件 MAIN 博客演示,用于存放项目文档,理论学 GGGGJIJZZ123 ADD PROJECT DESCRIPTION TO README 4次见交 86A366D-昨天 习文档,学科文档 GGGIJZZZZZ123-GITHUB-IO.VERCEL.APP 11个月前 SITE UPDATED:2025-04-20 1932:10 2025/04/20/HELLO-WORLD 中 自述文件 11个月前 SITE UPDATED:2025-04-20 19:00:22 ARCHIVES 活动 11个月前 SITE UPDATED 2025-04-20 1900 22 金0星标 R 1关注 11个月前 SITE UPDATED:2025-04-20 19:00:22 FANCYBOX 梦0复刻 11个月前 SITE UPDATED:2025-04-20 19:00:22 JS 发行版 昨天 ADD PROJECT DESCRIPTION TO README README.MD 未发布任何版本 11个月前 INDEX.HTML SITE UPDATED:2025-04-20 19:32:10 创建发行版 中自述文件 部署 GITHUB-PAGES 阶天 该网站用于上传各种文档,包括项目文档,学科文档,理论学习文档 PRODUCTION 昨天 +2个部若 软件包 未发布软件包 发布软件包 贡献者1 -->
![](/images/hexo-github-blog/github-repo.png)

> 注意仓库的命名规定！！
>

#### git安装完成后，打开git bash，检查git配置，配置用户名和邮箱
<!-- 这是一张图片，ocr 内容为：GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 GIT CONFIG -L DIFF.ASTEXTPLAIN.TEXTCONV-ASTEXTPLAIN FILTER.LFS.CLEAN-GIT-LFS CLEAN -- %F FILTER.LFS.SMUDGE-GIT-LFS SMUDGE -- %F FILTER.LFS.PROCESS-GIT-LFS FILTER-PROCESS FILTER.LFS.REQUIRED-TRUE HTTP.SSLBACKEND-SCHANNEL CORE.AUTOCRLF-TRUE CORE.FSCACHETRUE CORE.SYMLINKSFALSE PULL.REBASEFALSE CREDENTIAL.HELPEREMANAGER CREDENTIAL.HTTPS://DEV.AZURE.COM.USEHTTPPATH-TRUE INIT.DEFAULTBRANCHMASTER USER.NAMEGGGJJZZZ123 USER.EMAIL-GJZ12233@GMAIL.COM -->
![](/images/hexo-github-blog/git-config.png)

#### 连接GitHub
+ 在git中输入命令生成ssh公钥，此公钥用于计算机连接GitHub，一路回车不设置密码（也可以设置）

<!-- 这是一张图片，ocr 内容为：IGJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 I$ SSH-KEYGEN -T RSA -C GJZ1223330GMAIL.COM GENERATING PUBLIC/PRIVATE RSA KEY PAIR. ENTER FILE IN WHICH TO SAVE THE KEY (/C/USERS/9JZ/ SSH/ID_RSA): C/USERS/GJZ/.SSH/ID_RSA ALREADY EXISTS. OVERWRITE (Y/N)? Y (EMPTY FOR NO PASSPHRASE): ENTER PASSPHRASE FOR "/C/USERS/GJZ/.SSH/ID_RSA" SAME PASSPHRASE ENTER AGAIN: HAS JDENTIFICATION BEEN SAVED IN /C/USERS/GJZ/.SSH/ID_RSA YOUR -->
![](/images/hexo-github-blog/ssh-keygen.png)

> SSH密钥：
>
> + 生成的是一对密钥：公钥和私钥。私钥，是自己电脑上秘密保存的，不能随便给别人。公钥是可以公开给服务器的，可上传到GitHub。
>

+ 打开C盘查看生成的公钥，用记事本打开生成的公钥并复制

<!-- 这是一张图片，ocr 内容为：>用户>GJZ> 此电脑 在.SSH中搜索 WINDOWS-SSD(C:)> SSH 三查看 预览 个排序 类型 名称 修改日期 大小 文件 2025/5/31 13:35 CONFIG 1 KB 文件 ID RSA 2026/3/16 15:32 3KB PUB文件 2026/3/16 15:32 1 KB ID RSAPUB 文件 2025/5/3113:46 2 KB KNOWN HOSTS OLD 文件 KNOWN HOSTS.OLD 1 KB 2025/5/3113:46 -->
![](/images/hexo-github-blog/ssh-folder.png)

+ 打开GitHub的设置，添加一个新的SSH Key，名为Hexo blog-key（可自定义）

<!-- 这是一张图片，ocr 内容为：GGGJJZZ123(GGGJJJZZ123) GO TO YOUR PERSONAL PROFILE YOUR PERSONAL ACCOUNT ADD NEW SSH KEY PUBLIC PROFILE ACCOUNT TITLE APPEARANCE HEXO ACCESSIBILITY KEY TYPE NOTIFICATIONS AUTHENTICATION KEY ACCESS KEY BILLING AND LICENSING EMAILS OR'SK-SSH-ED25519@OPENSSH.COM' PASSWORD AND AUTHENTICATION SESSIONS SSH AND GPG KEYS ORGANIZATIONS ENTERPRISES MODERATION ADD SSH KEY CODE,PLANNING,AND AUTOMATION -->
![](/images/hexo-github-blog/github-ssh-add.png)

+ 添加完成

<!-- 这是一张图片，ocr 内容为：HEXO BLOG-KEY SHA256:346T7ZMN4GE9ATSLUBMGW5XRVPIARRZNXONCXIWI2A8 删除 添加于2026年3月16日 SSH 从未使用-读写 -->
![](/images/hexo-github-blog/github-ssh-added.png)

+ 在git中用命令测试是否能和GitHub通信

<!-- 这是一张图片，ocr 内容为：/D/桌面 GJZ@LAPTOP-50AIOOL8 MINGW64 $ SSH -T GIT@GITHUB.COM SSH: CONNECT TO HOST GITHUB.COM PORT 22: CONNECTION TIMED OUT GJZ@LAPTOP-50AI00L8 MINGW64 /D/桌面 $ SSH -T -P 443 GIT@SSH.GITHUB.COM 443)' CAN'T BE [SSH.GITHUB.COM]:443 ([20.205.243.160]:443) THE AUTHENTICITY OF HOST 'SSH ESTABLISHED. IED25519 KEY FINGERPRINT IS SHAZ56;+DIY3WYVETUJJHBPZISF/ZLDAOZPMSYHAKR4UVCOQU THIS HOST KEY IS KNOWN BY THE FOLLOWING OTHER NAMES/ADDRESSES: /.SSH/KNOWN_HOSTS:1:GITHUB.COM YOU WANT TO CONTINUE CONNECTING (YES/NO/CFINGERPRINT]? YES SURE ARE YOU PERMANENTLY ADDED ' SSH.GITHUB.COM):443' (ED25519) TO THE LIST OF KNOWN WARNING: HOSTS HI GGGJJZZZZI23! YOU'VE SUCCESSFULLY AUTHENTICATED, BUT GITHUB DOES NOT PROVIDE SHELL ACCESS, GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 -->
![](/images/hexo-github-blog/ssh-test.png)

+ 上述显示测试不通，原因是默认的22端口被占用，按照下面测试443端口是否能测通

<!-- 这是一张图片，ocr 内容为：/D/桌面 GJZ@LAPTOP-50AIOOL8 MINGW64 $ SSH -T GIT@GITHUB.COM SSH: CONNECT TO HOST GITHUB.COM PORT 22: CONNECTION TIMED OUT GJZ@LAPTOP-50AI00L8 MINGW64 /D/桌面 $ SSH -T -P 443 GIT@SSH.GITHUB.COM 443)' CAN'T BE [SSH.GITHUB.COM]:443 ([20.205.243.160]:443) THE AUTHENTICITY OF HOST 'SSH ESTABLISHED. IED25519 KEY FINGERPRINT IS SHAZ56;+DIY3WYVETUJJHBPZISF/ZLDAOZPMSYHAKR4UVCOQU THIS HOST KEY IS KNOWN BY THE FOLLOWING OTHER NAMES/ADDRESSES: /.SSH/KNOWN_HOSTS:1:GITHUB.COM YOU WANT TO CONTINUE CONNECTING (YES/NO/CFINGERPRINT]? YES SURE ARE YOU PERMANENTLY ADDED ' SSH.GITHUB.COM):443' (ED25519) TO THE LIST OF KNOWN WARNING: HOSTS HI GGGJJZZZZI23! YOU'VE SUCCESSFULLY AUTHENTICATED, BUT GITHUB DOES NOT PROVIDE SHELL ACCESS, GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 -->
![](/images/hexo-github-blog/ssh-test-443.png)

+ 上述显示测试成功，接下来把SSH配置改成以后默认走443

<!-- 这是一张图片，ocr 内容为：HTTPD.CONF ID RSA.PUB CONFI H1V : BIGA 文件 查看 编辑 HOST 192.168.216132 HOSTNAME 192.168.216.132 USER GJZ HOST GITHUB.COM HOSTNAME SSH.GITHUB.COM PORT 443 USER GIT GERPRI 19) TO GITHUB ARGUMER 纯文本 129个字符 行7,列13 UTF-8 UNIX (LF) 100% ARGL GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 $ NANO ~/,SSH/CONFIG MINGW64/D/桌面 GJZ@LAPTOP-50AIOOL8 NOTEPAD~/.SSH/CONFIG GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 NOTEPAD ~/.SSH/CONFIG -->
![](/images/hexo-github-blog/ssh-config.png)

+ 再进行测试，显示成功

<!-- 这是一张图片，ocr 内容为：/D/桌面 GJZ@LAPTOP-50AIOOL8 MINGW64 $ SSH -T GIT@GITHUB.COM HI GGGJJZZZZI23! YOU'VE SUCCESSFULLY AUTHENTICATED, BUT GITHUB DOES NOT PROVIDE SHELL ACCESS, GJZ@LAPTOP-50AIOOL8 MINGW64 /D/桌面 -->
![](/images/hexo-github-blog/ssh-test-success.png)

### 三、初始化Hexo项目（本地部署）
#### 新建一个文件夹专门存放博客内容
<!-- 这是一张图片，ocr 内容为：此电脑 > HEXO-BLOG DATA(D:) N 查看 排序 类 修改日期 名称 此文件夹为空. -->
![](/images/hexo-github-blog/hexo-folder.png)

#### 进入该文件夹，右键打开Git Bash，输入命令创建一个Hexo项目，项目名字为gjz-blog（可自定义）
<!-- 这是一张图片，ocr 内容为：LGJZ@LAPTOP-50AIOOL8 MINGW64 /D/HEXO-BLOG $ HEXO INIT GJZ-BLOG CLONING HEXO-STARTER HTTPS://GITHUB.COM/HEXOJS/HEXO-STARTER.GIT INFO FATAL: UNABLE TO ACCESS 'HTTPS://GITHUB.COM/HEXOJS/HEXO-STARTER.GIT/': COULD NOT RESOLVE HOST: GITHUB.COM GIT CLONE FAILED. COPYING DATA INSTEAD WARN 1 DEPENDENCIES INSTALL D INFO SE RUN 'NPM INSTALL' IN "D:\HEXO-BLOG\ FAILED TO INSTALL DEPENDENCIES. PLEASE WARN GJZ-BLOG" FOLDER, -->
![](/images/hexo-github-blog/hexo-init.png)

<!-- 这是一张图片，ocr 内容为：此电脑>DATA(D:)> HEXO-BLOG> 个排序 查看 修改日期 名称 类型 文件夹 2026/3/1616:04 GJZ-BLOG -->
![](/images/hexo-github-blog/hexo-folder-created.png)

+ 初始化项目后，gjz-blog有如下结构

<!-- 这是一张图片，ocr 内容为：此电脑 DATA(D:)> HEXO-BLOG GJZ-BLOG 在GJZ-BLOG中搜索 仆排序 三查看 大小 类型 修改日期 名称 文件夹 2026/3/1616:04 -GITHUB 文件夹 2026/3/16 16:04 SCAFFOLDS 文件夹 2026/3/16 16:04 SOURCE 文件夹 2026/3/16 16:04 THEMES O KB 2025/4/2016:50 CONFIG.LANDSCAPE.YML YMLFILE 3 KB 2025/4/2016:50 .CONFIG.YML YML FILE JSON FILE 1 KB 2025/4/2016:50 PACKAGE.JSON -->
![](/images/hexo-github-blog/hexo-structure.png)

> <!-- 这是一张图片，ocr 内容为： -->
![](/images/hexo-github-blog/hexo-structure-detail.png)
>

#### 在git中输入命令进入新建好的Hexo项目文件夹
<!-- 这是一张图片，ocr 内容为：LGJZ@LAPTOP-5OAIOOL8 MINGW64 /D/HEXO-BLOG $ CD GJZ-BLOG LOJZQLAPTOP-50AIOOL8 MINGW64 /D/HEXO-BLOG/GJZ-BLOG -->
![](/images/hexo-github-blog/hexo-cd.png)

#### 安装项目依赖
<!-- 这是一张图片，ocr 内容为：IGJZ@LAPTOP-50AIOOL8 MINGW64 /D/HEXO-BLOG/GJZ-BLOG NPMI INFLIGHT@L.O.6: THIS MODULE IS NOT SUPPORTED, AND LEAKS MEMO DEPRECATED WARN NPM BO NOT USE IT. CHECK OUT LRU-CACHE IF YOU WANT A GE GOOD AND TESTED WAY TO COAL RY. ASYNC REQUESTS BY A KEY VALUE, WHICH IS MUCH MORE COMPREHENSIVE AND POWERFUL ESCE DEPRECATED GLOBA7 .2.3: GLOB VERSIONS PRIOR TO V9 ARE NO LONGER SUPPORTEL WARN NPM P CUID@2.1.8: DEPRECATED CHE CUID AND OTHER K-SORTABLE AND NON-CRYPTOGRAPHIC WARN NPM ALL U OBJECTID, (ULID, UUIDS) ARE ALL INSECURE. USE @PARALLELDRIVE/CUID KSUID. DS 2 INSTEAD. DEPRECATED ABAB@2.0.6: USE YOUR PLATFORM'S NATIVE ATOBO AND BTOAG WARN MET NPM INSTEAD THODS DEPRECATED DOMEXCEPTIONE4.0.0. USE YOUR PLATFORM'S NATIVE DOMEXCEPTION WARN NPM INSTEAD DEPRECATED WARN MOIZE@6.1.7: THIS LIBRARY HAS BEEN DEPRECATED IN FAVOR OF MIN NPM VERSION 5 INCORPORATES MOST OF THE FUNCTIONALITY THAT THAT THE CRO-MEMOIZE, WHICH AS-OF LIBRARY OFFERS AT NEARLY HALF THE SIZE AND BETTER SPEED. HIS L -->
![](/images/hexo-github-blog/npm-install.png)

+ 生成文件如下

<!-- 这是一张图片，ocr 内容为：此电脑 在GJZ-BLOG中搜索 DATA(D:) HEXO-BLOG GJZ-BLOG 三查看 仆排序 大小 修改日期 类型 名称 2026/3/16 16:04 文件夹 -GITHUB 文件夹 2026/3/1616:04 SCAFFOLDS 文件夹 2026/3/16 16:04 SOURCE 文件夹 2026/3/1616:04 THEMES 2025/4/20 16:50 OKB YML FILE CONFIG.LANDSCAPE.YML 3 KB 2025/4/2016:50 YML FILE .CONFIG.YML ISON FILE 2025/4/20 16:50 1 KB PACKAGE.JSON 文件夹 2026/3/16 16:51 NODE MODULES 91 KB 2026/3/16 16:51 JSON FILE PACKAGE-LOCK.JSON -->
![](/images/hexo-github-blog/npm-install-done.png)

> 安装项目需要的依赖包
>
> + `npm i`就是 `npm install`的缩写，表示用 npm 安装依赖；单独写时通常安装当前项目所有依赖，后面加包名时表示安装指定包，加 `-g`时表示全局安装。
> + 全局工具≠项目依赖
> + npm 会去读取当前目录里的 `package.json`，然后把里面声明的依赖全部下载并安装到当前目录下的 `node_modules`文件夹里。
>

#### 启动项目
<!-- 这是一张图片，ocr 内容为：D/HEXO-BLOG/GJZ-BLOG GJZ@LAPTOP-50AIOOL8 MINGW64 $ HEXO S VALIDATING CONFIG INFO START PROCESSING INFO PRESS CTRL+C TO STOP. HEXO IS RUNNING AT HTTP://LOCALHOST:4000/ INFO -->
![](/images/hexo-github-blog/hexo-server.png)

+ 访问 [http://localhost:4000/](http://localhost:4000/)即可出现以下画面，本地部署成功

<!-- 这是一张图片，ocr 内容为：SUMMARIZE岛商家1品会 包南 LOCALHOST:4000 ARCHIVES HOME HEXO 2026-03-16 ARCHIVES MARCH 2026 HELLOWORLD WELCOME TO HEXO! THIS IS YOUR VERY FIRST POST.CHECK DOCUMENTATION FOR MORE INFO. IF YOU GET RECENT POSTS  ANY PROBLEMS WHEN USING OR YOU CAN FIND THE ANSWER IN TROUBLESHOOTING OR YOU CAN ASK ME ON GITHUB. HELLOWORLD QUICK START CREATE A NEW POST HEXO NEW "MY NEW POST" MORE INFO:WRITING RUN SERVER $ HEXO SERVER MORE INFO: SERVER -->
![](/images/hexo-github-blog/hexo-local.png)

### 四、将项目部署到GitHub Pages
#### 按ctrl+c退出刚刚运行的本地部署，输入命令安装部署所需要的依赖
<!-- 这是一张图片，ocr 内容为：GJZQLAPTOP-5OAIOOL8 MINGW64 /D/HEXO-BLOG/GJZ-BLOG -SAVE S NPM INSTALL HEXO-DEPLOYER-GIT ADDED 9 PACKAGES IN 4S LOOKING FOR FUNDING 34 ARE PACKAGES FUND FOR DETAILS RUN NPM -->
![](/images/hexo-github-blog/hexo-deployer-install.png)

> `hexo-deployer-git`  
> 这是要安装的包名。它是 Hexo 的一个部署插件，作用通常是让 Hexo 可以把生成好的博客内容部署到 Git 仓库，比如推送到 GitHub Pages。
>
> `--save`  
> 这是一个旧一点但仍能理解的参数，意思是安装这个包时，把它记录到当前项目的 `package.json`里的依赖项中。
>

#### 用vscode打开博客的配置文件
<!-- 这是一张图片，ocr 内容为：WINRAR 以NOTEPAD++编辑 在GJZ-BLOG中搜索 LOG EDIT WITH PYCHARM 添加到收藏夹(F) 转为在线文档 上传到迅雷云盘 类型 大小 名称 添加到压缩文件(A)... 文件夹 .GITHUB 添加到"_CONFIG.ZIP"(T) 文件夹 SCAFFOLDS 添加到高压缩率文件"CONFIG.7Z"(W) 文件夹 SOURCE 右键菜单管理 THEMES 打开方式(H) VISUAL STUDIO CODE CONFIG.LANDSC  KB 上传或同步到WPS V 搜索MICROSOFT STORE(S) .CONFIG.YML 3 KB 通过WPS发送 选择其他应用(C) 1 KB JSON FILE PACKAGE.JSON 编辑 文件夹 NODE MODULE 压缩文件 95 KB JSON FILE PACKAGE-LOCK. 上传到百度网盘 JSON FILE 20 KB DBJSON 同步至其它设备 -->
![](/images/hexo-github-blog/open-config.png)

#### 修改最后一行的配置，将repository修改为自己的GitHub项目地址即可，并把分支改为main
<!-- 这是一张图片，ocr 内容为：100 # DEPLOYMENT 101 ## DOCS: HTTPS://HEXO.IO/DOCS/ONE-COMMAND-DEPLOYMENT 102 DEPLOY: 103 TYPE: GIT 104 REPOSITORY: GIT@GITHUB.COM:GGGGJJZZ123/GGGGJJZZ123.GITHUB.IO.GIT 105 BRANCH: MAIN 106 107 -->
![](/images/hexo-github-blog/config-deploy.png)

> 它的意思是：当你以后执行 `hexo deploy`或 `hexo d`时，Hexo 会使用 Git 方式，把生成好的站点内容推送到你指定的 GitHub 仓库和分支。Hexo 官方把这种方式叫 one-command deployment，前提是先安装 `hexo-deployer-git`插件。
>
> `deploy:`表示下面开始写部署相关设置。  
> `type: git`表示部署方式是 Git，也就是 Hexo 会通过 Git 把网站文件推到远程仓库。
>
> `repository: git@github.com:GGGjjjjzzzz123/GGGjjjjzzzz123.github.io.git`表示远程仓库地址是你这个 GitHub 仓库，而且你写的是 SSH 地址，所以部署时会走你前面已经配置好的 SSH 认证。
>
> `branch: main`表示 Hexo 部署时，把生成后的站点文件推送到这个仓库的 `main`分支。
>

#### 输入命令，进行清理、生成和部署
<!-- 这是一张图片，ocr 内容为：D/HEXO-BLOG/GJZ-BLOG GJZ@LAPTOP-50AIOOL8 MINGW64 && HEXO CLEAN & HEXO DEPLOY $ HEXO GENERATE VALIDATING CONFIA INFO -->
![](/images/hexo-github-blog/hexo-deploy.png)

+ 出现下面这个信息表示成功部署到GitHub

<!-- 这是一张图片，ocr 内容为：TO TRAC MASTER AN SET BRANCH JO.GIT/MAIN INFO GIT DEPLOY DONE: -->
![](/images/hexo-github-blog/deploy-success.png)

> `hexo clean`  
> 清理缓存文件和旧的生成结果。
>
> `hexo generate`  
> 把你的文章、主题、配置这些内容重新生成成静态网页文件，通常会生成到 `public`文件夹。
>
> `hexo deploy`  
> 把生成好的静态网页部署到你配置好的远程仓库，比如 GitHub Pages。
>

<!-- 这是一张图片，ocr 内容为：台 O 请记入()去接素 GGGJJJZZ123 / GGGJLJZZZZ123.GITHUB.IO 田 中 WIKI K润察 字设置 项目 安全 操作 议题 拉取请求 代码 食星标O 置顶 GGGJJJZZZ123.QITHUB,IO R取消关注 公共 关于 亨 P MAIN 添加文件 <>代码 节 1分支 转到文件 0标签 博客演示,用于存放项目文档,理论学 GGGIJJZZZ123 SITE UPDATED:2026-03-15 17:12:47 2次提交 09CTD93.2分钟前 习文档,学科文档 999JJJZZZ123-GITHUB-IO.VERCEL.APP 2026/03/16/HELLO-WORLD 2分钟前 SITE UPDATED:2026-03-16 17:12:47 小活动 2分钟前 SITE UPDATED:2026-03-16 12:47 ARCHNES 0星标 SITE UPDATED:2026-03-16 17:12:47 2分钟前 CSS R 1关注 0复刻 SITE UPDATED:2026-03-16 17:12.47 2分钟前 FANCYBOX 2分钟前 SITE UPDATED:2026-03-16 17:12:47 JS 发行版 2分钟前 INDEXHTML SITE UPDATED:2026-03-16 17:12:47 未发布任何版本 创造发行版 中自述文件 部署 GITHUB-PAGES 2分钟前 PRODUCTION  2分钟前 添加README 二4个部署 帮助对此仓库感兴趣的人了解您的项目. 软件包 添加 README 未发布软件包 发布软件包 -->
![](/images/hexo-github-blog/github-repo-deployed.png)

### 五、安装butterfly主题
[butterfly主题](https://www.yuque.com/u49396310/eg1484/hi4stulcyt49uyqm)
