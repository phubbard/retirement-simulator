# Retirement Financial Planner — Developer Notes

## Version Management

**Always bump `APP_VERSION` when making changes.**

The version constant is at the top of `index.html` inside the `<script>` tag:

```js
const APP_VERSION = '1.1.1';
```

Follow semantic versioning:
- **Patch** (1.1.X): bug fixes, data corrections, copy changes
- **Minor** (1.X.0): new features, new tabs, new data sources
- **Major** (X.0.0): breaking changes to saved config format or localStorage schema

The version displays on the About tab and in the print PDF header.

## Architecture

Single-file HTML/JS app (`index.html`). No build step. Chart.js loaded from CDN.

Key sections in order:
1. CSS (including `@media print` block)
2. HTML tabs and panels
3. `<script>`: historical data → tax brackets → relocation data → state object → tab management → UI renderers → helpers → tax/SS/Prop13 functions → simulation engine → relocation UI → scenario table → CSV export → config export/import → localStorage persistence → initUI → print handlers

## Common Pitfalls

- **Import vs localStorage race**: `importConfig()` must persist to localStorage via `_doSave()` before any call to `loadFromStorage()` or `initUI()`, otherwise imported state gets overwritten.
- **Git lock files**: The mounted filesystem sometimes leaves stale `.git/HEAD.lock` files. Delete them manually if git commands hang.
- **Print CSS**: Chart.js charts need color swapping via `beforeprint`/`afterprint` event handlers — CSS alone can't restyle canvas elements.
