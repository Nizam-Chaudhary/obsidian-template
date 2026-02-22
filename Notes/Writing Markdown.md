---
categories:
  - "[[Docs]]"
created: 2026-02-22
tags:
  - markdown
related: "[[Obsidian]]"
---

Below is a comprehensive Markdown reference, tips, and tricks presented in Markdown format. It covers headings, lists, code, tables, links, images, blockquotes, emphasis, escaping, line breaks, nested structures, flavors (CommonMark vs GitHub Flavored Markdown), and practical best practices.

# Basic syntax

## Headings

Use 1–6 hash marks. Leave a space after the hashes.

# H1

## H2

### H3

#### H4

##### H5

###### H6

Tip: Pick a consistent heading style (ATX/hash style above is most common). Add a blank line before and after a heading for readability.

## Paragraphs and line breaks

- Paragraphs are separated by one or more blank lines.
- Soft break: press Enter once — many renderers collapse into a single space.
- Hard break: end a line with two or more spaces then Enter, or use a `<br>` in renderers that allow HTML (not recommended if you want pure Markdown portability).

Example (hard break with two spaces):
Line one␣␣  
Line two

## Emphasis

- Italic: `*italic*` or `_italic_`
- Bold: `**bold**` or `__bold__`
- Bold + italic: `***bold italic***` or `**_bold italic_**`
- Strikethrough (GFM): `~~strikethrough~~`

Tip: Use consistent marker types—`*` is common for emphasis, `**` for bold.

## Inline code and code blocks

- Inline code: use backticks: `` `code` ``
- Fenced code block (preferred): use triple backticks with language for syntax highlighting:

```python
# Example - specify language for highlighting
def greet(name):
    print(f"Hello, {name}")
```

- Indented code blocks (4 spaces) are supported but less flexible and can't specify language.

Tip: Always specify the language in fenced blocks for better readability and tooling support.

## Blockquotes

- Use `>` at the start of a line:

> This is a blockquote.
>
> You can nest blockquotes by adding additional `>` symbols.

Nested:

> > Nested quote

Tip: Blockquotes can contain other elements (lists, code blocks) if you prefix each content line with `>`.

## Lists

### Unordered lists

Use `-`, `*`, or `+` (pick one style and stay consistent).

- Item 1
- Item 2
  - Nested item
  - Another nested

### Ordered lists

Use numbers with periods. Markdown does not require correct numbering; you can use `1.` for all items and the renderer will renumber.

1. First
2. Second 3. Nested first 4. Nested second

Tip: Leave a blank line before a list to ensure proper parsing. For nested lists, indent nested items by 2 or 4 spaces (4 is safest).

### Task lists (GitHub Flavored Markdown)

- [ ] todo item
- [x] done item

Syntax:

```markdown
- [ ] Incomplete
- [x] Complete
```

## Tables (GFM)

Use pipes and hyphens. Align columns with colons.

| Left align | Center | Right align |
| :--------- | :----: | ----------: |
| left       | center |       right |

Syntax:

```markdown
| Left | Center | Right |
| :--- | :----: | ----: |
| a    |   b    |     c |
```

Tip: Tables are a GFM feature; other Markdown flavors may not support them.

## Links and images

- Link: `[link text](https://example.com "optional title")`
- Reference-style link:

```markdown
[example][1]

[1]: https://example.com "Optional title"
```

- Image: `![alt text](image-url.jpg "optional title")`

Tip: Prefer descriptive link text for accessibility, e.g. `[Project README](/README.md)` rather than `click here`.

## Horizontal rules

Use three or more `-`, `*`, or `_` on a line by themselves:

---

or

---

Tip: Surround with blank lines for clarity.

# Advanced and practical topics

## Escaping special characters

Escape Markdown characters with a backslash: `\*not italic\*` renders _not italic_ literally. Characters commonly escaped: `\` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `!` `>` `|` `.` `!`

Example:

```
Use \* to show an asterisk.
```

## HTML in Markdown

Many Markdown implementations allow inline HTML (e.g., for complex layouts). Use sparingly for portability. Some platforms sanitize HTML.

Example:

```html
<span style="color: red">This is red text.</span>
```

## YAML front matter

Used in static site generators (Jekyll, Hugo) and some documentation systems. Starts and ends with `---`:

```yaml
---
title: "My Page"
date: 2025-12-09
tags: [markdown, tips]
---
```

Tip: Front matter is not part of core Markdown; it’s a site generator feature.

## Footnotes (GFM/Markdown extensions)

Some implementations support footnotes:

This is a sentence with a footnote.[^1]

[^1]: This is the footnote.

## Definition lists (not in core Markdown)

Some flavors/extensions support definition lists:

Term
: Definition

## Math (LaTeX) support

Not part of core Markdown. Many sites (e.g., Jupyter, some static sites) support inline math `$...$` and display math `$$...$$`. Check your renderer.

Note: If you include LaTeX in Markdown, follow the renderer rules; some use KaTeX or MathJax.

## Syntax highlighting

- Always specify language in code fences (e.g., `js, `python).
- For unknown language, use plain `text` as language identifier.

## Embedding raw content

- You can embed raw HTML or use platform-specific shortcodes for media (e.g., YouTube embeds in site generators).

# Nesting rules and examples

Nested list with code block and blockquote:

````markdown
1. Item one
   - Subitem

     > Blockquote inside subitem

     ```js
     // code block inside nested list; indent fence to align
     console.log("hello");
     ```
````

Tip: Add a blank line before fenced blocks inside lists to ensure they are correctly parsed.

# Differences between CommonMark and GitHub Flavored Markdown (GFM)

- GFM adds tables, task lists, strikethrough, and autolinks.
- CommonMark is a consistent spec; many platforms implement CommonMark + extensions.
- Check your target renderer (GitHub, GitLab, Bitbucket, Jekyll, Hugo, MkDocs) for supported features.

# Accessibility and semantics

- Use descriptive alt text for images: `![Diagram of system architecture](arch.png)`
- Use headings in order (don’t skip H2 to H4) for screen readers.
- Use lists for actual lists, tables for tabular data.

# Best practices and tips

- Be consistent: choose one style for bullets (`-` or `*`) and stick to it.
- Always put a blank line between blocks (headings, lists, paragraphs, code blocks) for reliable rendering.
- Use fenced code blocks with language tags for syntax highlighting and tooling.
- Keep lines under ~80 characters for readability in raw form and diffs.
- Use reference-style links for long or repeated URLs to keep text readable.
- Prefer relative links for documentation within a repo/site.
- When collaborating, lint Markdown with tools (markdownlint, remark) to enforce style.
- For long documents, include a table of contents (some renderers auto-generate TOC).
- Use task lists for issue tracking and status in GitHub READMEs.
- Avoid relying on HTML unless necessary (hurts portability and readability).
- Use headings to structure content: think of the document as nested sections.

# Common pitfalls

- Forgetting blank lines before lists or code fences (causes incorrect parsing).
- Inconsistent indentation in nested lists leading to broken nesting.
- Using numbered lists with nonstandard markers (e.g., `1)` vs `1.`) — prefer `1.`.
- Inline HTML may be stripped or sanitized on some platforms.
- Relying on renderer-specific features without checking support.

# Tools and linters

- markdownlint (Node) — enforces style rules.
- remark / unified — parse and transform Markdown.
- Prettier — formats Markdown (respect soft/wrap settings).
- VS Code extensions (Markdown All in One, Markdown Lint) for editing help.

# Quick reference (cheat-sheet)

- Heading: `## Heading`
- Bold: `**bold**`
- Italic: `*italic*`
- Strikethrough (GFM): `~~strike~~`
- Inline code: `` `code` ``
- Code block: ` `js ... ```
- Link: `[text](url "title")`
- Image: `![alt](url "title")`
- Unordered list: `- item`
- Ordered list: `1. item`
- Task list (GFM): `- [ ] task`
- Blockquote: `> quote`
- Table: `| col | col |` then `|:--|--:|`

# Example full document

````markdown
# Project Title

A short description.

## Features

- [x] Feature one
- [ ] Feature two

## Usage

```bash
# run the project
npm install
npm start
```
````

## API

See [API docs](./API.md).

## License

MIT

```

Final tip: test your Markdown in the target environment (GitHub, GitLab, docs site) since support for extensions and exact rendering can vary. If you want, I can generate a tailored cheatsheet for a specific platform (GitHub, GitLab, Jekyll, Hugo, MkDocs, etc.). Which one do you use?
```
