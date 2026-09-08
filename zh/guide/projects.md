# 项目

通过内容集合 `src/content/projects/` 管理，展示你开发的个人项目。每个项目是一个 `.md` / `.mdx` 文件，**正文就是项目 README**，会渲染在详情页底部；frontmatter 里的字段用于列表卡片与详情页顶部展示。

## 创建项目

在 `src/content/projects/` 下新建一个 `.md` 或 `.mdx` 文件即可创建一个项目。

- 列表页 `/projects/`：卡片网格，支持按状态筛选 + 名称/描述/标签搜索。
- 详情页 `/projects/<slug>/`：封面（可点开灯箱放大）、状态徽标、项目名、描述、日期/标签、外链按钮，底部渲染 README 正文。

## Frontmatter 字段

| 字段 | 类型 | 说明 |
|------|------|------|
| `title` | `string` | 必填。项目名称。 |
| `slug` | string | 可选，和文章一样使用。 |
| `published` | `date` | 必填。发布/更新日期，如 `2025-10-01`。用于排序（配合 `order`）。 |
| `draft` | `boolean` | 可选，默认 `false`。设为 `true` 时生产构建会隐藏该页。 |
| `order` | `number` | 可选。手动排序权重，**越大越靠前**；未设置则按 `published` 降序。 |
| `description` | `string` | 可选。卡片简介 + 详情页描述。 |
| `image` | `string` | 可选。封面图。支持完整 URL、公共根路径 `/images/xxx.png`、相对路径（相对本文件目录，如 `images/xxx.png`）；留空则不显示封面。 |
| `tags` | `string[]` | 可选。标签。 |
| `link` | `array` | 可选。外链按钮数组：`{ label, icon, value }`。`icon` 可用 astro-icon 名（如 `fa7-brands:github`）、图片 URL，或留空用 `label` 首字母。 |
| `status` | `string` | 可选。项目状态，用标准 key（见下表）。 |
| `lang` | `string` | 可选。页面语言，如 `zh_CN`。 |

## 状态键值（status）

`status` 使用**标准 key**，前台会按站点语言显示本地化文案，并按状态自动配色 + 图标：

| key | 含义 |
|------|------|
| `planning` | 计划中 |
| `developing` | 开发中 |
| `published` | 已发布 |
| `archived` | 已归档 |

未知或自定义字符串会原样显示（中性灰），且不参与列表页的状态筛选。

## 示例

````yaml
---
title: "Firefly"
slug: firefly
published: 2025-10-01
draft: false
order: 100
description: "一个功能丰富的开源博客主题。"
image: "images/firefly.avif"
status: "published"
tags:
  - Astro
  - Svelte
link:
  - label: "GitHub"
    icon: "fa7-brands:github"
    value: "https://github.com/CuteLeaf/Firefly"
  - label: "文档"
    icon: "material-symbols:menu-book"
    value: "https://docs-firefly.cuteleaf.cn"
lang: ""
---

# Firefly

Firefly 是一款基于 Astro 框架和 Fuwari 模板开发的个人博客主题模板。
````

## 排序 / 筛选 / 搜索

- **排序**：`order` 降序（越大越靠前）→ `published` 降序 → 标题兜底。
- **状态筛选**：列表页顶部提供「全部 / 各状态」胶囊，点击按 `status` 过滤。
- **搜索**：列表页搜索框按项目名、描述、标签即时过滤，与状态筛选叠加。
