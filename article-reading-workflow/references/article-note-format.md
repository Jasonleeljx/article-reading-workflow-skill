# Article note format

## Frontmatter

Use YAML like the exemplar:

```yaml
---
Source: https://...
Section: Finance & economics
Rubric: Rubric text
Title: English article title
Subtitle: English article subtitle or deck
created: "YYYY-MM-DD"
Topics:
  - AI
  - China
  - Commercial real estate
---
```

Guidelines:

- Preserve existing fields and field names unless there is a clear reason to add missing metadata.
- `Source` is the canonical URL.
- `Section`, `Rubric`, `Title`, `Subtitle`, `created`, `Topics` follow the article source when available.
- Use quoted ISO date for `created`.

## Body layout

Use this order:

```md
**Finance & economics | Rubric text**

# English title

*English subtitle*

**DATELINE**

Paragraph 1.

Paragraph 2.

### Section heading if present

Paragraph...

---

## Mind map

![[Attachments/article-mindmap.svg]]
```

Keep original highlights (`<mark style="background: ...">...</mark>`) intact.

## Inline translation toggle

Append the translation trigger to the end of the English unit it translates. Do not put the trigger on a separate line unless impossible.

```html
English paragraph. <label class="translation-toggle"><input class="translation-checkbox" type="checkbox"><span class="translation-label">中文译文</span><span class="translation-content">中文译文。</span></label>
```

For headings, subtitles, rubrics, datelines, and paragraphs, each can have its own trigger.

The CSS snippet should make the trigger small, faint, and inline; the translation appears on the next line only after clicking.
