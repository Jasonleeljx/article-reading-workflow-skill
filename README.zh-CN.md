# Article Reading Workflow Skill（文章阅读工作流）

这是一个面向 Obsidian 文章精读的 Codex skill，适合处理长文章、外刊、新闻评论和杂志类文章。

它可以帮助 AI 助手完成：

- 整理导入后的文章笔记，统一 YAML/frontmatter、标题、副标题和正文结构；
- 为英文文章加入自然、地道的中文译文；
- 使用行内折叠译文，让中文译文不打断英文阅读；
- 为 HiNote 高亮写入精读型 comment；
- 可选同步到 Highlight Review / FSRS-like 复习卡片；
- 生成简约 XMind 风格的 SVG 文章结构导图。

## 安装 skill

把 `article-reading-workflow` 文件夹复制到你的 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R article-reading-workflow ~/.codex/skills/
```

然后重新开始 Codex 会话，可以直接说：

```text
$article-reading-workflow 帮我整理并翻译这篇文章
```

或者提出类似需求，例如：

- “把这篇文章整理成统一格式”
- “给这篇文章加中文译文”
- “解释我选中的 highlight 并写入 comment”
- “给这篇文章做一个 XMind 风格思维导图”

## 是否必须安装 HiNote？

不必须。

不需要 HiNote 的功能：

- 文章格式整理
- 中文译文
- 行内折叠译文
- SVG 思维导图

需要或建议使用 HiNote 的功能：

- 自动把解释写回 HiNote highlight comment
- 根据 HiNote 高亮定位对应批注数据

如果你使用其他批注插件，也可以适配，但前提是该插件的批注数据能在本地文件中读写，例如 JSON、Markdown 或 sidecar 文件。

## 可选：Highlight Review 复习插件

这个仓库内置了一个可选 Obsidian 插件：

```text
article-reading-workflow/assets/obsidian-plugins/highlight-review/
```

安装 skill 本身不会自动安装 Obsidian 插件。若要启用复习界面，需要把这个文件夹复制到你的 vault：

```text
<vault>/.obsidian/plugins/highlight-review/
```

然后在 Obsidian 设置中启用 **Highlight Review**，或把 `highlight-review` 加入：

```text
<vault>/.obsidian/community-plugins.json
```

这个插件会在本地生成并保存：

```text
.obsidian/plugins/highlight-review/data.json
```

该文件用于保存卡片、复习进度和排期。仓库没有附带任何 `data.json`，因此不会包含作者的个人卡片或学习记录。

## 数据与隐私

这个仓库只包含基础 skill 文件、样式、模板和可选插件代码，不包含：

- 个人 Obsidian vault 内容；
- 个人文章笔记；
- HiNote 高亮数据；
- Highlight Review 卡片数据；
- 复习历史；
- 本地绝对路径；
- API token 或密码。

## 开源许可

本项目使用 MIT License。你可以自由使用、复制、修改、fork 和提交 Pull Request。
