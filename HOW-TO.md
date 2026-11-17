# How to use ICT Institute Reports

Write a report in Markdown in Obsidian, see the finished report next to your text, and export a PDF with one click. Everything works offline: no account, no server, no internet connection.

## What you need

- [Obsidian](https://obsidian.md) 1.8.7 or later, on Windows, macOS or Linux (the plugin does not run on phones or tablets).
- The plugin: the file `icti-reports-<version>.zip` from the **Releases** page of this repository.

## 1. Install the plugin

1. Download `icti-reports-<version>.zip` from the latest release and unzip it. You get a folder called `icti-reports`.
2. Open your vault folder in your file manager. Go into the hidden folder `.obsidian` (on macOS press `Cmd+Shift+.` to show hidden folders; on Windows tick *View → Hidden items*). Create a folder `plugins` there if it does not exist.
3. Close Obsidian and copy the `icti-reports` folder into `.obsidian/plugins/`. The result is `<your vault>/.obsidian/plugins/icti-reports/main.js` (and more files).
4. Start Obsidian. Go to *Settings → Community plugins*. If it says **Restricted mode**, click **Turn on community plugins**. Switch on **ICT Institute Reports**.
5. In *Settings → ICT Institute Reports*, click **Install starter files**. This adds:
   - `ICT Rapporten/Sjablonen/`: two templates, *Simple report* (English) and *Eenvoudig rapport* (Dutch);
   - `ICT Rapporten/Opmaak/`: the layout (`report.typ`) and its pictures;
   - a **HOW TO** note (in Dutch) with the full manual.

   Existing files are never overwritten.
6. Optional: the plugin's own buttons and messages are in Dutch by default. Switch them to English in *Settings → ICT Institute Reports → Taal van de plugin*.

### Optional: the theme

The release also has `ICT-Institute-theme.zip`, an Obsidian theme in the same style. Unzip it and copy the folder `ICT Institute` into `<your vault>/.obsidian/themes/` and pick it in *Settings → Appearance → Themes*. The plugin works with any theme.

## 2. Make your first report

1. Click **New report** in the panel at the top left (or press `Ctrl+P` / `Cmd+P` and type *report*).
2. Pick a template, then **Internal project** or **Client project**, then a folder (type a name to create one), then the document name.
3. The note opens with the report preview next to it. Red text is still to be filled in.
4. Edit the cover block at the top: the title, a subtitle and the date.
5. Write the report under the headings. The preview updates while you type.
6. Click **PDF exporteren / Export PDF** above the preview. The PDF is saved next to the note.

The buttons above the preview turn the cover page, the page header and the table of contents on and off, and change the cover picture.

## 3. Learn the format

A report is ordinary Markdown with three special blocks:

```markdown
> [!cover]
> # Title of the report
> Subtitle
> 17 November 2026

> [!header]
> Project: …
> Document: Report

> [!contents]

\pagebreak

# Introduction
```

[REPORT-FORMAT.md](REPORT-FORMAT.md) lists everything: placeholders (`==…==`), tables, images, callouts and page breaks.

## 4. Use your own look

- **Cover picture**: click **Omslagafbeelding / Cover image** above the preview, or replace `ICT Rapporten/Opmaak/assets/cover-default.png` with your own picture to change the standard one. The repository ships a neutral placeholder.
- **Templates**: copy a template in `ICT Rapporten/Sjablonen/` to a new name and change it, or use **Import Word report** to turn an existing `.docx` report into a template.
- **Colours, fonts and page design**: these are in `ICT Rapporten/Opmaak/report.typ` (a [Typst](https://typst.app) file). Change it only if you know Typst; *Settings → ICT Institute Reports → Update layout* puts the original back (your old copy is kept as `report.typ.bak`).

## Updating

Replace the `icti-reports` folder in `.obsidian/plugins/` with the new one (keep `data.json`, which holds your settings) and restart Obsidian. Then click **Update layout** and **Install starter files** in the plugin settings.

## Problems

- *The plugin does not appear*: check that the folder is exactly `.obsidian/plugins/icti-reports/` with `manifest.json` directly inside it.
- *The preview shows warnings*: they are listed above the pages; click one to jump to the line.
- Errors are written to `.obsidian/plugins/icti-reports/errors.log`. Please attach it when you open an issue.
