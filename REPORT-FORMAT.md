# Report format

This file describes the Markdown that the ICT Institute Reports plugin turns into a PDF. Everything here is plain Markdown: a report stays readable in any text editor, and without the plugin the special blocks show as quotes.

## Skeleton of a report

```markdown
---
language: en
---

> [!cover]
> # Information security assessment
> Report for ABC B.V.
> 17 November 2026
> ![Cover](../Images/abc-cover.png)
> Prepared for ABC B.V.
> Jan Jansen, CISO

> [!header]
> Project: Information security assessment – ABC B.V.
> Document: Report

> [!contents]

\pagebreak

# 1. Introduction

Text…

## 1.1 Scope

Text…

# 2. Findings

…
```

## The parts

| Part | How to write it | Notes |
|---|---|---|
| **Properties** | `language: nl` or `language: en` in the frontmatter | The only property that is read. `nl` gives Dutch labels (such as *Inhoud* for the contents title); default is English. A report needs no frontmatter at all. |
| **Cover page** | A `> [!cover]` block at the very top | Line 1 `# Title`. The next line is the subtitle, the one after it the small line (normally the date); both sit between the navy bars. An optional image line `> ![Cover](path)` is the cover picture. Every further line is printed under the bars (for example "Prepared for …", a name). The title size adapts to fit (40 pt down to 12 pt). Leave the block out for a report without a cover. |
| **Page header** | A `> [!header]` block with two lines | The two small lines at the top left of every page after the cover. A third line is ignored. Without it the header shows the title. |
| **Table of contents** | `> [!contents]` (English) or `> [!inhoud]` (Dutch) on its own | Generated in the PDF from all `#` and `##` headings, with page numbers. `> [!inhoud] Inhoudsopgave` sets a custom title. Use at most one. Normally followed by `\pagebreak`. |
| **Page break** | `\pagebreak` on its own line | Starts a new page. |
| **Headings** | `#` chapter, `##` section, `###` sub-section | Number them yourself if you want numbers (`# 2. Findings`). Only `#` and `##` appear in the contents. |
| **Placeholders** | `==text to fill in==` | Printed red. Export warns while any are left. Use them for anything the author still has to supply. |
| **Red text on purpose** | `<span style="color:red">text</span>` | Red without the placeholder warning. No other HTML is read. |
| **Callouts** | `> [!note] Title` followed by `> text` lines | Any callout type prints as a quote with a bold title. |
| **Tables** | Normal Markdown tables | Printed at 10 pt with a coloured header row. The number of dashes per column in the separator row sets relative widths (`\|------\|--------------\|`). `<br>` makes a line break in a cell. |
| **Images** | `![[image.png]]`, `![[image.png\|300]]` (300 pt wide), `![](folder/image.png)`, `![](../Images/x.png)` | Paths are relative to the note and must stay inside the vault. |
| **Lists, bold, italic, links, code, footnotes** | Standard Markdown | Body text is 11 pt. |

## Rules that keep the PDF correct

1. Put the cover block first, then the header block, then the contents block and `\pagebreak`, then the text.
2. Each block line starts with `> `. Leave an empty line between blocks.
3. Never write Typst or LaTeX: all text is printed literally. `\pagebreak` is the only command.
4. No HTML except `<br>` in table cells and the red `<span>` above.
5. Only one cover, one header and one contents block per report; extra ones are ignored with a warning.
6. Use `==…==` for every fact you do not know (client name, dates, numbers) instead of inventing it.

## Templates

Every note in the templates folder of the vault is a template for *New report*. Templates may use these fields, filled in when a report is created: `{{title}}` (document name), `{{long_date}}` (today, written out in the template's language), `{{date}}` (YYYY-MM-DD), `{{year}}`, `{{folder}}` (client or project folder) and `{{type}}` (template name). In frontmatter, put them inside double quotes.
