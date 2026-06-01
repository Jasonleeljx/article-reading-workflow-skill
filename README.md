# Article Reading Workflow Skill

[中文说明](README.zh-CN.md)

A Codex skill for working with long-form article notes in Obsidian.

It helps an AI assistant:

- format imported article notes with standardized YAML/frontmatter and clean body layout;
- add inline collapsible natural Chinese translations;
- write contextual HiNote highlight comments for intensive reading;
- sync comments to optional Highlight Review / FSRS-style review cards;
- optionally install the bundled Highlight Review Obsidian plugin for local review UI;
- generate minimalist XMind-style SVG article-structure mind maps.

## Install

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R article-reading-workflow ~/.codex/skills/
```

Then start a new Codex session and ask for `$article-reading-workflow`, or ask it to format/translate/comment on an article note.

## Obsidian assumptions

This skill is designed for an Obsidian vault and uses relative vault paths. Optional integrations:

- HiNote highlight JSON under `.hinote/highlights/`
- Highlight Review card data under `.obsidian/plugins/highlight-review/data.json`
- legacy fallback for older local setups: `.obsidian/plugins/hinote-free-srs/data.json`

## License

MIT

## Optional Highlight Review plugin

This repository includes a bundled Obsidian plugin at:

```text
article-reading-workflow/assets/obsidian-plugins/highlight-review/
```

Installing the skill alone does **not** automatically install the Obsidian plugin. To enable the review UI in a vault, copy that folder to:

```text
<vault>/.obsidian/plugins/highlight-review/
```

Then add `highlight-review` to `.obsidian/community-plugins.json` or enable it from Obsidian's Community Plugins settings.

The bundled plugin does not include any `data.json`, so it will not ship someone else's cards or review history.
