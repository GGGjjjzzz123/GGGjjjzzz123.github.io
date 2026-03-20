---
title: butterfly主题
date: 2025-04-21  # 发布日期
categories: [技术文章]  # 分类
tags: [Hexo, 主题]  # 标签
---

## 安装butterfly主题
用VScode打开项目文件夹，新建终端

```powershell
npm i hexo-theme-butterfly
```

> <font style="color:rgb(31, 31, 31);">安装成功后可在【C:/Hexo-Blog/blog-demo/node_modules】文件夹下找到hexo-theme-butterfly文件夹</font>
>

## <font style="color:rgb(31, 31, 31);">应用butterfly主题</font>
1. <font style="color:rgb(31, 31, 31);">在配置文件</font><font style="color:rgb(244, 116, 102);">_config.yml中</font>，把主题改为butterfly

```yaml
theme: butterfly
```

2. 接着安装两个渲染器插件，使butterfly主题正常运行

```powershell
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

## 在VScode终端启动项目
:::color2
目的： 本地预览，快速调试样式、排查错误 ， 不需要每次都上传 GitHub 就看效果 。

:::

1. 修改执行策略，使得项目能够在VScode终端运行

```powershell
get-ExecutionPolicy
```

> 显示RemoteSigned，表示当前系统允许运行本地的脚本
>
> 显示Restricted，状态是禁止的
>

```powershell
Set-ExecutionPolicy RemoteSigned
```

>  将 PowerShell 的执行策略设置为 `RemoteSigned`
>

:::color2
如果这步出现报错的情况：

权限问题，以管理员的身份重新打开VScode

:::

```powershell
Get-ExecutionPolicy
```

>  再次查看当前的执行策略，确认修改是否生效。  
>

2. 清理并启动本地项目

```powershell
hexo cl; hexo s
```

> 访问 [http://localhost:4000/](http://localhost:4000/) 即可在本地查看网站已经换上主题
>



:::info
理解

在安装了butterfly的毛坯房后，进行个性化的装修、装饰

:::

## 基础用法
### Front Matter（头部信息）
> 模板中的示例文章使用markdown语法写的，删除示例文章后，文件中没有内容，网站页面显示会出现错误
>

 头部信息（Front-matter）是每篇文章或页面文件最上方用 `YAML` 格式编写的一段内容，用于定义该文章的元数据。它被三个短横线 `---` 包裹，Hexo 会根据这些信息来生成对应的页面结构、链接、标签等。  

1. 新建md文件

> 在文件中输入Front Matter（头部信息），hexo就是依靠头部信息判定这是一篇文章
>

+ 手动输入

```powershell
---
title: 第一篇文章
date: 2025-4-23 21:00:00
update: 2025-4-23 21:00:00
---
## 第一篇文章
```

> 写在“---”内的信息为头部信息
>

+ 自动创建

```powershell
hexo new "文章的名字"
```

2. Front Matter（头部信息）的其他功能关键字

| <font style="color:rgb(31, 31, 31);">写法</font> | <font style="color:rgb(31, 31, 31);">解释</font> |
| --- | --- |
| <font style="color:rgb(31, 31, 31);">title</font> | <font style="color:rgb(31, 31, 31);">【必需】文章标题</font> |
| <font style="color:rgb(31, 31, 31);">date</font> | <font style="color:rgb(31, 31, 31);">【必需】文章创建日期</font> |
| <font style="color:rgb(31, 31, 31);">updated</font> | <font style="color:rgb(31, 31, 31);">【可选】文章更新日期</font> |
| <font style="color:rgb(31, 31, 31);">tags</font> | <font style="color:rgb(31, 31, 31);">【可选】文章标籤</font> |
| <font style="color:rgb(31, 31, 31);">categories</font> | <font style="color:rgb(31, 31, 31);">【可选】文章分类</font> |
| <font style="color:rgb(31, 31, 31);">keywords</font> | <font style="color:rgb(31, 31, 31);">【可选】文章关键字</font> |
| <font style="color:rgb(31, 31, 31);">description</font> | <font style="color:rgb(31, 31, 31);">【可选】文章描述</font> |
| <font style="color:rgb(31, 31, 31);">top_img</font> | <font style="color:rgb(31, 31, 31);">【可选】文章顶部图片</font> |
| <font style="color:rgb(31, 31, 31);">cover</font> | <font style="color:rgb(31, 31, 31);">【可选】文章缩略图(如果没有设置top_img,文章页顶部将显示缩略图，可设为false/图片地址/留空)</font> |
| <font style="color:rgb(31, 31, 31);">comments</font> | <font style="color:rgb(31, 31, 31);">【可选】显示文章评论模块(默认 true)</font> |
| <font style="color:rgb(31, 31, 31);">toc</font> | <font style="color:rgb(31, 31, 31);">【可选】显示文章TOC(默认为设置中toc的enable配置)</font> |
| <font style="color:rgb(31, 31, 31);">toc_number</font> | <font style="color:rgb(31, 31, 31);">【可选】显示toc_number(默认为设置中toc的number配置)</font> |
| <font style="color:rgb(31, 31, 31);">toc_style_simple</font> | <font style="color:rgb(31, 31, 31);">【可选】显示 toc 简洁模式</font> |
| <font style="color:rgb(31, 31, 31);">copyright</font> | <font style="color:rgb(31, 31, 31);">【可选】显示文章版权模块(默认为设置中post_copyright的enable配置)</font> |
| <font style="color:rgb(31, 31, 31);">copyright_author</font> | <font style="color:rgb(31, 31, 31);">【可选】文章版权模块的文章作者</font> |
| <font style="color:rgb(31, 31, 31);">copyright_author_href</font> | <font style="color:rgb(31, 31, 31);">【可选】文章版权模块的文章作者链接</font> |
| <font style="color:rgb(31, 31, 31);">copyright_url</font> | <font style="color:rgb(31, 31, 31);">【可选】文章版权模块的文章连结链接</font> |
| <font style="color:rgb(31, 31, 31);">copyright_info</font> | <font style="color:rgb(31, 31, 31);">【可选】文章版权模块的版权声明文字</font> |
| <font style="color:rgb(31, 31, 31);">mathjax</font> | <font style="color:rgb(31, 31, 31);">【可选】显示mathjax(当设置mathjax的per_page: false时，才需要配置，默认 false)</font> |
| <font style="color:rgb(31, 31, 31);">katex</font> | <font style="color:rgb(31, 31, 31);">【可选】显示katex(当设置katex的per_page: false时，才需要配置，默认 false)</font> |
| <font style="color:rgb(31, 31, 31);">aplayer</font> | <font style="color:rgb(31, 31, 31);">【可选】在需要的页面加载aplayer的js和css,请参考文章下面的音乐 配置</font> |
| <font style="color:rgb(31, 31, 31);">highlight_shrink</font> | <font style="color:rgb(31, 31, 31);">【可选】配置代码框是否展开(true/false)(默认为设置中highlight_shrink的配置)</font> |
| <font style="color:rgb(31, 31, 31);">aside</font> | <font style="color:rgb(31, 31, 31);">【可选】显示侧边栏 (默认 true)</font> |


3. <font style="color:rgb(31, 31, 31);">例子：</font>

<!-- 这是一张图片，ocr 内容为：2025.4.21.MD POSTS SOURCE 1 TITLE:第一篇文章 2 DATE: 2025-4-21 16:00:00 3 4 UPDATE: 2025-4-21 16:00:00 随笔 CATEGORIES: 5 6 第一篇文章 7 -->
![](/images/butterfly-theme/image_001_1745224270084-fbc06dc9-ad9d-49a6-acde-60da7c5fc1e6.png)<!-- 这是一张图片，ocr 内容为：第一篇文章 曲CREATED 2025-04-21 随笔 第一篇文章 -->
![](/images/butterfly-theme/image_002_1745224290568-81dde2cc-4a0b-4744-9b77-f7fb3fbaf9dc.png)<!-- 这是一张图片，ocr 内容为：随笔 随笔 O CATEGORY -  2025 JOHN DOE 曲2025-04-21 CATEGORIES TAGS ARTICLES 0 2 第一篇文章 FOLLOW ME -->
![](/images/butterfly-theme/image_003_1745224314881-8dc51c92-6313-4ae0-a597-60a96a32e1a5.png)

### 标签页
1. 建立tags文件夹

```powershell
hexo new page tags
```

> <font style="color:rgb(31, 31, 31);">在</font>`<font style="color:rgb(244, 116, 102);">source</font>`<font style="color:rgb(31, 31, 31);">会生成一个含有</font>`<font style="color:rgb(244, 116, 102);">index.md</font>`<font style="color:rgb(31, 31, 31);">文件的</font>`<font style="color:rgb(244, 116, 102);">tags</font>`<font style="color:rgb(31, 31, 31);">文件夹</font>
>

2. 在 <font style="color:rgb(244, 116, 102);">source\tags\index.md</font> 中添加 type: "tags"

```powershell
---
title: tags
date: 2022-10-28 12:00:00
type: "tags"
---
```

> 添加一条类型信息来说明这个页面是一个标签页，butterfly主题会根据这个类型在页面上渲染出特定的信息
>

### 友情链接页
1. 建立一个友情链接link文件夹

```powershell
hexo new page link
```

> 在`<font style="color:rgb(244, 116, 102);">source\</font>`<font style="color:rgb(31, 31, 31);">会生成一个含有</font>`<font style="color:rgb(244, 116, 102);">index.md</font>`<font style="color:rgb(31, 31, 31);">文件的</font>`<font style="color:rgb(244, 116, 102);">link</font>`<font style="color:rgb(31, 31, 31);">文件夹</font>
>

2. <font style="color:rgb(31, 31, 31);">修改</font>`<font style="color:rgb(244, 116, 102);">source\link\index.md</font>`<font style="color:rgb(31, 31, 31);">，添加</font>`<font style="color:rgb(244, 116, 102);">type: "link"</font>`

```powershell
---
title: link
date: 2022-10-28 12:00:00
type: "link"
---
```

> 步骤和原理和标签页一样
>

3. 在source下创建一个_data文件夹（友链配置文件），在_data文件夹下再创建一个link.yml文件

```yaml
- class_name: 1.技术支持
  class_desc: 本网站的搭建由以下开源作者提供技术支持
  link_list: 
    - name: Hexo 
      link: https://hexo.io/zh-cn/
      avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg
      descr: 快速、简单且强大的网志框架
      siteshot: https://source.fomal.cc/siteshot/hexo.io.jpg
      
- class_name: 2.友情链接
  class_desc: 一些好朋友~~
  link_list:
    - name: Fomalhaut🥝
      link: https://fomal.cc/
      avatar: /assets/head.jpg
      descr: Future is now 🍭🍭🍭
      siteshot: https://source.fomal.cc/siteshot/www.fomal.cn.jpg
```

### 图库、子页面等
创建其他的页面只需要

```powershell
hexo new page  xxx
```

再在相应的文件中修改头部信息，添加对应页面类型的标签

### 404页面
在_config.butterfly.yml修改error_404部分代码

<!-- 这是一张图片，ocr 内容为：# A SIMPLE 404 PAGE 110 111 404: ERROR ENABLE: TRUE 112 FOUND' 113 SUBTITLE: PAGE NOT BACKGROUND: /IMG/ERROR-PAGE.PNG 114 115 -->
![](/images/butterfly-theme/image_004_1745237697398-9bc4f64e-de2e-4d37-95ad-e000d13310cd.png)

<!-- 这是一张图片，ocr 内容为：CANNOT GET ET/404.HTML -->
![](/images/butterfly-theme/image_005_1745237605639-32b773ba-85a8-480c-8f52-27a031a5c288.png)<!-- 这是一张图片，ocr 内容为：HEXO 404 404 PAGE NOT FOUND -->
![](/images/butterfly-theme/image_006_1745237751129-61882863-95b2-40d2-bba7-f871b8ee59f4.png)

## butterfly主题的基础配置
:::color2
在_config.butterfly.yml（主题配置文件）文件中进行修改

:::

### 修改菜单栏选项配置
1. ctrl+/：释放注释
2. 将菜单栏选项进行重命名

```yaml
menu:
  首页: / || fas fa-home
  列表||fas fa-list:
    音乐: /music/ || fas fa-music
    电影: /movies/ || fas fa-video
  友链: /link/ || fas fa-link
  标签: /tags/ || fas fa-tags


```

3. 在source文件夹（Hexo默认的根目录）下创建不存在的文件夹，再在文件下创建index.md文件（代表文件夹的主页），在各个index.md文件下配置相关的内容（头部信息）

<!-- 这是一张图片，ocr 内容为：SOURCE DATA POSTS LINK INDEX.MD MOVIES INDEX.MD MUSIC INDEX.MD TAGS INDEX.MD -->
![](/images/butterfly-theme/image_007_1745239353907-4fbb32b4-ecfb-43a5-9cb6-671da807669d.png)<!-- 这是一张图片，ocr 内容为：INDEX.MD MUSIC SOURCE 1 TITLE:音乐 2 DATE: 2025-04-21 16:54:27 3 4 -->
![](/images/butterfly-theme/image_008_1745239371524-18503c83-2dd6-46ae-a409-ad38769e0802.png)

```yaml
---
title: 音乐
date: 2025-04-21 16:54:27
---
```

4. 效果展示

<!-- 这是一张图片，ocr 内容为：友链 首页 三列表 标签 音乐 电影 -->
![](/images/butterfly-theme/image_009_1745239971156-231f1784-0eaa-4e7b-8cdd-f8eb0bf372f2.png)

> 上面设置的友链部分内容
>

<!-- 这是一张图片，ocr 内容为：1.技术支持 本网站的搭建由以下开源作者提供技术支持 HEXO H 快速,简单且强大的网... 2.友情链接 一些好朋友~~ FOMALHAUT FUTURE IS NOW -->
![](/images/butterfly-theme/image_010_1745240001269-5660d176-29e4-4232-95fd-1c0eb6f4b6b7.png)

### 代码块的设置（Code Blocks Settings）
1. 代码格式

```yaml
code_blocks:
  # Code block theme: darker / pale night / light / ocean / false
  theme: light
```

<!-- 这是一张图片，ocr 内容为：编辑 复制 YAML CODE_BLOCKS: # CODE BLOCK THEME: DARKER / PALE NIGHT / LIGHT / OCEAN / FALSE THEME: LIGHT 代码块的配色主题. 可选值: DARKER:暗黑风 PALENIGHT:柔和暗色风 LIGHT:亮色风(你现在用的) 蓝色系 OCEAN 不使用主题样式(你会失去美化) FALSE -->
![](/images/butterfly-theme/image_011_1745239572183-8c9ab60a-a7ad-433b-ae40-4e233afe9577.png)

```yaml
macStyle: false
```

<!-- 这是一张图片，ocr 内容为：白复制 编辑 YAML MACSTYLE: FALSE 红黄绿). 是否开启MAC风格的代码块样式(左上角显示三个小圆点 会模拟MACOS终端的样式. TRUE -->
![](/images/butterfly-theme/image_012_1745239602199-e0e21f0a-4e84-4b28-813f-6e617a5ceae2.png)

```yaml
  height_limit: false
```

<!-- 这是一张图片，ocr 内容为：限制代码块最大高度,超出部分会滚动. 举例:HEIGHT_LIMIT:300表示最多显示300PX高,超过就滚动. 表示不限制,显示全部内容. FALSE -->
![](/images/butterfly-theme/image_013_1745239775022-c5aada5d-89cb-41c2-907e-05a55a4c1975.png)

```yaml
  word_wrap: false
```

<!-- 这是一张图片，ocr 内容为：是否自动换行. 当代码太长时自动换行显示(适合移动端) TRUE FALSE:长代码横向滚动 -->
![](/images/butterfly-theme/image_014_1745240254037-17dafdf3-47ac-4fd8-b4d3-c0a51694753e.png)

2. 代码工具栏部分

```yaml
  copy: true
```

<!-- 这是一张图片，ocr 内容为：是否显示"复制代码"按钮 TRUE:每个代码块右上角会出现"复制"图标 用户一键点击即可复制代码,非常实用! -->
![](/images/butterfly-theme/image_015_1745240336753-eb78d738-8bb3-42f8-bab1-520876c25567.png)

```yaml
  language: true
```

<!-- 这是一张图片，ocr 内容为：是否显示代码块的语言标识(如 JAVASCRIPT PYTHON 显示语言 TRUE 不显示 FALSE -->
![](/images/butterfly-theme/image_016_1745240385840-75e94d8b-fd6f-4278-8d15-0954c760fa00.png)

```yaml
  shrink: false
```

<!-- 这是一张图片，ocr 内容为：是否收起/折叠代码块 可选值: 默认折叠,用户需要点击"展开" TRUE 默认展开 FALSE 展开代码块并隐藏"展开/收起"按钮 NONE -->
![](/images/butterfly-theme/image_017_1745240435819-14c76e06-6702-492a-bbf2-9867a1e165a1.png)

```yaml
  fullpage: false
```

<!-- 这是一张图片，ocr 内容为：是否开启"全屏查看代码"按钮(点击后代码块会放大全屏显示) 开启全屏按钮 TRUE FALSE:关闭该按钮 -->
![](/images/butterfly-theme/image_018_1745240480734-1117ee57-998c-4c93-810e-95b3c05ea1a3.png)

3. 效果展示

<!-- 这是一张图片，ocr 内容为：IBS CREATE TABLE "TOPIC"( "ID"SERIAL NOT NULL PRIMARY KEY, "FORUM ID INTEGER NOT NULL, "SUBJECT"VARCHAR(255)NOT NULL 4 5 ALTER TABLE"TOPIC" 9 ADD CONSTRAINT FORUM_ID FOREIGN KEY ("FORUM ID") Z ("ID"); 8 REFERENCEST FORUM" 9 10--INITIALS 11 INSERT INTO "TOPIC"("FORUM ID","SUBJECT") 12 VALUES(2,D''ARTAGNIAN'); -->
![](/images/butterfly-theme/image_019_1745240626768-f8bfad5c-3663-4628-b290-1e4e056c111e.webp)

### 个人社交卡片的信息（Social media links）
添上想展示的个人信息即可

### 设置图片
自行设置

### 各种设置
自行了解

### 搜索功能（以本地搜索为例）
1. 需要安装依赖

```powershell
npm install hexo-generator-search --save
```

2. 在网站配置文件中添加以下内容

> 注意不是主题配置文件
>

```yaml
search:
  path: search.xml
  field: post
  content: true
```

3. 修改主题配置文件中的本地搜索

```yaml
  # Local Search
  local_search:
    # Preload the search data when the page loads.
    preload: true
    # Show top n results per article, show all results by setting to -1
    top_n_per_article: 1
    # Unescape html strings to the readable one.
    unescape: true
    CDN:
```

4. 在主题配置配置文件中选择启用本地搜索，并设置占位文本

<!-- 这是一张图片，ocr 内容为：465 # SEARCH 466 467 # 468 469 SEARCH: LOCAL_SEARCH / DOCSEARCH  # CHOOSE: ALGOLIA_SEARCH / 470 471 I LEAVE IT EMPTY IF YOU DON'T NEED SEARCH LOCAL SEARCH 472 USE: 输入关键词 473 PLACEHOLDER: -->
![](/images/butterfly-theme/image_020_1745243395307-a780d1f2-ad8f-4b0d-9d8d-18cfaf8fe7b0.png)

5. 效果展示

<!-- 这是一张图片，ocr 内容为：Q SEARCH 首页 列表 SEARCH 输入矣键词 8. -->
![](/images/butterfly-theme/image_021_1745243139279-7af50e09-1fbc-4783-86da-6b4f829ab087.png)

:::color2
出现默认是英文的情况：

网站配置文件默认语言是en，在网站配置文件修改为zn-CN即可

<!-- 这是一张图片，ocr 内容为：SITE 5 # TITLE: HEXO 6 7 SUBTITLE: 8 DESCRIPTION: 9 KEYWORDS:  AUTHOR: JOHN DOE 10  LANGUAGE: ZH-CN 11 TIMEZONE: 12 13 -->
![](/images/butterfly-theme/image_022_1745243426555-b5bf83fd-725c-42a7-81ee-bd628cb4d149.png)

在这里还可以修改网站的名字、作者名字、描述等

:::

<!-- 这是一张图片，ocr 内容为：搜索 首页 -->
![](/images/butterfly-theme/image_023_1745243363399-3b4bc0d7-b047-491c-8bd0-dd7807c9c206.png)



