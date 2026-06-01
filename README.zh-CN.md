# 个人主页编辑指南（中文）

本项目基于 [Academic Pages](https://github.com/academicpages/academicpages.github.io) 模板（由 Minimal Mistakes 主题派生），是一个用于**学术 / 个人作品集**的 GitHub Pages 静态网站。

核心理念：**内容与样式分离**。你只需要编辑 Markdown（`.md`）和 YAML（`.yml`）文件来填写内容，主题会自动把它们生成为网页。你几乎不需要碰 HTML/CSS。

---

## 一、整体结构速览

| 路径 | 作用 | 你需要改吗 |
| --- | --- | --- |
| `_config.yml` | **全站配置**：站点标题、你的名字、头像、侧边栏社交链接等 | ✅ 必改 |
| `_data/navigation.yml` | **顶部导航栏**菜单项 | ✅ 按需 |
| `_pages/about.md` | **首页内容**（permalink 为 `/`） | ✅ 必改 |
| `_publications/` | 论文 / 出版物，每篇一个 `.md` | ✅ |
| `_talks/` | 学术报告 / 演讲 | ✅ |
| `_teaching/` | 教学经历 | ✅ |
| `_portfolio/` | 项目 / 作品集 | 可选 |
| `_posts/` | 博客文章 | 可选 |
| `_pages/cv.md` | 简历（CV）页面 | ✅ |
| `files/` | 你的 PDF、slides、bib 等文件 | ✅ 上传 |
| `images/` | 图片，如头像 `profile.png` | ✅ |
| `_layouts/`、`_includes/`、`_sass/`、`assets/` | 主题模板与样式 | ❌ 一般不动 |

> 内容文件顶部用 `---` 包裹的部分叫 **front matter（YAML 元数据）**，主题靠它来排版；`---` 之后是正文 Markdown。

---

## 二、第一步：改全站配置 `_config.yml`

打开 `_config.yml`，把默认值换成你自己的信息。关键字段：

```yaml
title    : "你的名字 / 站点标题"
name     : &name "你的名字"
description : "你的学术主页"
url      : https://你的GitHub用户名.github.io   # 网站地址
repository : "你的GitHub用户名/你的GitHub用户名.github.io"

author:
  avatar    : "profile.png"          # 头像文件名，放在 images/ 下
  name      : "侧边栏显示的名字"
  bio       : "一句话简介"
  location  : "城市 / 国家"
  employer  : "所在单位"
  email     : "you@example.com"

  # 学术 / 社交链接：填了才显示，留空则该图标隐藏
  googlescholar : "https://scholar.google.com/citations?user=XXXX"
  orcid         : "https://orcid.org/XXXX"
  github        : "你的GitHub用户名"
  linkedin      : "你的LinkedIn用户名"
```

侧边栏支持几十种链接（GitHub、Twitter/X、知乎、微博、Bilibili 没有但有 YouTube 等）。**规则：填上值就显示对应图标，留空就隐藏。**

> 📌 **以后想加 arXiv / Google Scholar / ORCID 链接？**
> 都在 `_config.yml` 的 `author:` 这一段里改，目前先留空了，等你有了主页地址再填即可：
> ```yaml
> author:
>   arxiv         :   # 例如 https://arxiv.org/a/你的ID
>   googlescholar :   # 例如 https://scholar.google.com/citations?user=你的ID
>   orcid         :   # 例如 https://orcid.org/0000-0000-0000-0000
> ```
> 填上后侧边栏会自动出现对应图标；另外只要填了 `googlescholar`，**Publications 页面顶部**还会自动出现一句 “You can also find my articles on my Google Scholar profile”。

> ⚠️ 修改 `_config.yml` 后，本地预览必须**重启服务**才生效（其他 `.md` 文件改动会自动刷新）。

---

## 三、改首页：`_pages/about.md`

`permalink: /` 表示这是网站首页。直接把正文部分替换为你自己的介绍即可，正文是标准 Markdown：

```markdown
---
permalink: /
title: "你的名字"
author_profile: true
---

这里写你的自我介绍、研究方向、近况等。

研究兴趣
======
- 方向一
- 方向二

[查看我的 CV](/cv/) ｜ [Google Scholar](https://scholar.google.com/...)
```

---

## 四、添加内容（论文 / 报告 / 教学等）

每条内容 = 对应目录下的**一个 Markdown 文件**。命名习惯：`日期-标题.md`（如 `2025-06-08-my-paper.md`），日期会用于排序。

### 1. 添加论文 → `_publications/`

复制一个现有文件改内容：

```markdown
---
title: "论文标题"
collection: publications
category: conferences      # books / manuscripts(期刊) / conferences(会议)
permalink: /publication/2025-06-08-my-paper
excerpt: '一句话摘要'
date: 2025-06-08
venue: '会议或期刊名称'
paperurl: 'https://你的用户名.github.io/files/paper.pdf'
citation: '作者. (2025). "论文标题." <i>期刊</i>. 卷(期).'
---

这里可以写论文的详细介绍（点进单篇页面时显示）。
```

- `category` 的取值（books / manuscripts / conferences）及其显示标题在 `_config.yml` 的 `publication_category` 中定义。
- PDF 先上传到 `files/` 目录，链接形如 `https://你的用户名.github.io/files/xxx.pdf`。也可以直接用外部链接（如 arXiv）。
- **关于 `date`**：Publications 页面**只显示年份**（如 `2026`），月、日不会显示，只用来给同年的论文排序。所以日期不能留空（留空会显示 1900），但写成完整的 `2026-02-01` 即可，看上去就是 “2026”。
- **预印本（arXiv）**：暂时没正式发表时，`venue` 可写 `arXiv preprint`，`paperurl` 填 arXiv 链接；`category` 用 `manuscripts` 即可（本站已把它的显示标题改成 “Preprints & Journal Articles”）。

### 2. 添加报告 → `_talks/`

```markdown
---
title: "报告标题"
collection: talks
type: "Talk"               # Talk / Tutorial 等
permalink: /talks/2025-03-01-my-talk
venue: "举办方"
date: 2025-03-01
location: "城市, 国家"
---

报告描述，支持 Markdown。
```

### 3. 添加教学经历 → `_teaching/`

```markdown
---
title: "课程名称"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/2025-spring-course
venue: "学校, 院系"
date: 2025-01-01
location: "城市, 国家"
---

课程描述。
```

### 4. 作品集 → `_portfolio/`，博客 → `_posts/`

格式类似，参考目录下现有示例文件即可。

### 5. 编辑简历 → `_pages/cv.md`

`cv.md` 就是纯 Markdown，按 `教育经历 / 工作经历 / 技能` 等小节直接写即可。

---

## 五、改顶部导航栏 `_data/navigation.yml`

想隐藏某个菜单（比如你没有作品集），把对应几行删掉或注释即可：

```yaml
main:
  - title: "Publications"
    url: /publications/
  - title: "Talks"
    url: /talks/
  - title: "CV"
    url: /cv/
```

> 删掉菜单只是不在导航栏显示，页面本身仍然存在。

---

## 六、本地预览（强烈推荐）

在推送到 GitHub 之前先在本地看效果。三选一：

### 方式 A：直接用 Ruby/Jekyll
```bash
# macOS
brew install ruby node
gem install bundler

bundle install
bundle exec jekyll serve -l -H localhost
```
浏览器打开 http://localhost:4000 ，改 `.md` 文件会自动刷新（改 `_config.yml` 需重启）。

> 若遇到权限报错，可改为本地安装依赖：
> `bundle config set --local path 'vendor/bundle'` 再 `bundle install`。

### 方式 B：Docker（免装依赖）
```bash
chmod -R 777 .
docker compose up
```
然后访问 http://localhost:4000 。

### 方式 C：VS Code Dev Container
本仓库自带 `.devcontainer`。VS Code 中按 `F1` → **Dev Containers: Reopen in Container**，会自动在 http://localhost:4000 托管站点。

---

## 七、发布上线

本站托管在 **GitHub Pages**，每次把改动 push 到仓库就会自动重新构建发布：

```bash
git add .
git commit -m "更新主页内容"
git push
```

等一两分钟后访问 `https://你的GitHub用户名.github.io` 即可看到更新。构建状态可在 GitHub 仓库 **Settings → Pages** 查看。

> 不熟悉 git 也可以直接在 github.com 网页上点文件右上角的铅笔图标在线编辑、提交。

---

## 八、进阶功能

- **数学公式**：MathJax（直接写 `$...$`）
- **图表**：Mermaid
- **绘图**：Plotly
- **演讲地图**：运行 `talkmap.py` 或 `talkmap.ipynb`，根据 `_talks/` 内容生成你做过报告的地点地图（需在 `_config.yml` 中把 `talkmap_link` 设为 `true`）。
- **批量生成**：`markdown_generator/` 下的脚本可把 CSV/TSV 表格批量转成论文/报告的 `.md` 文件。

---

## 常见问题

- **改了 `_config.yml` 没生效？** → 本地需重启 Jekyll 服务。
- **图标不显示？** → 检查 `_config.yml` 中对应字段是否填了值（留空即隐藏）。
- **PDF 打不开？** → 确认文件已放进 `files/`，链接路径与用户名一致。
- **改坏了？** → 内容都在 Markdown 里很安全，可用 `git` 回滚，或保存好 `.md`/`.yml` 后重新 fork 模板。

更多官方文档：<https://academicpages.github.io/> ｜ Wiki：<https://github.com/academicpages/academicpages.github.io/wiki>
