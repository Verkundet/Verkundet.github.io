---
name: volantis-blog
description: 维护本站（Hexo 7 + Volantis 主题）博客。当需要新建/编辑文章、修改站点或主题配置、安装插件、本地预览、生成静态文件或部署到 GitHub Pages 时使用。
---

# Volantis 博客维护

本站基于 **Hexo 7.3.0 + Volantis 主题**（`hexo-theme-volantis@5.8.1`）。

## 站点结构

| 路径 | 作用 |
| --- | --- |
| `_config.yml` | Hexo 主配置（站点信息、URL、主题名、部署目标） |
| `_config.volantis.yml` | Volantis 主题配置（导航栏、封面、页脚、插件开关），**覆盖**主题默认 `_config.yml` |
| `source/_posts/` | 文章（Markdown） |
| `source/about/` `friends/` `categories/` `tags/` `archives/` `more/` | 各独立页面 |
| `source/_data/friends.yaml` | 友链数据 |
| `source/images/` | 站点图片（封面 `主页.jpg` 等） |
| `scaffolds/` | `hexo new` 的模板 |
| `themes/` | 为空；主题通过 npm 装在 `node_modules/hexo-theme-volantis` |

## 常用命令

- `hexo new "文章标题"` — 新建文章（`layout: post`，输出到 `source/_posts/`）
- `hexo new page "页面名"` — 新建独立页面
- `hexo server` / `hexo s` — 本地预览（默认 http://localhost:4000）
- `hexo clean` — 清理 `public/` 与缓存
- `hexo generate` / `hexo g` — 生成静态文件到 `public/`
- `hexo deploy` / `hexo d` — 部署到 GitHub Pages
- 一键发布：`hexo clean && hexo g && hexo d`

## 文章 front-matter

```yaml
---
title: 文章标题
date: 2026-08-17 04:12:00   # 注意是 date:，不是 data:
tags:
  - 标签1
  - 标签2
categories:
  - 分类1
# 可选：
cover: true            # 文章页显示封面
seo_title:             # 单独设置 SEO 标题
description:           # 摘要 / SEO 描述
excerpt:               # 列表页摘要
bottom_meta: false     # 关闭文章底部 meta
sidebar: []            # 关闭侧边栏
comments: false        # 关闭评论
---
```

## 主题配置要点（`_config.volantis.yml`）

- `navbar.menu` — 导航栏菜单；URL 末尾建议带 `/`
- `cover` — 首页封面（`title` / `background` / `layout_scheme` / `height_scheme`）
- `site_footer` — 页脚（`social`、`copyright`、`layout`）
- `comments.service` — 评论系统（giscus / artalk / waline），需自行填写对应 ID
- `search.enable` — 站内搜索，依赖 `hexo-generator-json-content`
- `plugins.*` — 各类增强插件开关（懒加载、代码高亮、字数统计等）

## 可选但常用的插件

| 功能 | 命令 |
| --- | --- |
| 站内搜索 | `npm i hexo-generator-json-content` |
| 文章字数统计（`counter`） | `npm i hexo-wordcount` |
| RSS 订阅（`atom.xml`） | `npm i hexo-generator-feed` |
| 相关文章推荐 | `npm i hexo-related-popular-posts` |

## 部署

- 目标：`git@github.com:Verkundet/Verkundet.github.io.git`（branch: `main`）
- 站点 URL：`https://verkundet.github.io`
- 使用 `hexo-deployer-git`，产物在 `.deploy_git/`

## 官方文档

- 入门：https://volantis.js.org/v6/getting-started/
- 备用镜像：https://vlts.cc 、 https://volantis.vercel.app
- 主题仓库：https://github.com/volantis-x/hexo-theme-volantis
