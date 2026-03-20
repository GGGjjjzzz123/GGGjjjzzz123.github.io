# Hexo Butterfly 主题装饰完整指南

## 🎨 一、基础配置优化

### 1. 导航栏美化
在 `_config.butterfly.yml` 中配置：
```yaml
nav:
  logo: /img/logo.png
  display_title: true
  fixed: true  # 顶部固定导航

menu:
  首页: / || fas fa-home
  项目文档: /projects/ || fas fa-file-alt
  学习笔记: /notes/ || fas fa-notebook
  语雀链接: /yuque/ || fas fa-link
  标签: /tags/ || fas fa-tags
  分类: /categories/ || fas fa-folder
  关于: /about/ || fas fa-user
```

### 2. 头部横幅 (Hero Banner)
```yaml
# 首页背景图推荐
index_img: /img/banner.jpg
# 其他页面背景图
default_top_img: /img/default-banner.jpg

# 或使用渐变色（无需图片）
index_img: linear-gradient(to right, #4facfe 0%, #00f2fe 100%)
```

### 3. 侧边栏配置
```yaml
aside:
  enable: true
  hide: false
  button: true
  mobile: true

sidebar:
  position: right  # left / right
  divider: true  # 分割线
```

---

## 📚 二、分类和标签美化

### 创建分类页面
```bash
hexo new page categories
```

编辑 `source/categories/index.md`：
```markdown
---
title: 分类
date: 2024-03-18
type: categories
layout: categories
---
```

### 创建标签页面
```bash
hexo new page tags
```

编辑 `source/tags/index.md`：
```markdown
---
title: 标签
date: 2024-03-18
type: tags
layout: tags
---
```

---

## 🗂️ 三、建立语雀文档专区

### 方案 A：创建专题页面
```bash
hexo new page yuque-docs
```

编辑 `source/yuque-docs/index.md`：
```markdown
---
title: 语雀文档库
date: 2024-03-18
layout: page
comments: false
---

## 📖 项目文档
- [您的语雀知识库链接](https://yuque.com/xxx)

## 🎓 学习笔记
- [学习笔记链接](https://yuque.com/xxx)

<iframe 
  src="https://yuque.com/xxx" 
  width="100%" 
  height="800px"
  frameborder="0">
</iframe>
```

### 方案 B：友链式展示
在 `_config.butterfly.yml` 中：
```yaml
# 配置友链
links:
  Yuque知识库: https://yuque.com/xxx
  项目文档: https://docs.example.com
```

---

## 🎭 四、视觉美化配置

### 1. 代码块主题
```yaml
code_blocks:
  theme: ocean  # ocean / light / pale_night / darker
  macStyle: true  # Mac风格标题栏
  copy: true
  language: true
  shrink: false
```

### 2. 首页文章卡片
```yaml
index_post_content:
  method: 1  # 1: 自动摘取 | 2: 摘要标签 | 3: 不显示
  length: 200

# 圆角卡片
index_radius: 8
```

### 3. 日间/夜间模式
```yaml
# 启用深色模式
prefers-color-scheme: true
```

---

## 🖼️ 五、高级美化 - 自定义样式

在 `themes/butterfly/source/css/` 创建 `custom.css`，添加：

```css
/* 渐变色导航栏 */
#nav {
  background: linear-gradient(to right, #667eea 0%, #764ba2 100%);
}

/* 卡片阴影效果 */
.article-card {
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  border-radius: 12px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.article-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

/* 主题色设置 */
:root {
  --primary-color: #667eea;
  --secondary-color: #764ba2;
}
```

---

## 📸 六、推荐外观资源

### 背景图片来源
- Unsplash: https://unsplash.com (免费高质量图片)
- Pexels: https://www.pexels.com
- Pixabay: https://pixabay.com

### 配色方案
- 推荐配色：紫蓝渐变、清爽绿、深邃蓝
- 在线配色：https://coolors.co

### 图标库
- Font Awesome (已集成): https://fontawesome.com
- 优雅图标：https://elegant-icons.com

---

## 🔧 七、社交媒体链接美化

```yaml
social:
  fab fa-github: https://github.com/你的账户 || Github || '#24292e'
  fab fa-qq: https://qq.com || QQ || '#1296db'
  fab fa-weibo: https://weibo.com || 微博 || '#e6162d'
  fas fa-envelope: mailto:你的邮箱 || Email || '#4a7dbe'
  fas fa-link: https://yuque.com/你的账户 || 语雀 || '#25b27b'
```

---

## 🚀 八、动画和交互

在 `_config.butterfly.yml` 中启用：
```yaml
# 鼠标点击效果
cursor: # 配置鼠标样式
  enable: false

# 烟火效果（可选）
fireworks: false

# 页面加载动画
loading: true
```

---

## 📝 九、语雀内容更新策略

### 每周同步流程
1. **在语雀中编辑文档**
2. **导出为Markdown** (语雀支持)
3. **保存至 `source/_posts/yuque/`**
4. **本地 `hexo g && hexo s` 预览**
5. **部署 `hexo deploy`**

### 自动化方案（高级）
创建脚本定期从语雀API拉取文档更新。

---

## ✨ 十、快速开始清单

- [ ] 修改导航菜单 - 添加项目文档、语雀专区
- [ ] 设置头部banner - 选择合适背景图
- [ ] 创建分类/标签/about页面
- [ ] 配置社交媒体链接
- [ ] 启用深色模式
- [ ] 上传logo和头像
- [ ] 创建语雀文档专题页
- [ ] 调整代码块主题
- [ ] 测试移动端响应
- [ ] 部署上线

---

## 🔗 相关资源
- Butterfly 官方文档: https://butterfly.js.org/
- Hexo 官方文档: https://hexo.io/zh-cn/docs/
- 语雀 API: https://www.yuque.com/yuque/developer
