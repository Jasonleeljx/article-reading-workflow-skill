# HiNote comments and review-card sync

## Files

HiNote highlight files usually live under `.hinote/highlights/`. File names are normalized from note paths; confirm via `.hinote/metadata/file-mapping.json` when unsure.

Review cards may live in `.obsidian/plugins/highlight-review/data.json` under `cards`. For older vaults, also check the legacy path `.obsidian/plugins/hinote-free-srs/data.json`.


## Optional bundled review plugin

This skill can bundle a small Obsidian plugin named **Highlight Review** at `assets/obsidian-plugins/highlight-review/`. It is not installed automatically just because the skill exists.

When the user asks to install or enable the review system:

1. Copy the bundled plugin folder to `.obsidian/plugins/highlight-review/` in the target vault.
2. Do **not** overwrite an existing `data.json` unless the user explicitly wants to reset review data. The bundled plugin folder intentionally contains only `manifest.json`, `main.js`, and `styles.css`.
3. Add `highlight-review` to `.obsidian/community-plugins.json` if it is not already listed.
4. Tell the user to reload Obsidian or toggle the plugin off/on.

The plugin provides the local review UI and stores scheduling/card data in `.obsidian/plugins/highlight-review/data.json`. Without this plugin, the skill can still format articles, translate, make mind maps, and write HiNote comments, but it will not add a review interface.

## Workflow

1. Read the article note and the corresponding HiNote JSON.
2. Locate the highlighted item by selected text, highlight id, or nearest context.
3. Back up JSON before edits:
   - `.hinote/highlights/<file>.json.bak-<slug>-<timestamp>`
   - `.obsidian/plugins/highlight-review/data.json.bak-<slug>-<timestamp>` when touching review cards
   - if using the legacy plugin path, back up `.obsidian/plugins/hinote-free-srs/data.json` similarly
4. Add or update the highlight comment in `highlights[highlightId].comments`.
5. Locate matching review card by `highlightId`; update its `comment`, `highlight`, `sentence`, `translationSentence`, and `updated` fields as appropriate.
6. Preserve scheduling fields (`due`, `stability`, `difficulty`, `reps`, `lapses`, `lastReview`, `history`) unless the user explicitly asks to reschedule.
7. Validate JSON parses after editing.

## Comment style

A good comment is a **contextual reading note**, not a dictionary entry. It should contain enough context that the card remains useful for future reading review.

Preferred structure:

```md
这里的 **phrase** 不是……，而是……。

原句：`... phrase ...`

可以理解为：

> 自然中文解释 / 译法

放在这篇文章的语境里，它的作用是……

常见搭配 / 误读提醒：

- `phrase pattern` = 中文含义
```

Use this structure flexibly, but preserve the substance: original context, natural Chinese interpretation, article-specific function, and traps.

### Puns, allusions, and magazine-style jokes

For title/rubric wordplay, cultural references, historical allusions, slogans, idioms, and jokes, include extra explanation. A good comment should answer:

1. What is the original reference or idiom?
2. What did the author change or twist?
3. Why does the joke/allusion fit this article’s argument?
4. How can it be translated naturally into Chinese?

Do not reduce such highlights to one-line definitions.

### Quality check before saving

Before writing HiNote/review-card JSON, sample the generated comments. If most comments lack `原句`, `可以理解为`, or article-specific logic, rewrite them before saving.
