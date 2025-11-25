---
title: 🔵Docusaurus 入门使用教程
sidebar_position: 1
permalink: /help/intro
id: help-intro
---
# Docusaurus 入门使用教程

## 什么是 Docusaurus？

Docusaurus 是由 Facebook（Meta）开源的一个现代化静态网站生成器，专门用于构建文档网站。它基于 React 构建，提供了开箱即用的功能，让你能够快速创建美观、易于维护的文档站点。

### 核心特性

- **简单易用**：使用 Markdown 编写文档
- **可定制化**：支持 React 组件和自定义页面
- **国际化**：内置多语言支持
- **版本控制**：支持文档多版本管理
- **全文搜索**：集成搜索功能
- **SEO 友好**：优化的 SEO 和性能
- **深色模式**：内置深色主题支持

## 环境准备

### 系统要求

- Node.js 版本 18.0 或以上
- npm 或 yarn 包管理器

### 检查环境

```bash
# 检查 Node.js 版本
node -v

# 检查 npm 版本
npm -v
```

## 快速开始

### 1. 创建新项目

使用官方脚手架快速创建项目：

```bash
# 使用 npx（推荐）
npx create-docusaurus@latest my-website classic

# 或使用 npm
npm init docusaurus@latest my-website classic

# 或使用 yarn
yarn create docusaurus my-website classic
```

参数说明：
- `my-website`：项目名称（可自定义）
- `classic`：使用经典模板（推荐新手使用）

### 2. 进入项目目录

```bash
cd my-website
```

### 3. 启动开发服务器

```bash
npm start
# 或
yarn start
```

浏览器会自动打开 `http://localhost:3000`，你将看到默认的 Docusaurus 网站。

## 项目结构详解

```
my-website/
├── blog/                    # 博客文章目录
│   ├── 2024-01-01-welcome.md
│   └── authors.yml         # 作者信息
├── docs/                    # 文档目录
│   ├── intro.md
│   └── tutorial-basics/
├── src/                     # 源代码目录
│   ├── components/         # React 组件
│   ├── css/               # 自定义样式
│   └── pages/             # 自定义页面
│       └── index.js       # 首页
├── static/                 # 静态资源
│   └── img/               # 图片资源
├── docusaurus.config.js   # 主配置文件
├── sidebars.js            # 侧边栏配置
├── package.json
└── README.md
```

### 重要文件说明

**docusaurus.config.js**：整个网站的核心配置文件，包括网站元数据、主题配置、插件等。

**sidebars.js**：控制文档侧边栏的结构和导航。

**docs/**：存放所有文档的 Markdown 文件。

**blog/**：存放博客文章的 Markdown 文件。

**src/pages/**：自定义页面，使用 React 或 Markdown 编写。

## 配置网站基本信息

编辑 `docusaurus.config.js` 文件：

```javascript
module.exports = {
  title: '我的网站',
  tagline: '一个很酷的标语',
  favicon: 'img/favicon.ico',

  // 网站的生产环境 URL
  url: 'https://your-docusaurus-site.com',
  // 网站的基础路径
  baseUrl: '/',

  // GitHub Pages 部署配置
  organizationName: 'your-org', // GitHub 组织/用户名
  projectName: 'your-repo',      // 仓库名

  // 国际化配置
  i18n: {
    defaultLocale: 'zh-CN',
    locales: ['zh-CN', 'en'],
  },

  presets: [
    [
      'classic',
      {
        docs: {
          sidebarPath: require.resolve('./sidebars.js'),
          // 编辑此页的链接
          editUrl: 'https://github.com/your-org/your-repo/tree/main/',
        },
        blog: {
          showReadingTime: true,
          editUrl: 'https://github.com/your-org/your-repo/tree/main/',
        },
        theme: {
          customCss: require.resolve('./src/css/custom.css'),
        },
      },
    ],
  ],

  themeConfig: {
    navbar: {
      title: '我的网站',
      logo: {
        alt: '网站 Logo',
        src: 'img/logo.svg',
      },
      items: [
        {
          type: 'docSidebar',
          sidebarId: 'tutorialSidebar',
          position: 'left',
          label: '教程',
        },
        {to: '/blog', label: '博客', position: 'left'},
        {
          href: 'https://github.com/your-org/your-repo',
          label: 'GitHub',
          position: 'right',
        },
      ],
    },
    footer: {
      style: 'dark',
      links: [
        {
          title: '文档',
          items: [
            {
              label: '教程',
              to: '/docs/intro',
            },
          ],
        },
        {
          title: '社区',
          items: [
            {
              label: 'Stack Overflow',
              href: 'https://stackoverflow.com/questions/tagged/docusaurus',
            },
          ],
        },
      ],
      copyright: `Copyright © ${new Date().getFullYear()} 我的项目`,
    },
  },
};
```

## 编写文档

### 创建新文档

在 `docs/` 目录下创建 Markdown 文件：

```markdown
---
id: my-doc
title: 我的文档标题
sidebar_label: 侧边栏显示名称
sidebar_position: 1
---

# 我的文档

这是文档内容...

## 二级标题

文档支持标准的 Markdown 语法。

### 代码块

\`\`\`javascript
function hello() {
  console.log('Hello Docusaurus!');
}
\`\`\`

### 告示框

:::note
这是一个提示框
:::

:::tip
这是一个技巧提示
:::

:::info
这是一个信息提示
:::

:::warning
这是一个警告
:::

:::danger
这是一个危险警告
:::
```

### Front Matter 参数

文档顶部的元数据（Front Matter）控制文档的行为：

- `id`：文档的唯一标识符
- `title`：文档标题
- `sidebar_label`：侧边栏中显示的名称
- `sidebar_position`：侧边栏中的排序位置
- `tags`：文档标签
- `description`：文档描述（用于 SEO）
- `keywords`：关键词列表

## 配置侧边栏

编辑 `sidebars.js` 文件：

```javascript
module.exports = {
  tutorialSidebar: [
    'intro', // 直接引用文档 ID
    {
      type: 'category',
      label: '基础教程',
      items: [
        'tutorial-basics/create-a-page',
        'tutorial-basics/create-a-document',
      ],
    },
    {
      type: 'category',
      label: '高级教程',
      collapsed: false, // 默认展开
      items: [
        'tutorial-advanced/advanced-feature-1',
        'tutorial-advanced/advanced-feature-2',
      ],
    },
  ],
};
```

### 自动生成侧边栏

使用 `autogenerated` 类型自动根据文件结构生成：

```javascript
module.exports = {
  tutorialSidebar: [
    {
      type: 'autogenerated',
      dirName: '.', // 自动生成 docs 目录下的所有文档
    },
  ],
};
```

## 编写博客

### 创建博客文章

在 `blog/` 目录下创建文件，命名格式：`YYYY-MM-DD-标题.md`

```markdown
---
slug: welcome
title: 欢迎使用博客
authors: [author-name]
tags: [hello, docusaurus]
---

这是博客文章的摘要，会显示在列表页。

<!-- truncate -->

这里是完整的文章内容...
```

### 配置作者信息

编辑 `blog/authors.yml`：

```yaml
author-name:
  name: 张三
  title: 前端工程师
  url: https://github.com/zhangsan
  image_url: https://github.com/zhangsan.png
  email: zhangsan@example.com
```

## 自定义页面

在 `src/pages/` 目录下创建自定义页面：

### React 页面示例

`src/pages/about.js`：

```jsx
import React from 'react';
import Layout from '@theme/Layout';

export default function About() {
  return (
    <Layout title="关于我们" description="关于页面描述">
      <div className="container margin-vert--lg">
        <h1>关于我们</h1>
        <p>这是一个自定义页面</p>
      </div>
    </Layout>
  );
}
```

访问路径：`http://localhost:3000/about`

### Markdown 页面示例

`src/pages/contact.md`：

```markdown
---
title: 联系我们
description: 联系方式
---

# 联系我们

- Email: contact@example.com
- GitHub: https://github.com/your-org
```

## 添加搜索功能

### 使用 Algolia DocSearch（推荐）

在 `docusaurus.config.js` 中添加：

```javascript
themeConfig: {
  algolia: {
    appId: 'YOUR_APP_ID',
    apiKey: 'YOUR_SEARCH_API_KEY',
    indexName: 'YOUR_INDEX_NAME',
    contextualSearch: true,
  },
}
```

申请 Algolia DocSearch：https://docsearch.algolia.com/

### 使用本地搜索插件

```bash
npm install @easyops-cn/docusaurus-search-local
```

配置：

```javascript
themes: [
  [
    require.resolve('@easyops-cn/docusaurus-search-local'),
    {
      hashed: true,
      language: ['zh', 'en'],
    },
  ],
],
```

## 多语言支持

### 1. 配置语言

在 `docusaurus.config.js` 中：

```javascript
i18n: {
  defaultLocale: 'zh-CN',
  locales: ['zh-CN', 'en'],
  localeConfigs: {
    'zh-CN': {
      label: '简体中文',
    },
    en: {
      label: 'English',
    },
  },
},
```

### 2. 创建翻译文件

```bash
npm run write-translations -- --locale en
```

这会生成 `i18n/en/` 目录结构。

### 3. 翻译文档

复制文档到对应语言目录：

```
i18n/
└── en/
    ├── docusaurus-plugin-content-docs/
    │   └── current/
    │       └── intro.md
    └── docusaurus-plugin-content-blog/
        └── 2024-01-01-welcome.md
```

## 部署网站

### 构建生产版本

```bash
npm run build
```

生成的静态文件在 `build/` 目录中。

### 部署到 GitHub Pages

#### 配置

在 `docusaurus.config.js` 中设置：

```javascript
url: 'https://your-username.github.io',
baseUrl: '/your-repo-name/',
organizationName: 'your-username',
projectName: 'your-repo-name',
```

#### 使用 GitHub Actions 自动部署

创建 `.github/workflows/deploy.yml`：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build website
        run: npm run build
      
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```

### 部署到 Vercel

1. 在 Vercel 导入你的 GitHub 仓库
2. Vercel 会自动检测 Docusaurus 项目
3. 点击部署即可

### 部署到 Netlify

1. 连接 GitHub 仓库
2. 构建命令：`npm run build`
3. 发布目录：`build`

## 常用插件

### PWA 支持

```bash
npm install @docusaurus/plugin-pwa
```

配置：

```javascript
plugins: [
  [
    '@docusaurus/plugin-pwa',
    {
      pwaHead: [
        {
          tagName: 'link',
          rel: 'icon',
          href: '/img/logo.png',
        },
        {
          tagName: 'link',
          rel: 'manifest',
          href: '/manifest.json',
        },
      ],
    },
  ],
],
```

### Google Analytics

```javascript
themeConfig: {
  gtag: {
    trackingID: 'G-XXXXXXXXXX',
    anonymizeIP: true,
  },
},
```

## 常用命令总结

```bash
# 启动开发服务器
npm start

# 构建生产版本
npm run build

# 本地预览生产版本
npm run serve

# 清除缓存
npm run clear

# 部署到 GitHub Pages
npm run deploy

# 生成翻译文件
npm run write-translations -- --locale en

# 更新 Docusaurus
npm update @docusaurus/core @docusaurus/preset-classic
```

## 最佳实践

### 1. 文档组织

- 使用清晰的目录结构
- 每个文档一个主题
- 合理使用 Front Matter
- 保持文档简洁易读

### 2. 性能优化

- 压缩图片资源
- 使用 WebP 格式图片
- 启用代码分割
- 利用 CDN 加速

### 3. SEO 优化

- 为每个页面设置合适的 title 和 description
- 使用语义化的 HTML 标签
- 添加 sitemap
- 设置正确的 canonical URL

### 4. 用户体验

- 提供清晰的导航
- 添加搜索功能
- 支持深色模式
- 确保移动端友好

## 常见问题

### 如何修改主题颜色？

编辑 `src/css/custom.css`：

```css
:root {
  --ifm-color-primary: #2e8555;
  --ifm-color-primary-dark: #29784c;
  --ifm-color-primary-darker: #277148;
  --ifm-color-primary-darkest: #205d3b;
  --ifm-color-primary-light: #33925d;
  --ifm-color-primary-lighter: #359962;
  --ifm-color-primary-lightest: #3cad6e;
}
```

### 如何添加自定义组件？

在 `src/components/` 创建组件，然后在 Markdown 中导入使用：

```markdown
import MyComponent from '@site/src/components/MyComponent';

<MyComponent />
```

### 如何隐藏某个页面？

在 Front Matter 中添加：

```markdown
---
unlisted: true
---
```

## 学习资源

- 官方文档：https://docusaurus.io/
- GitHub 仓库：https://github.com/facebook/docusaurus
- Discord 社区：https://discord.gg/docusaurus
- 示例网站：https://docusaurus.io/showcase

## 总结

Docusaurus 是一个功能强大且易于使用的文档网站生成器，特别适合技术文档、API 文档、产品文档等场景。通过本教程，你应该已经掌握了：

- 安装和配置 Docusaurus
- 创建和组织文档
- 自定义网站外观
- 添加博客和自定义页面
- 配置多语言支持
- 部署到各种平台

现在你可以开始创建自己的文档网站了！祝你使用愉快！