# FrameLab Visual Data Studio

中英双语的浏览器本地数据分析工具。Bilingual browser-local visual data analysis.

## Run locally

Requires Python 3 for the optional static server, or any static web server.

```sh
python -m http.server 8080 --directory dist
```

Open http://localhost:8080. No build, package install, API key or backend required.

## Features

CSV / TSV / JSON record-array import, drag-and-drop, paste, CORS-enabled URL; customizable local default; cell editing, search and sorting; missing-value cleanup, deduplication, type conversion, arithmetic columns, text transforms, date buckets, rolling means, random sampling; group aggregation, pivot and left / inner joins; bar, line, scatter, histogram, donut and Pearson correlation matrix; undo / redo; CSV, JSON, SVG, Python and replayable workflow export.

## Files

- `dist/index.html`: app shell
- `dist/style.css`: responsive visual design
- `dist/engine.js`: parser and tabular primitives
- `dist/app.js`: bilingual UI, operations, charts and workflow
- `.openai/hosting.json`: deployment configuration

## Scope and limits

Implements common pandas-inspired workflows in JavaScript, not the whole pandas API or a Python runtime. CSV/TSV/JSON supported; native XLSX, Parquet, SQL and MultiIndex are not supported. Import cap: 50,000 rows. Charts display up to 24 categories; scatter up to 3,000 points; correlation up to 8 numeric columns. Full imported rows remain available for transformations and export. Missing values are null / undefined / empty string. Dates use browser parsing and UTC buckets. Numeric statistics use sample standard deviation; IQR outliers use 1.5 × IQR. Undo snapshots consume memory. Saved defaults use browser localStorage and can exceed its quota. External URLs require CORS. The optional Google Font is cosmetic; the app works with fallback fonts. Python snippets are a starting point; null grouping, pivot layout, inferred types, date parsing and random samples can differ from pandas. Review snippets before production use.

## Privacy

Imported data is processed locally in your browser, not uploaded to an analysis server. Only explicit URL imports issue data requests. Custom defaults persist on the current browser/device until restored. Hosting may require owner sign-in.
