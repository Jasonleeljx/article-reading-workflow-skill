---
name: article-reading-workflow
description: Format imported article notes in an Obsidian vault, especially long-form news and magazine articles, with standardized YAML/frontmatter, title/subtitle/body layout, inline collapsible natural Chinese translations, contextual HiNote highlight comments synced to optional Highlight Review/FSRS cards, and minimalist XMind-style article-structure mind maps. Use when the user asks to copy/save an article, translate an article, comment on highlighted article text, create review cards from highlights, or generate an article mind map.
---

# Article Reading Workflow

## Core rule

Work inside the Obsidian vault using relative paths. Preserve existing highlights, wikilinks, embeds, frontmatter fields, and plugin data unless the user explicitly asks to replace them.


## 中文说明

这是一个用于 Obsidian 文章精读的工作流 skill。它可以整理文章格式、生成自然中文译文、为 HiNote 高亮写入精读型 comment、同步到可选的 Highlight Review 复习卡片，并生成简约 XMind 风格的文章结构导图。

HiNote 不是必需依赖：文章整理、翻译和思维导图可以独立使用。只有在需要自动写入 HiNote comment 时，才需要 HiNote 或其他可读写本地批注数据的插件。

Highlight Review 复习插件也是可选组件，位于 `assets/obsidian-plugins/highlight-review/`。安装 skill 不会自动安装 Obsidian 插件；用户明确需要复习界面时，再把该文件夹复制到目标 vault 的 `.obsidian/plugins/highlight-review/`。

Use the bundled references as the source of truth:

- Article note format: `references/article-note-format.md`
- Translation style: `references/translation-style.md`
- HiNote / review-card sync: `references/hinote-fsrs.md`
- Mind map style: `references/mindmap-style.md`
- Mind map template: `assets/xmind-style-mindmap-template.svg`
- Inline translation CSS: `assets/inline-translation.css`
- Optional Obsidian review plugin: `assets/obsidian-plugins/highlight-review/`

## Task router

- **Copy/save an article**: read `references/article-note-format.md` and apply the note structure.
- **Translate an article**: read `references/translation-style.md`; use inline collapsible translations unless the user asks for a separate translation note.
- **Comment on highlights**: read `references/hinote-fsrs.md`; update HiNote comments and matching review cards when available.
- **Install or enable review cards**: read `references/hinote-fsrs.md`; copy `assets/obsidian-plugins/highlight-review/` into `.obsidian/plugins/highlight-review/` if the user wants the bundled review UI.
- **Generate a mind map**: read `references/mindmap-style.md`; use the SVG/XMind style from `assets/xmind-style-mindmap-template.svg`.

## Article note format quick guide

Use this order:

1. YAML frontmatter with source metadata.
2. Rubric/section line.
3. H1 title.
4. Italic subtitle/deck.
5. Dateline/location in bold if present.
6. Body paragraphs.
7. `---`, then `## Mind map`, then an Obsidian image embed if a mind map exists.

When including Chinese translations in the same note, append the trigger directly after the corresponding English unit:

```html
<label class="translation-toggle"><input class="translation-checkbox" type="checkbox"><span class="translation-label">中文译文</span><span class="translation-content">自然中文译文</span></label>
```

Ensure `.obsidian/snippets/inline-translation.css` exists and is enabled in `.obsidian/appearance.json`. If missing, copy `assets/inline-translation.css` into `.obsidian/snippets/inline-translation.css` and add `inline-translation` to `enabledCssSnippets`.

## Translation principles

Translate for meaning, not word order. Produce fluent, natural Chinese with accurate nuance, especially for headlines, puns, idioms, and magazine-style irony. Keep names, numbers, dates, and institutional terms precise. Prefer concise Chinese that reads like original Chinese business/news writing.

## Highlight comment principles

When the user asks to comment on highlighted text, produce **精读型 comment**, not terse dictionary glosses.

Each substantial highlight comment should normally include:

- the highlighted phrase in bold;
- the original sentence or a tight sentence fragment labelled `原句：`;
- `可以理解为：` followed by a natural Chinese interpretation, often in a blockquote;
- the local article logic: why this word/phrase matters in this paragraph’s argument;
- likely mistranslation or reading traps, especially when the literal meaning is misleading;
- concise usage/collocation notes when useful.

Always explain puns, cultural references, historical allusions, named slogans, title/rubric wordplay, idioms, and magazine-style jokes. For these, go beyond word meaning: identify the source/allusion, explain how the author twists it, and suggest natural Chinese renderings.

Avoid batch-style one-sentence comments unless the highlight is genuinely trivial. If generating many comments, maintain depth and consistency rather than compressing them.

Then, when the related data exists:

- Write the comment into the matching HiNote highlight JSON object.
- Sync the same comment and relevant sentence/translation fields to the corresponding card in `.obsidian/plugins/highlight-review/data.json` when a matching `highlightId` exists. If the vault still uses the legacy plugin path, check `.obsidian/plugins/hinote-free-srs/data.json` as a fallback.
- Back up JSON files before structural edits.

## Mind map principles

Create a clean SVG mind map, not a screenshot. Use a white background, thin colored strokes, rounded white nodes, and grey dashed logic arrows. Avoid filled color blocks. Show both:

- paragraph/section summaries; and
- the role of each paragraph plus the logic between paragraphs.

Embed it as `![[Attachments/<descriptive-name>.svg]]` under `## Mind map`.
