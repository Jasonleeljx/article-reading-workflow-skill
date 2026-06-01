# Natural Chinese translation style

## Goal

Translate into idiomatic, fluent, natural Chinese. Do not produce translationese. Preserve the author’s meaning, tone, irony, and argumentative structure.

## Rules

- Translate ideas and rhetorical function, not English word order.
- Rewrite awkward literal structures into natural Chinese business/news prose.
- Keep facts exact: names, numbers, dates, institutions, places, causal claims.
- For puns/rubrics/headlines, prefer a Chinese line that carries the article’s function and tone. Explain alternatives only if the user asks.
- Avoid over-explaining inside the translation; save explanations for HiNote comments.
- Use full-width Chinese punctuation in Chinese text.
- Use Arabic numerals naturally in Chinese: `12.8 万人`, `9000 万套`, `2025 年初`.
- Maintain paragraph alignment: one English paragraph maps to one Chinese paragraph when possible.

## Inline format

Use:

```html
<label class="translation-toggle"><input class="translation-checkbox" type="checkbox"><span class="translation-label">中文译文</span><span class="translation-content">译文</span></label>
```

Do not include markdown headings inside `translation-content`; use plain Chinese text for the hidden content.
