# 沉浸阅读

沉浸阅读（Immersive Reading）让文章详情页进入「类 PDF」的专注阅读模式：只保留文章卡片居中阅读，外加一条常驻目录栏，隐藏导航栏、侧边栏、页脚、壁纸等所有干扰项，并在右下角提供进入/退出入口。

## 配置文件

`src/config/siteConfig.ts` → `siteConfig.post.immersiveReading`

## 配置项

| 属性 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `enable` | `boolean` | `true` | 总开关。设为 `false` 时不渲染按钮 |
| `defaultOn` | `boolean` | `false` | 进入文章页是否默认开启沉浸阅读 |
| `tocEnabled` | `boolean` | `true` | 沉浸阅读中是否显示目录栏 |
| `tocPosition` | `"left" \| "right"` | `"left"` | 目录栏位置 |

## 使用说明

- 文章详情页右下角新增「沉浸阅读」按钮，点击进入沉浸态；再次点击或按 `Esc` 退出，并恢复进入前的滚动位置。
- 沉浸态仅保留文章卡片 + 目录栏（左侧或右侧）；导航栏、壁纸、水波纹、渐变、侧边栏、页脚等全部隐藏，阅读面始终为不透明底色，与壁纸模式无关。
- 目录栏默认展开，可通过「目录开关」按钮或目录面板右上角的折叠按钮展开/收起；收起后文章让位空间随之释放。
- 沉浸阅读**仅桌面端**（窗口宽度 ≥ 1024px）可用，移动端不显示按钮。
- 悬浮在按钮上会显示对应提示：进入/退出沉浸阅读、展开/折叠目录。

::: tip
相关实现：逻辑在 `src/utils/immersive-reading-utils.ts`，样式在 `src/styles/immersive-reading.css`，按钮组件为 `src/components/controls/ImmersiveReading.astro`，目录栏组件为 `src/components/controls/ImmersiveTOC.astro`。
:::

## 示例

```ts
// src/config/siteConfig.ts
post: {
  immersiveReading: {
    enable: true,
    defaultOn: false,
    tocEnabled: true,
    tocPosition: "left",
  },
},
```
