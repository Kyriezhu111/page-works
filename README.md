# 页工坊 · 学生网页工单

一份可以直接发给客户的网页作品集：一个主站 + 三份样片 + 一个可点的 React 原型。

全部是**单文件 HTML**，不依赖任何外部图片、字体或 CDN。下载下来双击就能看，部署到任何静态托管都能跑。

## 目录结构

| 路径 | 是什么 |
|---|---|
| `index.html` | 主站：能力介绍、**三份样片预览**、工具箱、交付流程、产品 UI 演示、React 原型、质检记录、行情问答、**联系方式** |
| `works/club-recruit.html` | 样片 01 · 社团招新页（夜空视觉、实时倒计时、表单校验） |
| `works/portfolio.html` | 样片 02 · 个人作品集（编辑风排版、作品筛选、就地展开详情） |
| `works/shop.html` | 样片 03 · 小店门面页（暖色调、实时营业状态、菜单切换、位置示意） |
| `prototype-quote.html` | React 18 + TS + Tailwind + shadcn/ui 打包成的单文件「页面报价」交互原型 |
| `assets/` | 品牌矢量标记、favicon（16/32/180）、1200×630 社交分享封面 |
| `web-design-review-2026-09-09.md` | 第一轮质检报告（主站），用 review-ui-design 走查 |
| `web-design-review-2026-09-27-samples.md` | 第二轮质检报告（三份样片），含 109 组对比度实测 |
| `web-design-review-2026-09-27-recheck.md` | 复评报告（全部四页）：12 项状态对照 + 3 项复评新发现 |
| `review-v1-status.png` / `review-v2-status.png` | 第一轮的问题标注图 |
| `review-v3-samples-annotated.png` | 第二轮问题标注图（7 个面板，1520×5252） |
| `review-v3-samples-suggestion.png` | 第二轮优化建议图（四组改前/改后色值，含实测比值） |
| `review-v4-recheck-status.png` | 复评状态图（12 项状态 + 6 张修复实证） |

## 联系方式

已经填好，无需再改：微信号 `zwx-hh0122`、邮箱 `2572892063@qq.com`，两处都带一键复制按钮。

若日后想换成二维码：把二维码图存成 `assets/wechat-qr.png`，在 `#contact` 区的 `.wx-card` 里加一段 `<img src="assets/wechat-qr.png" alt="微信二维码" width="148">` 即可。目前刻意没放二维码占位方块——一个空的虚线框在对外页面上看起来像没做完。

样片里的社团、店铺、人名、地址**全部是虚构的**，只用来演示版式和交互。如果你要拿去当真实案例展示，请替换成自己做过的真项目——这是底线。

## 本地预览

直接双击 `index.html` 即可。若想本地起服务：

```
python -m http.server 8000
```

然后打开 `http://localhost:8000`。

## 设计要点

- 视觉方向：纸感米白 + 墨色 + 印章红，工单/票据母题贯穿全站
- 三份样片刻意用了三套**完全不同**的视觉语言，用来证明风格适应能力
- 无障碍：正文与强调色对比度均达 WCAG AA（正文 5.52:1，强调 5.85:1）
- 全站 4 页共 198 组「前景/背景/字号/字重」色对全部达 AA，最低 4.81:1
- 响应式：桌面 / 平板 / 390px 手机三档，无横向溢出
- 键盘可达，`prefers-reduced-motion` 下自动关闭动效

## 技术说明

- `index.html` 里嵌了 3 个 iframe 做样片实时预览，用 JS 按卡片宽度等比缩放（基准宽 1400px）
- `prototype-quote.html` 由 Vite 构建 + html-inline 内联产出，源码工程未随仓库提供
- 滚动揭示动画带 1.2s 兜底全显 + `beforeprint` 钩子，截图和打印不会出现空白区
