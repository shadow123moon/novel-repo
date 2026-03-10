# 发布流程（纯静态站 / GitHub Pages）

本仓库用于小说《临川无证之夜》的创作与发布。

- **源稿（写作区）**：`chapters/` 下的 `chapter-XXX.md`
- **发布站（静态站）**：`docs/`（GitHub Pages 可直接发布 `/docs`）

---

## 0. 目录结构（你需要记住的）

- `chapters/chapter-001.md`：章节源稿（Markdown）
- `docs/index.html`：主页（目录 + 简介 + 按钮）
- `docs/chapters/chapter-001.html`：章节发布页（HTML）
- `docs/assets/style.css`：全站样式

> 约定：章节文件名统一 `chapter-XXX`（三位数字）。

---

## 1) 新增/更新一章（推荐步骤）

### Step A：写/改源稿（Markdown）

1. 在 `chapters/` 新建或修改：
   - 新章：`chapters/chapter-002.md`
   - 修订旧章：`chapters/chapter-001.md`

### Step B：同步到发布页（HTML）

1. 复制一份上一章的发布页作为模板：
   - 例如把 `docs/chapters/chapter-001.html` 复制为 `docs/chapters/chapter-002.html`
2. 仅替换以下信息（尽量保持结构不变，方便统一样式）：
   - `<title>`（浏览器标题）
   - 章节号（如“第002章”）
   - 主标题（如《坏灯》）
   - 摘要/引子（`chapter-summary` / `chapter-intro`）
   - 正文段落（`reading-content` 内的 `<p>...</p>`）
3. **确认样式引用路径正确**：
   - 章节页必须是：`<link rel="stylesheet" href="../assets/style.css">`

> 说明：当前仓库没有自动从 Markdown 生成 HTML 的脚本，所以这一步是手动同步（后续如果需要可再加一个简单生成脚本，但现在先保持纯静态、无依赖）。

### Step C：更新主页目录（index）

1. 打开 `docs/index.html`
2. 在“章节目录”区域（`<ol class="chapter-list">`）追加一个 `<li>`：
   - 链接指向新章节：`chapters/chapter-002.html`
   - 更新章节号、标题、简介
3. （可选）把主页“开始阅读”按钮改为指向最新章。

---

## 2) 本地预览（不需要任何依赖）

- 直接用浏览器打开：
  - `docs/index.html`
- 点目录卡片确认：
  - 链接是否正确
  - 样式是否加载（章节页是否引用 `../assets/style.css`）

---

## 3) GitHub Pages 部署（建议）

1. 把仓库推到 GitHub（main/master 分支）
2. 仓库 Settings → Pages：
   - Source: **Deploy from a branch**
   - Branch: `main`（或 `master`）
   - Folder: `/docs`
3. 之后每次 `git push`，Pages 会自动更新站点。

---

## 4) 小检查清单（每次发布前 30 秒）

- [ ] `docs/index.html` 里目录新增条目已加入
- [ ] 新章节页路径：`docs/chapters/chapter-XXX.html`
- [ ] 新章节页 CSS 引用：`../assets/style.css`
- [ ] 首页按钮（开始阅读 / 最近更新）指向正确
