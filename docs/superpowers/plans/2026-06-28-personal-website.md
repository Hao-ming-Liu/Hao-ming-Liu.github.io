# 个人主页实现计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 从零构建一个单文件综合个人主页（首页 + 关于 + 博客 + 作品），纯 HTML/CSS/JS，无框架零依赖。

**Architecture:** 单个 `index.html` 文件，所有 CSS 写在 `<style>` 标签中，所有 JS 写在 `<script>` 标签中。四个页面内容分别放在四个 `<section>` 中，通过 JavaScript 控制显示/隐藏实现页面切换。URL hash（`#home`、`#about`、`#blog`、`#works`）支持浏览器前进/后退。

**Tech Stack:** HTML5 + CSS3 + Vanilla JavaScript（约 20 行）

## Global Constraints

- 单文件：所有 HTML、CSS、JS 都在 `index.html` 中
- 零外部依赖：不使用任何 CSS/JS 框架、字体、图标库
- 响应式断点：768px（>768px 桌面端，≤768px 移动端）
- 配色：背景 `#fafafa`，卡片 `#ffffff`，文字 `#2d2d2d`，强调 `#4a6cf7`，辅强调 `#6c63ff`
- 字体栈：`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
- 内容最大宽度：800px（桌面端居中）
- 导航最大宽度：960px（桌面端居中）
- 所有内容用占位文本，后续可替换
- 文件编码：UTF-8，语言：zh-CN

---

### Task 1: 创建 HTML 骨架 —— 导航栏 + 页面结构 + 页脚

**Files:**
- Create: `index.html`

**Interfaces:**
- Produces: HTML 文档基础结构，包含 `<nav>`、四个 `<section>`、`<footer>`，以及空的 `<style>` 和 `<script>` 标签供后续任务填充

- [ ] **Step 1: 写入完整的 HTML 骨架**

将以下内容写入 `index.html`：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>我的个人主页</title>
  <style>
    /* 后续任务将在此添加 CSS */
  </style>
</head>
<body>
  <!-- 导航栏 -->
  <nav id="navbar">
    <div class="nav-container">
      <a href="#home" class="nav-logo">你的名字</a>
      <ul class="nav-links">
        <li><a href="#home" class="nav-link active">首页</a></li>
        <li><a href="#about" class="nav-link">关于</a></li>
        <li><a href="#blog" class="nav-link">博客</a></li>
        <li><a href="#works" class="nav-link">作品</a></li>
      </ul>
    </div>
  </nav>

  <!-- 页面内容 -->
  <main>
    <!-- 首页 -->
    <section id="home" class="page">
      <div class="home-content">
        <img src="https://via.placeholder.com/120" alt="头像" class="avatar">
        <h1>你好，我是 ___</h1>
        <p class="tagline">一句介绍自己的话，比如：热爱编程的初学者 / 探索技术的乐趣</p>
        <div class="quick-links">
          <a href="#about" class="btn">关于我</a>
          <a href="#blog" class="btn">读博客</a>
          <a href="#works" class="btn">看作品</a>
        </div>
      </div>
    </section>

    <!-- 关于我 -->
    <section id="about" class="page">
      <h2>关于我</h2>
      <p>这里是一段自我介绍。你可以写写自己的背景、兴趣爱好、或者正在学习的东西。比如：我目前在学习 Web 开发，之前有一些 C/C++ 的编程经验，正在探索如何把自己的想法变成网页。</p>
      <p>这是第二段。可以写写你的目标、价值观、或者想通过这个网站分享什么。比如：我希望通过这个网站记录学习过程，分享一些有用的资源，也欢迎大家和我交流。</p>
      <h3>技能</h3>
      <div class="skills">
        <span class="skill-tag">C</span>
        <span class="skill-tag">C++</span>
        <span class="skill-tag">HTML</span>
        <span class="skill-tag">CSS</span>
      </div>
    </section>

    <!-- 博客 -->
    <section id="blog" class="page">
      <h2>博客</h2>
      <div class="blog-list">
        <article class="blog-card">
          <h3>我的第一篇文章</h3>
          <time datetime="2026-06-28">2026-06-28</time>
          <p>这是文章的摘要内容。写几句概括文章大意的话，让读者知道这篇文章讲了什么。点击可以阅读全文。</p>
        </article>
        <article class="blog-card">
          <h3>学习 Web 开发的第一周</h3>
          <time datetime="2026-06-21">2026-06-21</time>
          <p>记录一下刚开始学习 HTML 和 CSS 的过程，遇到了哪些问题，又是怎么解决的。</p>
        </article>
        <article class="blog-card">
          <h3>C++ 指针理解心得</h3>
          <time datetime="2026-06-15">2026-06-15</time>
          <p>最近终于搞懂了指针和引用的区别，写篇文章总结一下，防止以后忘记。</p>
        </article>
      </div>
    </section>

    <!-- 作品 -->
    <section id="works" class="page">
      <h2>作品</h2>
      <div class="works-grid">
        <div class="work-card">
          <h3>项目名称 1</h3>
          <p>项目的简短描述，说明它是什么、解决了什么问题。</p>
          <a href="#" class="work-link">查看详情 →</a>
        </div>
        <div class="work-card">
          <h3>项目名称 2</h3>
          <p>另一个项目的描述。这里可以写上你做过的小项目，比如课程设计、个人练习等。</p>
          <a href="#" class="work-link">查看详情 →</a>
        </div>
        <div class="work-card">
          <h3>项目名称 3</h3>
          <p>第三个项目的描述。先放占位内容，以后随时可以替换成真实项目。</p>
          <a href="#" class="work-link">查看详情 →</a>
        </div>
        <div class="work-card">
          <h3>项目名称 4</h3>
          <p>第四个项目的描述。即使还没有四个项目，也可以先写好框架。</p>
          <a href="#" class="work-link">查看详情 →</a>
        </div>
      </div>
    </section>
  </main>

  <!-- 页脚 -->
  <footer>
    <p>&copy; 2026 你的名字. 保留所有权利。</p>
  </footer>

  <script>
    /* 后续任务将在此添加 JavaScript */
  </script>
</body>
</html>
```

- [ ] **Step 2: 在浏览器中打开检查**

用浏览器打开 `index.html`，确认：
- 所有文字内容正确显示
- 四个页面区块同时可见（暂无样式，所以全部显示是正常的）
- 页面标题为"我的个人主页"

---

### Task 2: 添加全局 CSS —— 配色、字体、基础布局

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签内添加全局样式

**Interfaces:**
- Consumes: Task 1 的 HTML 结构
- Produces: 全局样式生效，页面背景色、字体、导航栏、页脚、内容区宽度可见

- [ ] **Step 1: 在 `<style>` 标签内添加全局样式**

打开 `index.html`，找到 `<style>` 标签，替换其内容为：

```css
/* === 全局重置 & 基础 === */
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  background-color: #fafafa;
  color: #2d2d2d;
  line-height: 1.7;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* === 导航栏 === */
#navbar {
  position: sticky;
  top: 0;
  background: rgba(255, 255, 255, 0.92);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.06);
  z-index: 100;
}

.nav-container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 60px;
}

.nav-logo {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2d2d2d;
  text-decoration: none;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 32px;
}

.nav-link {
  color: #555;
  text-decoration: none;
  font-size: 0.95rem;
  padding-bottom: 4px;
  border-bottom: 2px solid transparent;
  transition: color 0.2s, border-color 0.2s;
}

.nav-link:hover {
  color: #4a6cf7;
}

.nav-link.active {
  color: #4a6cf7;
  border-bottom-color: #4a6cf7;
}

/* === 主体内容区 === */
main {
  flex: 1;
  max-width: 800px;
  width: 100%;
  margin: 0 auto;
  padding: 60px 24px;
}

.page {
  /* 默认全部隐藏，由 JS 控制显示 */
  display: none;
}

.page.active {
  display: block;
}

/* 默认显示首页（JS 加载前） */
#home {
  display: block;
}

/* === 页脚 === */
footer {
  text-align: center;
  padding: 32px 24px;
  color: #999;
  font-size: 0.85rem;
  border-top: 1px solid rgba(0, 0, 0, 0.05);
}
```

- [ ] **Step 2: 刷新浏览器检查**

用浏览器刷新 `index.html`，确认：
- 页面背景变为极浅灰色（`#fafafa`）
- 导航栏固定在顶部，白色半透明背景
- 导航栏宽度限制在 960px 内，居中
- 内容区宽度限制在 800px 内，居中
- 字体变为系统默认无衬线字体
- 页脚有上边框，文字灰色居中
- 所有四个页面区块仍然可见（因为还没有 JS 控制）

---

### Task 3: 添加首页 CSS —— 头像、标题、按钮

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签末尾追加首页相关样式

**Interfaces:**
- Consumes: Task 2 的全局样式
- Produces: 首页视觉完成——头像圆形、标题醒目、三个按钮排列美观

- [ ] **Step 1: 在 `</style>` 之前追加首页样式**

```css
/* === 首页 === */
.home-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 180px);
  text-align: center;
}

.avatar {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 28px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.home-content h1 {
  font-size: 2.2rem;
  font-weight: 700;
  margin-bottom: 12px;
  color: #2d2d2d;
}

.tagline {
  font-size: 1.1rem;
  color: #666;
  margin-bottom: 36px;
  max-width: 400px;
}

.quick-links {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  justify-content: center;
}

.btn {
  display: inline-block;
  padding: 12px 28px;
  background: #4a6cf7;
  color: #fff;
  text-decoration: none;
  border-radius: 6px;
  font-size: 0.95rem;
  font-weight: 500;
  transition: background 0.2s, transform 0.2s;
}

.btn:hover {
  background: #6c63ff;
  transform: translateY(-2px);
}
```

- [ ] **Step 2: 刷新浏览器检查**

确认：
- 头像变成圆形（120×120px），有柔和阴影
- 名字用大号粗体显示
- 三个按钮水平排列，蓝色背景白色文字
- 鼠标悬停按钮时背景变紫色并微微上浮
- 首页整体在垂直方向居中

---

### Task 4: 添加关于页 CSS —— 标签、段落

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签末尾追加关于页样式

**Interfaces:**
- Consumes: Task 2 全局样式
- Produces: 关于页样式完成——段落排版、技能标签排列

- [ ] **Step 1: 在 `</style>` 之前追加关于页样式**

```css
/* === 关于我 === */
.page h2 {
  font-size: 1.8rem;
  margin-bottom: 24px;
  color: #2d2d2d;
}

.page p {
  margin-bottom: 18px;
  color: #444;
  font-size: 1rem;
  max-width: 650px;
}

.page h3 {
  font-size: 1.2rem;
  margin-top: 32px;
  margin-bottom: 14px;
  color: #2d2d2d;
}

.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.skill-tag {
  display: inline-block;
  padding: 6px 16px;
  background: #eef1ff;
  color: #4a6cf7;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
}
```

- [ ] **Step 2: 刷新浏览器检查**

确认：
- 关于页标题大号粗体
- 段落文字颜色比标题浅，行间距舒适
- 技能标签显示为圆角药丸形状，浅蓝背景蓝色文字
- 标签水平排列，自动换行

---

### Task 5: 添加博客页 CSS —— 卡片样式

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签末尾追加博客页样式

**Interfaces:**
- Consumes: Task 2 全局样式
- Produces: 博客卡片样式完成——白色卡片、日期、悬停效果

- [ ] **Step 1: 在 `</style>` 之前追加博客页样式**

```css
/* === 博客 === */
.blog-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.blog-card {
  background: #ffffff;
  padding: 28px 32px;
  border-radius: 10px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}

.blog-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
}

.blog-card h3 {
  font-size: 1.2rem;
  margin: 0 0 8px 0;
  color: #2d2d2d;
}

.blog-card time {
  display: block;
  font-size: 0.85rem;
  color: #999;
  margin-bottom: 12px;
}

.blog-card p {
  font-size: 0.95rem;
  color: #555;
  line-height: 1.6;
}
```

- [ ] **Step 2: 刷新浏览器检查**

确认：
- 每篇文章显示为白色卡片，有圆角和轻微阴影
- 卡片之间均匀间隔
- 鼠标悬停时卡片微微上浮，阴影加深
- 日期灰色小字显示在标题下方

---

### Task 6: 添加作品页 CSS —— 网格布局

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签末尾追加作品页样式

**Interfaces:**
- Consumes: Task 2 全局样式
- Produces: 作品卡片网格完成——桌面端两列、链接样式

- [ ] **Step 1: 在 `</style>` 之前追加作品页样式**

```css
/* === 作品 === */
.works-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

.work-card {
  background: #ffffff;
  padding: 28px;
  border-radius: 10px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s, box-shadow 0.2s;
}

.work-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
}

.work-card h3 {
  font-size: 1.1rem;
  margin-bottom: 10px;
  color: #2d2d2d;
}

.work-card p {
  font-size: 0.9rem;
  color: #555;
  margin-bottom: 16px;
  line-height: 1.6;
}

.work-link {
  color: #4a6cf7;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  transition: color 0.2s;
}

.work-link:hover {
  color: #6c63ff;
}
```

- [ ] **Step 2: 刷新浏览器检查**

确认：
- 项目卡片以两列网格排列
- 每张卡片白色背景，圆角阴影
- 悬停效果与博客卡片一致
- "查看详情 →" 链接蓝色，悬停变为紫色

---

### Task 7: 添加响应式 CSS + 导航 JavaScript

**Files:**
- Modify: `index.html` —— 在 `<style>` 标签末尾追加响应式样式，在 `<script>` 标签内写入导航逻辑

**Interfaces:**
- Consumes: Task 2~6 的所有样式
- Produces: 手机端正常显示、导航可点击切换页面、URL hash 支持浏览器前进/后退

- [ ] **Step 1: 在 `</style>` 之前追加响应式 CSS**

```css
/* === 响应式：手机端 === */
@media (max-width: 768px) {
  .nav-container {
    flex-direction: column;
    height: auto;
    padding: 16px 24px;
    gap: 12px;
  }

  .nav-links {
    gap: 20px;
  }

  main {
    padding: 40px 20px;
  }

  .home-content h1 {
    font-size: 1.7rem;
  }

  .works-grid {
    grid-template-columns: 1fr;
  }

  footer {
    padding: 24px 20px;
  }
}
```

- [ ] **Step 2: 在 `<script>` 标签内写入导航 JS**

```javascript
// 页面导航切换
function switchPage(hash) {
  // 隐藏所有页面
  document.querySelectorAll('.page').forEach(function(page) {
    page.classList.remove('active');
  });

  // 移除所有导航高亮
  document.querySelectorAll('.nav-link').forEach(function(link) {
    link.classList.remove('active');
  });

  // 显示目标页面
  var target = document.querySelector(hash);
  if (target) {
    target.classList.add('active');
  }

  // 高亮对应导航
  var activeLink = document.querySelector('.nav-link[href="' + hash + '"]');
  if (activeLink) {
    activeLink.classList.add('active');
  }
}

// 监听导航点击
document.querySelectorAll('.nav-link').forEach(function(link) {
  link.addEventListener('click', function(e) {
    e.preventDefault();
    var hash = this.getAttribute('href');
    window.location.hash = hash;
    switchPage(hash);
  });
});

// 监听快捷按钮点击（首页的三个按钮）
document.querySelectorAll('.btn[href^="#"]').forEach(function(btn) {
  btn.addEventListener('click', function(e) {
    e.preventDefault();
    var hash = this.getAttribute('href');
    window.location.hash = hash;
    switchPage(hash);
  });
});

// 页面加载时根据 URL hash 显示对应页面
var initialHash = window.location.hash || '#home';
switchPage(initialHash);

// 浏览器前进/后退时更新页面
window.addEventListener('hashchange', function() {
  switchPage(window.location.hash);
});
```

- [ ] **Step 3: 刷新浏览器测试所有功能**

进行以下检查：

1. **导航切换**：依次点击"首页""关于""博客""作品"，确认每次只显示对应页面内容
2. **导航高亮**：当前选中的导航项有蓝色下划线
3. **快捷按钮**：在首页点击"关于我""读博客""看作品"按钮，确认跳转正确
4. **浏览器前进/后退**：点击几次导航后，使用浏览器的前进/后退按钮，确认页面正确切换
5. **手机端效果**：缩小浏览器窗口到 768px 以下，确认：
   - 导航栏变为竖排
   - 作品卡片变为单列
   - 字体大小适配手机

---

### Task 8: 启动预览服务器 & 最终检查

**Files:**
- Create: 无新文件

**Interfaces:**
- Consumes: 完整的 `index.html`

- [ ] **Step 1: 启动本地 HTTP 服务器**

```bash
cd "c:/studyy/Vscode/code/wangzhan"
python -m http.server 8080
```

- [ ] **Step 2: 在浏览器中打开**

访问 `http://localhost:8080`，在桌面端和手机端（或用浏览器开发者工具的移动视图）分别检查：

| 检查项 | 预期 |
|--------|------|
| 首页头像圆形、居中 | ✓ |
| 三个按钮悬停效果 | ✓ |
| 导航四个标签切换正常 | ✓ |
| URL 栏显示对应 hash | ✓ |
| 前进/后退按钮正常 | ✓ |
| 关于页技能标签圆角 | ✓ |
| 博客卡片悬停上浮 | ✓ |
| 作品网格两列排列 | ✓ |
| 手机端排版适配 | ✓ |
| 配色统一、无突兀元素 | ✓ |

- [ ] **Step 3: 发现问题则回到对应 Task 修复**

如果有任何不符合预期的表现，定位到对应 CSS/JS 代码进行修正。

- [ ] **Step 4: 确认完成**

所有检查项通过后，项目可交付。
