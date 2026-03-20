# 🎨 简约高级风 - 使用指南

## ✨ 配置已完成的内容

### ✅ 已修改：
- ✓ 导航菜单：添加了4个板块 + 关于页面
- ✓ 首页背景：紫蓝渐变 (linear-gradient 135deg)
- ✓ 代码块主题：ocean (高级感)
- ✓ 导航栏：固定在顶部
- ✓ 网站背景：浅灰渐变
- ✓ 各板块背景：独特的渐变配色

### ✅ 已创建的页面结构：
```
source/
├── projects/index.md     → 项目文档
├── theory/index.md       → 理论学习
├── courses/index.md      → 课程笔记
├── miscellaneous/index.md → 杂项
└── about/index.md        → 关于我
```

---

## 🚀 下一步：发布内容

### 为不同板块分类发文：

#### 1️⃣ 项目文档类
```bash
hexo new post "项目名称" --categories "项目文档"
```

#### 2️⃣ 理论学习类
```bash
hexo new post "算法学习笔记" --categories "理论学习" --tags "算法"
```

#### 3️⃣ 课程笔记类
```bash
hexo new post "课程名称笔记" --categories "课程笔记"
```

#### 4️⃣ 杂项类
```bash
hexo new post "工具推荐" --categories "杂项"
```

---

## 🎨 背景图优化方案

### 方案 A：使用渐变色（已应用，推荐）
✅ **优点**：
- 加载快速
- 简约风格完美
- 无需下载管理

✅ **规格**：
```yaml
首页:       紫蓝渐变    linear-gradient(135deg, #667eea 0%, #764ba2 100%)
项目文档:   深紫渐变    linear-gradient(135deg, #667eea 0%, #764ba2 100%)
理论学习:   紫粉渐变    linear-gradient(135deg, #764ba2 0%, #f093fb 100%)
课程笔记:   蓝青渐变    linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)
杂项:       粉绿渐变    linear-gradient(135deg, #a8edea 0%, #fed6e3 100%)
```

---

### 方案 B：升级到高质感背景图（可选）

#### 步骤 1：下载背景图
访问这些网站下载 1600x900px 的图片：
- **Unsplash** (推荐): https://unsplash.com
  - 搜索词: "technology", "minimal", "gradient", "clean"
- **Pexels**: https://www.pexels.com
- **Pixabay**: https://pixabay.com

#### 步骤 2：保存图片
```
source/img/banners/
├── index-bg.jpg         (首页)
├── projects-bg.jpg      (项目文档)
├── theory-bg.jpg        (理论学习)
├── courses-bg.jpg       (课程笔记)
└── misc-bg.jpg          (杂项)
```

#### 步骤 3：修改配置
编辑 `_config.butterfly.yml`，替换渐变色为图片：

```yaml
# 将下面这些：
index_img: linear-gradient(135deg, #667eea 0%, #764ba2 100%)

# 改成：
index_img: /img/banners/index-bg.jpg

# 类似修改其他的 category_per_img
```

---

### 方案 C：最高级 - 自定义CSS微调（可选)

在主题文件夹创建 `source/css/custom.css`，添加：

```css
/* 卡片弹起效果 */
.article-card {
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
}

.article-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(102, 126, 234, 0.15);
}

/* 导航栏玻璃毛玻璃效果 */
#nav {
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.9);
}

/* 代码块优化 */
.hljs {
  border-radius: 8px;
  overflow: hidden;
}
```

---

## 📝 示例文章结构

创建你的第一篇文章来测试效果：

```bash
hexo new post "我的第一篇笔记"
```

编辑 `source/_posts/我的第一篇笔记.md`：

```markdown
---
title: 我的第一篇笔记
date: 2026-03-18
categories: 理论学习
tags: [学习, 笔记]
---

## 文章标题

### 简介
这里是简短介绍...

### 正文内容
在这里写你的内容。

### 总结
学到了什么？
```

---

## 🔄 本地预览 & 部署

### 预览效果
```bash
hexo clean          # 清除缓存
hexo generate       # 生成静态文件
hexo server         # 本地预览 (访问 http://localhost:4000)
```

### 部署上线
```bash
hexo deploy         # 根据你的配置部署到 GitHub/Gitee 等
```

---

## 🎯 配色速查表

| 板块 | 渐变色 | 心理暗示 |
|------|--------|--------|
| 项目文档 | 紫蓝 (#667eea → #764ba2) | 专业、深度 |
| 理论学习 | 紫粉 (#764ba2 → #f093fb) | 创意、学习 |
| 课程笔记 | 蓝青 (#4facfe → #00f2fe) | 清爽、活力 |
| 杂项 | 粉绿 (#a8edea → #fed6e3) | 温暖、包容 |

---

## ⚙️ 常用命令速查

```bash
# 创建新文章
hexo new post "标题"

# 创建新页面
hexo new page "页面名"

# 本地预览
hexo server

# 清空生成
hexo clean

# 全量生成
hexo generate

# 部署
hexo deploy

# 一键生成+部署
hexo generate && hexo deploy
```

---

## 💡 小贴士

1. **分类vs标签**：分类用于板块划分，标签用于细粒度分类
2. **定期更新**：建议每周至少发布1-2篇内容
3. **语雀集成**：在杂项中可以链接到语雀文档
4. **社交链接**：记得在 _config.butterfly.yml 中配置你的社交媒体

---

## 🆘 常见问题

**Q: 页面没有出现？**
A: 运行 `hexo clean` 然后 `hexo generate`

**Q: 背景图没显示？**
A: 检查图片路径是否正确，访问 http://localhost:4000/img/banners/xxx.jpg 测试

**Q: 渐变色效果不好看？**
A: 使用方案C中的CSS微调，或者切换到背景图方案

---

开始创建内容，让你的博客绽放光彩吧！🌟
