# AGENTS.md — hai-an-read（《海峡的另一边》样章阅读页）

面向所有在这个仓库干活的人与 AI（Hermes、ChatGPT、Meta AI …）。动手前先读这份。

## 这是什么
长篇小说的**免费样章阅读页**，纯静态（GitHub Pages）。中文长文排版：衬线字体、1.95 行距、
首行缩进 2em、最大宽度 36rem。
线上：https://yanbing2026.github.io/hai-an-read/

## 构建
章节 HTML 是**生成物**，由生成器从手稿 markdown 渲染：
```sh
novel-site-build.py --chapters 1,2,3 [--author 笔名]
```
读 `src/chapter0N.md` → 重新生成 `ch0N.html`（标题取自 md 的 `#` 行，正文转义，`---` 为分场符，
`>` 为引用块）。
⚠️ **生成器 `novel-site-build.py` 不在本仓库里**（只在作者本机跑）。所以：
- **不要手改 `ch0N.html`** —— 它是生成物，下次重建就没了。
- 改正文 = 改 `src/chapter0N.md`，然后在**有生成器的机器上**重跑生成器。
- 没有生成器可用时，只改 `index.html`（手写落地页），不要临时手写章节 HTML。

## 测试
无自动化测试、无 lint。改完在浏览器里看：目录跳转、每章排版（行距/缩进/分场符）、移动端宽度。

## 发布
GitHub Pages，source = `main` / 根目录（legacy，`.nojekyll` 已存在），无 CI workflow。
合并进 `main` 即上线。

## 绝不手改的生成文件
`ch01.html`、`ch02.html`、`ch03.html`（后续章节同理）。`src/*.md` 是正文唯一真源。

## 版权
所有文字版权归作者所有，谢绝转载与商业使用。不要把这些正文复制到别的仓库/站点。

## 流程（main 已保护）
1. 开分支 → 提交 → 开 PR。**不要直接推 `main`**（已禁止直推/强推/删分支，对管理员同样生效）。
2. PR 里写清：改的是正文源（`src/*.md`）、排版还是落地页，以及重跑生成器的命令与结果。
