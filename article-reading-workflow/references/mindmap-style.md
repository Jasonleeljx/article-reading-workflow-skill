# Minimalist XMind-style article mind map

## Visual style

Create an SVG with:

- white background;
- central rounded white node with dark stroke;
- main nodes as rounded white rectangles with colored strokes;
- subnodes as smaller rounded white rectangles with lighter strokes;
- curved colored branches;
- grey dashed arrows between main nodes to show logic;
- no filled color blocks;
- system UI fonts with Chinese fallbacks;
- clean spacing and enough canvas width for labels.

Use `assets/xmind-style-mindmap-template.svg` as the style template.

## Content requirements

For each major paragraph/section, include:

- a short role label: e.g. `反讽切口`, `铺垫背景`, `收窄焦点`, `转折`, `扩散`, `反讽收束`;
- a one-line summary of what the paragraph says;
- 1-2 subnodes with key evidence or examples;
- a dashed logic annotation to the next paragraph explaining the transition.

The mind map should let the reader see the article’s whole argument at a glance: not only “what each paragraph says”, but “why this paragraph is here” and “how it connects to the next one”.

## Embed

Save under `Attachments/` with a descriptive filename and embed:

```md
---

## Mind map

![[Attachments/<article-slug>-mindmap.svg]]
```
