---
---
title: "文章标题"
description: "SEO 描述，约 120-160 字"
publishedAt: 2026-05-21
author: "docomola"
tags: ["标签1", "标签2"]
featured: true          # 可选，标记为精选文章
locale: en
---
正文内容...
---

# astro 博客的目录详解

下面是 Astro-Rocket 博客的完整目录结构详解：

---

## 网站结构总览

```
astroblog/
├── astro.config.mjs          ← Astro 主配置 (site/base/output)
├── package.json              ← 依赖与脚本
├── .npmrc                    ← npm legacy-peer-deps
├── .github/workflows/
│   └── deploy.yml            ← GitHub Pages 自动部署
│
├── src/
│   ├── config/               ← 🎛️ 你主要修改的配置区
│   │   ├── site.config.ts    ← 站点名称/作者/社交链接/品牌色
│   │   ├── nav.config.ts     ← 导航菜单和页脚链接
│   │   ├── i18n.config.ts    ← 多语言开关
│   │   └── consent.config.ts ← Cookie 同意弹窗
│   │
│   ├── pages/                ← 📄 页面路由 (文件即路由)
│   │   ├── index.astro       ← 首页 /
│   │   ├── about.astro       ← 关于 /
│   │   ├── services.astro    ← 服务 /
│   │   ├── projects/         ← 项目详情页 (动态路由)
│   │   ├── contact.astro     ← 联系 /
│   │   ├── components.astro  ← 组件展示页
│   │   ├── 404.astro         ← 404 页面
│   │   ├── blog/
│   │   │   ├── index.astro   ← 博客列表页
│   │   │   ├── page/[page].astro  ← 博客分页
│   │   │   ├── tag/[tag].astro    ← 标签归档
│   │   │   └── [...slug].astro    ← 单篇文章页
│   │   └── og/               ← OG 社交分享图生成
│   │
│   ├── content/              ← ✍️ 这里写内容！
│   │   ├── blog/en/          ← 🇬🇧 博客文章 (.mdx)
│   │   ├── projects/         ← 作品集项目 (.mdx)
│   │   ├── stack/            ← 技术栈展示 (.mdx)
│   │   ├── authors/          ← 作者信息 (.json)
│   │   ├── faqs/             ← FAQ 问答 (.json)
│   │   └── pages/            ← 预留内容页
│   │
│   ├── layouts/              ← 📐 页面布局框架
│   │   ├── BaseLayout.astro  ← 最底层的 HTML 骨架
│   │   ├── PageLayout.astro  ← 通用页面 (Header + Footer)
│   │   ├── BlogLayout.astro  ← 博客文章页专用
│   │   ├── LandingLayout.astro ← 首页落地页
│   │   ├── ProjectLayout.astro ← 项目详情页
│   │   └── MarketingLayout.astro ← 营销页面
│   │
│   ├── components/           ← 🧩 UI 组件库 (57+ 组件)
│   │   ├── blog/             ← BlogCard, TagList, Pagination 等
│   │   ├── layout/           ← Header, Footer, ThemeToggle
│   │   ├── ui/               ← 通用 UI: Button/Card/Avatar/Input...
│   │   ├── landing/          ← 首页专用: CTA, TechStack, Lighthouse
│   │   ├── hero/             ← Hero 区域 + 打字动画
│   │   ├── seo/              ← SEO, Breadcrumbs, JsonLd
│   │   ├── patterns/         ← 组合模式: ContactForm, Newsletter
│   │   └── effects/          ← 特效: 字符故障动画
│   │
│   ├── styles/               ← 🎨 样式系统
│   │   ├── global.css        ← 全局样式
│   │   ├── themes/           ← 12 套色彩主题 (蓝色默认)
│   │   └── tokens/           ← 设计令牌 (颜色/间距/字体)
│   │
│   ├── lib/                  ← 🔧 工具函数
│   │   ├── blog.ts           ← 博客查询/分页/标签/URL
│   │   ├── utils.ts          ← 通用工具
│   │   ├── cn.ts             ← className 合并
│   │   └── schema.ts         ← JSON-LD Schema
│   │
│   ├── i18n/                 ← 🌐 翻译文件
│   └── assets/               ← 🖼️ 图片资源
│       ├── blog/             ← 博客配图 SVG
│       └── projects/         ← 项目缩略图
│
└── public/                   ← 静态文件 (直接映射到网站根目录)
    ├── favicon.svg
    └── og-default.svg
```

---

## 你日常需要操作的文件

|做什么|去哪改|
| --------| -----------------------------------|
|**写博客**|​`src/content/blog/en/`​ 新建 `.mdx`|
|**改网站名/作者**|​`src/config/site.config.ts`|
|**改导航菜单**|​`src/config/nav.config.ts`|
|**添加项目**|​`src/content/projects/`​ 新建 `.mdx`|
|**添加技术栈**|​`src/content/stack/`​ 新建 `.mdx`|
|**换颜色主题**|页面顶部直接点击色块（12 色可选）|
|**换默认主题**|​`src/config/site.config.ts` 改 branding colors|

## 博客文章 Frontmatter

```yaml
---
title: "文章标题"
description: "SEO 摘要"
publishedAt: 2026-05-21
author: "docomola"
tags: ["标签1", "标签2"]
featured: true               # 可选，标记为精选
locale: en
image: "./cover.svg"         # 可选，文章配图
---
```
