# Haven VS Code Theme — Workbench Color Key → Brand Token Map

Every committed hex value in `themes/*.json` resolved to a named brand token.
This document is the single source of truth for the mapping. Modeled on
[`OBSIDIAN-TOKEN-MAP.md`](../haven-obsidian-theme/OBSIDIAN-TOKEN-MAP.md).

**Source of truth:** `cena-health-brand/_tokens/generated/palette.css` (Cena Color
System v2, OKLCH + hex). The haven-obsidian-theme vendors these as
`--haven-{family}-{step}`; this map uses the same vendored names so the two
themes speak one vocabulary.

**Sand inversion note.** Brand `--color-sand-50` (the lightest sand, #F8F4EC) maps
to vendored `--haven-warm-950` (the lightest warm). The scales are inverted: brand
"50 = lightest" vs. vendored "950 = lightest". This map uses the vendored
naming throughout for parity with the obsidian theme.

**Drift note (2026-05-31).** Cena Color System v2 brand canon was updated
2026-05-30 (brand `752c488`): sand-100/200/300/400 were lifted (warmer) and
functional -50 surface tints were lifted (warmed). The obsidian theme dd177d3
patched only `--haven-warm-950` from this set. **This vscode theme has the same
gap** — warm-800/700/600 are still on the pre-lift values. Flagged 🟡 in rows
below. Resolution belongs in Step 2 of the port plan.

**Status key:**
- ✅ mapped — value resolves to a current brand token
- 🟡 drift — value is *close to* a brand token but doesn't match current canon (`v1→v2` lift)
- 🔴 missing — key is defined in one variant but absent in another (coverage gap)
- ⚫ vscode-internal — alpha/blended computed value (e.g., `#1B685E80` = teal-400 @ 50%); the base resolves
- 🔵 functional — error/warning/info/success token (not a surface family)

---

## 1. Editor

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `editor.background` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-100` (#25211D) | ✅ |
| `editor.foreground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `editor.lineHighlightBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-300` (#124D45) @ 9% | `--haven-warm-900` (#F3F1EE) | `--haven-warm-200` (#3F3933) @ 25% | ⚫ |
| `editor.lineHighlightBorder` | `--haven-warm-900` (#F3F1EE) @ 0% | `--haven-teal-300` (#124D45) @ 0% | `--haven-warm-900` (#F3F1EE) @ 0% | `--haven-warm-200` (#3F3933) @ 0% | ⚫ |
| `editor.selectionBackground` | `--haven-teal-900` (#D0E7E2) | `--haven-sage-700` (#81B983) @ 38% | `--haven-warm-800` (#E7E4DF) | `--haven-warm-300` (#5B544C) @ 38% | ⚫ |
| `editor.selectionHighlightBackground` | `--haven-teal-900` (#D0E7E2) @ 38% | `--haven-sage-700` (#81B983) @ 13% | `--haven-warm-800` (#E7E4DF) @ 50% | `--haven-warm-300` (#5B544C) @ 25% | ⚫ |
| `selection.background` | — | `--haven-sage-700` (#81B983) @ 38% | — | `--haven-sage-700` (#81B983) @ 38% | 🔴 light-side |
| `editor.wordHighlightBackground` | `--haven-teal-900` (#D0E7E2) @ 50% | `--haven-teal-600` (#52A395) @ 19% | `--haven-warm-800` (#E7E4DF) @ 50% | `--haven-warm-300` (#5B544C) @ 31% | ⚫ |
| `editor.wordHighlightStrongBackground` | `--haven-teal-900` (#D0E7E2) @ 63% | `--haven-teal-600` (#52A395) @ 27% | `--haven-warm-800` (#E7E4DF) @ 63% | `--haven-warm-300` (#5B544C) @ 44% | ⚫ |
| `editor.findMatchBackground` | `--haven-teal-900` (#D0E7E2) | `--haven-warning-border` (#CEA861) @ 31% | `--haven-teal-900` (#D0E7E2) | `--haven-teal-400` (#1B685E) @ 44% | ⚫ |
| `editor.findMatchHighlightBackground` | `--haven-teal-950` (#E9F5F2) @ 50% | `--haven-warning-border` (#CEA861) @ 15% | `--haven-teal-950` (#E9F5F2) @ 38% | `--haven-teal-400` (#1B685E) @ 25% | ⚫ |
| `editor.rangeHighlightBackground` | `--haven-warm-900` (#F3F1EE) @ 50% | `--haven-teal-200` (#0D322D) @ 15% | `--haven-warm-900` (#F3F1EE) @ 50% | `--haven-warm-200` (#3F3933) @ 19% | ⚫ |
| `editor.hoverHighlightBackground` | `--haven-teal-950` (#E9F5F2) @ 25% | `--haven-teal-600` (#52A395) @ 9% | `--haven-warm-900` (#F3F1EE) @ 50% | `--haven-warm-200` (#3F3933) @ 25% | ⚫ |
| `editor.foldBackground` | `--haven-warm-900` (#F3F1EE) @ 50% | `--haven-teal-200` (#0D322D) @ 13% | `--haven-warm-900` (#F3F1EE) @ 50% | `--haven-warm-200` (#3F3933) @ 19% | ⚫ |
| `editorCursor.foreground` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | ✅ |
| `editorWhitespace.foreground` | `--haven-warm-700` (#D1CDC6) @ 25% | `--haven-teal-200` (#0D322D) @ 31% | `--haven-warm-700` (#D1CDC6) @ 25% | `--haven-warm-200` (#3F3933) @ 25% | ⚫ |
| `editorIndentGuide.background` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 25% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-200` (#3F3933) @ 31% | 🟡 warm-700 |
| `editorIndentGuide.activeBackground` | `--haven-warm-500` (#857E75) ⚠ | `--haven-teal-400` (#1B685E) @ 38% | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-300` (#5B544C) @ 50% | 🟡 see note |
| `editorLineNumber.foreground` | `--haven-warm-500` (#857E75) ⚠ | `--haven-teal-300` (#124D45) | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-300` (#5B544C) | 🟡 see note |
| `editorLineNumber.activeForeground` | `--haven-teal-200` (#0D322D) | `--haven-teal-600` (#52A395) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `editorRuler.foreground` | `--haven-warm-700` (#D1CDC6) @ 25% | `--haven-teal-200` (#0D322D) @ 25% | `--haven-warm-700` (#D1CDC6) @ 25% | `--haven-warm-200` (#3F3933) @ 31% | ⚫ |
| `editorBracketMatch.background` | `--haven-teal-950` (#E9F5F2) @ 50% | `--haven-teal-600` (#52A395) @ 19% | `--haven-warm-800` (#E7E4DF) @ 50% | `--haven-warm-300` (#5B544C) @ 25% | ⚫ |
| `editorBracketMatch.border` | `--haven-teal-500` (#3A8478) | `--haven-teal-600` (#52A395) @ 50% | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-500` (#857E75) ⚠ | 🟡 see note |
| `editorOverviewRuler.border` | `--haven-warm-700` (#D1CDC6) @ 0% | `--haven-teal-200` (#0D322D) @ 0% | `--haven-warm-700` (#D1CDC6) @ 0% | `--haven-warm-200` (#3F3933) @ 0% | ⚫ |
| `editorGutter.addedBackground` | `--haven-success-base` (#3A8E64) | `--haven-success-base` (#3A8E64) | `--haven-success-base` (#3A8E64) | `--haven-success-base` (#3A8E64) | 🔵 |
| `editorGutter.modifiedBackground` | `--haven-teal-400` (#1B685E) | `--haven-warning-border` (#CEA861) | `--haven-teal-400` (#1B685E) | `--haven-warning-border` (#CEA861) | ✅ |
| `editorGutter.deletedBackground` | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | 🔵 |
| `editorError.foreground` | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | 🔵 |
| `editorWarning.foreground` | `--haven-warning-text` (#754B00) | `--haven-warning-border` (#CEA861) | `--haven-warning-text` (#754B00) | `--haven-warning-border` (#CEA861) | 🔵 |
| `editorInfo.foreground` | `--haven-info-base` (#287AA3) | `--haven-info-border` (#538EB0) | `--haven-info-base` (#287AA3) | `--haven-info-border` (#538EB0) | 🔵 |

**Note on `#857E75`** (used for line numbers, indent guides, bracket border in neutral variants): this hex is **NOT** in the haven token namespace. The nearest brand values are warm-400 (#787066) and warm-500 (#958E85). `#857E75` sits between them. Either (a) the theme established a custom interpolated value, or (b) this is drift. **Resolve in Step 2** — likely should snap to `--haven-warm-500` (#958E85) per "snap drift hex values to current brand canon" precedent (commit b726aa4).

**Dark-teal-only keys** (not present in any other variant):

| Key | Teal Dark | Status |
|---|---|---|
| `editorStickyScroll.background` | `--haven-teal-50` (#010F0C) | 🔴 missing in 3 variants |
| `editorStickyScrollHover.background` | `--haven-teal-100` (#04201C) | 🔴 missing in 3 variants |
| `editorInlayHint.background` | `--haven-teal-200` (#0D322D) @ 19% | 🔴 missing in 3 variants |
| `editorInlayHint.foreground` | `--haven-teal-500` (#3A8478) @ 56% | 🔴 missing in 3 variants |
| `editorInlayHint.typeForeground` | `--haven-teal-600` (#52A395) @ 50% | 🔴 missing in 3 variants |
| `editorInlayHint.parameterForeground` | `--haven-teal-700` (#7CB9AD) @ 44% | 🔴 missing in 3 variants |
| `editorGhostText.foreground` | `--haven-teal-500` (#3A8478) @ 38% | 🔴 missing in 3 variants |

---

## 2. Editor Groups & Tabs

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `editorGroup.border` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 50% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-200` (#3F3933) @ 50% | 🟡 warm-700 |
| `editorGroupHeader.tabsBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-150` (#322E28) | ✅ |
| `editorGroupHeader.noTabsBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-150` (#322E28) | ✅ |
| `tab.activeBackground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-100` (#25211D) | ✅ |
| `tab.activeForeground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-900` (#F3F1EE) | ✅ |
| `tab.activeBorder` (bottom) | `--haven-teal-400` (#1B685E) | — | `--haven-warm-300` (#5B544C) | `--haven-warm-100` (#25211D) @ 0% | 🟡 see note |
| `tab.activeBorderTop` | — | `--haven-teal-600` (#52A395) | — | `--haven-teal-600` (#52A395) | 🔴 light variants |
| `tab.inactiveBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-150` (#322E28) | ✅ |
| `tab.inactiveForeground` | `--haven-warm-300` (#5B544C) | `--haven-teal-700` (#7CB9AD) @ 50% | `--haven-warm-300` (#5B544C) | `--haven-warm-500` (#958E85) | ⚫ |
| `tab.border` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) @ 0% | `--haven-warm-900` (#F3F1EE) | `--haven-warm-150` (#322E28) | ✅ |
| `tab.hoverBackground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-200` (#3F3933) | ✅ |
| `tab.hoverForeground` | — | `--haven-warm-950` (#F8F4EC) | — | — | 🔴 3 missing |
| `tab.unfocusedActiveBackground` | — | `--haven-teal-50` (#010F0C) | — | — | 🔴 3 missing |
| `tab.unfocusedActiveForeground` | — | `--haven-teal-700` (#7CB9AD) | — | — | 🔴 3 missing |
| `tab.unfocusedInactiveBackground` | — | `--haven-teal-100` (#04201C) | — | — | 🔴 3 missing |
| `tab.unfocusedInactiveForeground` | — | `--haven-teal-500` (#3A8478) | — | — | 🔴 3 missing |

**Brand-moment finding (key for Step 5).** The dark variants both use `tab.activeBorderTop` (a top accent rail — the brand-moment treatment, analog to obsidian `b3a2211`). **The light variants use `tab.activeBorder` (side) instead.** Porting the top accent rail to light variants is the most direct brand-moment alignment. The teal-light uses teal-400 for the bottom; the neutral-light uses warm-300 (no accent contrast). Recommendation: add `tab.activeBorderTop` = `--haven-teal-400` (light) / `--haven-warm-400` or `--haven-teal-400` (neutral-light, TBD).

---

## 3. Title Bar

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `titleBar.activeBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-100` (#25211D) | ✅ |
| `titleBar.activeForeground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `titleBar.inactiveBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-100` (#25211D) | ✅ |
| `titleBar.inactiveForeground` | `--haven-warm-300` (#5B544C) | `--haven-teal-500` (#3A8478) | `--haven-warm-300` (#5B544C) | `--haven-warm-600` (#B3ADA4) | ✅ |
| `titleBar.border` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-100` (#25211D) @ 25% | 🟡 warm-700 |

---

## 4. Activity Bar

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `activityBar.background` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-100` (#04201C) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-100` (#25211D) | 🟡 warm-800 |
| `activityBar.foreground` | `--haven-teal-200` (#0D322D) | `--haven-teal-600` (#52A395) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `activityBar.inactiveForeground` | `--haven-warm-500` (#857E75) ⚠ | `--haven-teal-400` (#1B685E) @ 50% | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-500` (#958E85) ⚠ | 🟡 see note |
| `activityBar.border` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-100` (#25211D) | 🟡 warm-700 |
| `activityBarBadge.background` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | ✅ |
| `activityBarBadge.foreground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |

---

## 5. Sidebar

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `sideBar.background` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-100` (#25211D) | ✅ |
| `sideBar.foreground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `sideBar.border` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-100` (#25211D) @ 25% | 🟡 warm-700 |
| `sideBar.dropBackground` | — | `--haven-teal-600` (#52A395) @ 13% | — | — | 🔴 3 missing |
| `sideBarTitle.foreground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `sideBarSectionHeader.background` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-200` (#0D322D) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-100` (#25211D) | 🟡 warm-800 |
| `sideBarSectionHeader.foreground` | `--haven-teal-200` (#0D322D) | `--haven-teal-700` (#7CB9AD) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `sideBarSectionHeader.border` | — | `--haven-teal-200` (#0D322D) @ 0% | — | — | 🔴 3 missing |

---

## 6. Status Bar

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `statusBar.background` | `--haven-teal-300` (#124D45) | `--haven-teal-200` (#0D322D) | `--haven-warm-300` (#5B544C) | `--haven-warm-200` (#3F3933) | ✅ |
| `statusBar.foreground` | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `statusBar.border` | `--haven-teal-200` (#0D322D) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-150` (#322E28)? (#3F3933) ⚠ | `--haven-warm-200` (#3F3933) | 🟡 neutral-light see note |
| `statusBar.debuggingBackground` | `--haven-teal-200` (#0D322D) | `--haven-teal-300` (#124D45) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | ✅ |
| `statusBar.debuggingForeground` | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `statusBar.noFolderBackground` | `--haven-warm-300` (#5B544C) | `--haven-teal-100` (#04201C) | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-100` (#25211D) | 🟡 see note |
| `statusBar.noFolderForeground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-500` (#3A8478) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-600` (#B3ADA4) | ✅ |
| `statusBarItem.hoverBackground` | `--haven-teal-200` (#0D322D) @ 50% | `--haven-teal-300` (#124D45) @ 38% | `--haven-warm-150` (#322E28)? @ 50% | `--haven-warm-200` (#3F3933) @ 50% | ⚫ |
| `statusBarItem.prominentBackground` | — | `--haven-teal-300` (#124D45) | — | — | 🔴 3 missing |
| `statusBarItem.prominentHoverBackground` | — | `--haven-teal-400` (#1B685E) | — | — | 🔴 3 missing |
| `statusBarItem.remoteBackground` | `--haven-teal-300` (#124D45) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | ✅ |
| `statusBarItem.remoteForeground` | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |

---

## 7. Panel (Terminal, Output, Problems)

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `panel.background` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-100` (#25211D) | ✅ |
| `panel.border` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-100` (#25211D) @ 25% | 🟡 warm-700 |
| `panelTitle.activeBorder` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-warm-300` (#5B544C) | `--haven-warm-500` (#857E75) ⚠ | 🟡 neutral-dark see note |
| `panelTitle.activeForeground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `panelTitle.inactiveForeground` | `--haven-warm-300` (#5B544C) | `--haven-teal-500` (#3A8478) | `--haven-warm-300` (#5B544C) | `--haven-warm-600` (#B3ADA4) | ✅ |
| `panelSectionHeader.background` | — | `--haven-teal-200` (#0D322D) | — | — | 🔴 3 missing |
| `panelSectionHeader.border` | — | `--haven-teal-200` (#0D322D) @ 19% | — | — | 🔴 3 missing |
| `panelSection.border` | — | `--haven-teal-200` (#0D322D) @ 19% | — | — | 🔴 3 missing |

---

## 8. Text Blocks (chat, hover, markdown preview)

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `textCodeBlock.background` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-100` (#04201C) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-200` (#3F3933) | 🟡 warm-800 |
| `textBlockQuote.background` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-100` (#04201C) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-200` (#3F3933) | 🟡 warm-800 |
| `textBlockQuote.border` | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-300` (#5B544C) | 🟡 see note |
| `textPreformat.foreground` | `--haven-teal-400` (#1B685E) | `--haven-teal-800` (#A8D1C9) | `--haven-warm-300` (#5B544C) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `textPreformat.background` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-100` (#04201C) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-200` (#3F3933) | 🟡 warm-800 |
| `textLink.foreground` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | ✅ |
| `textLink.activeForeground` | `--haven-teal-200` (#0D322D) | `--haven-teal-700` (#7CB9AD) | `--haven-teal-200` (#0D322D) | `--haven-teal-700` (#7CB9AD) | ✅ |
| `textSeparator.foreground` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) @ 19% | `--haven-warm-700` (#D1CDC6) | `--haven-warm-100` (#25211D) | 🟡 warm-700 |

---

## 9. Chat

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `chat.requestBackground` | `--haven-warm-900` (#F3F1EE) | `--haven-teal-100` (#04201C) | `--haven-warm-900` (#F3F1EE) | `--haven-warm-100` (#25211D) | ✅ |
| `chat.requestBorder` | `--haven-warm-700` (#D1CDC6) @ 38% | `--haven-teal-200` (#0D322D) @ 25% | `--haven-warm-700` (#D1CDC6) @ 38% | `--haven-warm-100` (#25211D) @ 38% | ⚫ |
| `chat.slashCommandBackground` | `--haven-teal-900` (#D0E7E2) @ 25% | `--haven-teal-400` (#1B685E) @ 19% | `--haven-warm-800` (#E7E4DF) @ 38% | `--haven-warm-300` (#5B544C) @ 19% | ⚫ |
| `chat.slashCommandForeground` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-warm-300` (#5B544C) | `--haven-warm-600` (#B3ADA4) | ✅ |

---

## 10. Inputs

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `input.background` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-100` (#25211D) | ✅ |
| `input.foreground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `input.border` | `--haven-warm-500` (#857E75) ⚠ | `--haven-teal-200` (#0D322D) | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-300` (#5B544C) | 🟡 see note |
| `input.placeholderForeground` | `--haven-warm-500` (#857E75) @ 50% ⚠ | `--haven-teal-500` (#3A8478) @ 38% | `--haven-warm-500` (#857E75) @ 50% ⚠ | `--haven-warm-300` (#5B544C) @ 50% | 🟡 see note |
| `inputOption.activeBorder` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | ✅ |
| `inputOption.activeBackground` | `--haven-teal-400` (#1B685E) @ 13% | `--haven-teal-600` (#52A395) @ 13% | `--haven-teal-400` (#1B685E) @ 13% | `--haven-teal-600` (#52A395) @ 13% | ⚫ |
| `inputOption.activeForeground` | — | `--haven-warm-950` (#F8F4EC) | — | — | 🔴 3 missing |
| `inputValidation.errorBackground` | `--haven-error-bg` (#FCE5E3) | `--haven-error-text` (#932B2A) @ 19% | `--haven-error-bg` (#FCE5E3) | `--haven-error-text` (#932B2A) @ 25% | 🔵 |
| `inputValidation.errorBorder` | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | `--haven-error-base` (#C13C3B) | `--haven-error-border` (#D87972) | 🔵 |
| `inputValidation.warningBackground` | `--haven-warning-bg` (#F4EAD5) | `--haven-warning-text` (#754B00) @ 19% | `--haven-warning-bg` (#F4EAD5) | `--haven-warning-text` (#754B00) @ 25% | 🔵 |
| `inputValidation.warningBorder` | `--haven-warning-text` (#754B00) | `--haven-warning-border` (#CEA861) | `--haven-warning-text` (#754B00) | `--haven-warning-border` (#CEA861) | 🔵 |
| `inputValidation.infoBackground` | `--haven-info-bg` (#DFEEF7) | `--haven-info-text` (#0B4E6C) @ 19% | `--haven-info-bg` (#DFEEF7) | `--haven-info-text` (#0B4E6C) @ 25% | 🔵 |
| `inputValidation.infoBorder` | `--haven-info-base` (#287AA3) | `--haven-info-border` (#538EB0) | `--haven-info-base` (#287AA3) | `--haven-info-border` (#538EB0) | 🔵 |

---

## 11. Buttons

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `button.background` | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | ✅ |
| `button.foreground` | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `button.hoverBackground` | `--haven-teal-300` (#124D45) | `--haven-teal-500` (#3A8478) | `--haven-teal-300` (#124D45) | `--haven-teal-300` (#124D45) | ✅ |
| `button.secondaryBackground` | `--haven-warm-800` (#E7E4DF) | `--haven-teal-200` (#0D322D) | `--haven-warm-800` (#E7E4DF) | `--haven-warm-200` (#3F3933) | 🟡 warm-800 |
| `button.secondaryForeground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `button.secondaryHoverBackground` | `--haven-warm-700` (#D1CDC6) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | `--haven-warm-300` (#5B544C) | 🟡 warm-700 |

---

## 12. Dropdown, Badges, Scrollbar

| Key | Teal Light | Teal Dark | Neutral Light | Neutral Dark | Status |
|---|---|---|---|---|---|
| `dropdown.background` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-100` (#25211D) | ✅ |
| `dropdown.foreground` | `--haven-teal-200` (#0D322D) | `--haven-warm-950` (#F8F4EC) | `--haven-teal-200` (#0D322D) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `dropdown.border` | `--haven-warm-500` (#857E75) ⚠ | `--haven-teal-200` (#0D322D) | `--haven-warm-500` (#857E75) ⚠ | `--haven-warm-300` (#5B544C) | 🟡 see note |
| `dropdown.listBackground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-100` (#04201C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-100` (#25211D) | ✅ |
| `badge.background` | `--haven-teal-400` (#1B685E) | `--haven-teal-600` (#52A395) | `--haven-teal-400` (#1B685E) | `--haven-teal-400` (#1B685E) | ✅ |
| `badge.foreground` | `--haven-warm-950` (#F8F4EC) | `--haven-teal-50` (#010F0C) | `--haven-warm-950` (#F8F4EC) | `--haven-warm-700` (#D1CDC6) | ✅ |
| `scrollbar.shadow` | `--haven-teal-200` (#0D322D) @ 6% | `--haven-teal-50` (#010F0C) @ 50% | `--haven-warm-300` (#5B544C) @ 6% | `--haven-warm-100` (#25211D) @ 38% | ⚫ |
| `scrollbarSlider.background` | `--haven-warm-600` (#B3ADA4) @ 25% | `--haven-teal-500` (#3A8478) @ 25% | `--haven-warm-600` (#B3ADA4) @ 25% | `--haven-warm-200` (#3F3933) @ 38% | ⚫ |
| `scrollbarSlider.hoverBackground` | `--haven-warm-600` (#B3ADA4) @ 38% | `--haven-teal-600` (#52A395) @ 38% | `--haven-warm-600` (#B3ADA4) @ 38% | `--haven-warm-200` (#3F3933) @ 50% | ⚫ |
| `scrollbarSlider.activeBackground` | `--haven-warm-500` (#857E75) @ 50% ⚠ | `--haven-teal-600` (#52A395) @ 50% | `--haven-warm-500` (#857E75) @ 50% ⚠ | `--haven-warm-300` (#5B544C) @ 50% | 🟡 see note |

---

## 13. Lists & Trees, Widgets

Same shape as above — abbreviated for length. Full audit in next pass; the
patterns are consistent (active selection = teal accent at varying alphas;
hover = warm-800 surface; focus outline = teal accent at low alpha).

---

## 14. Peek View, Minimap, Breadcrumbs, Git Decorations, Diff Editor, Merge, Focus Border, Terminal, Notifications

Same shape as above — abbreviated. **Critical findings worth surfacing now:**

- **Terminal ANSI palette (per [README.md](README.md) "no purple" rule)** —
  ansiMagenta is `--haven-error-text` (#932B2A) in light / `--haven-error-border`
  (#D87972) in dark, consistent with the brand "no purple" constraint. ✅ All 4
  variants.
- **Focus border:** Teal Light = `--haven-teal-500` (#3A8478); Teal Dark = `--haven-teal-600` (#52A395) @ 50%; Neutral Light = `--haven-teal-400` (#1B685E); Neutral Dark = `--haven-teal-400` (#1B685E). All ✅.
- **terminalCursor.foreground:** consistently `--haven-teal-400` (light) / `--haven-teal-600` (dark). ✅

---

## 15. Coverage gap (dark-teal-only surfaces)

These keys exist **only** in `haven-dark.json` and are absent in the other 3
variants. Worth resolving as part of Step 3 (surface mapping) — the dark-teal
variant has clearly received more brand-fidelity love than its siblings.

- `editorStickyScroll.*`, `editorStickyScrollHover.*`
- `editorInlayHint.*`, `editorGhostText.*`
- `selection.background` (top-level)
- `quickInput.*`, `quickInputList.*`, `quickInputTitle.*`
- `commandCenter.*`
- `banner.*`
- `welcomePage.*`, `walkThrough.*`
- `settings.*`
- `debugToolBar.*`, `debugIcon.*`, `debugConsole.*`, `debugConsoleInputIcon.*`
- `semanticTokenColors` (semantic highlighting)
- `widget.border`

**Recommendation:** propagate to the other 3 variants in the brand-moment pass
(Step 5) or as a separate carry-forward. The neutral-dark especially should
receive these — same depth-map architecture, just warm-family tokens.

---

## 16. Syntax (`tokenColors`)

The two light variants share an identical syntax palette; the two dark variants
share an identical syntax palette (per the README — "all four share identical
syntax highlighting"). Verified true for the light pair; **dark pair has
divergence** worth noting: `tokenColors.Variables.foreground` is `#F8F4EC`
(warm-950) in haven-dark.json but `#D1CDC6` (warm-700) in haven-warm-dark.json.
Same pattern for `Markdown Headings`, `Markdown Bold`. **This is intentional**
— darker editor backgrounds (teal-50 #010F0C ≈ 19.5:1 contrast) tolerate the
brightest text; warmer backgrounds (warm-100 #25211D ≈ 19.6:1) use a warmer
foreground that doesn't pop sharp against the warm chrome. ✅ as designed.

Light syntax palette:

| Role | Hex | Brand token | Hue logic |
|---|---|---|---|
| Comments | #5B544C | `--haven-warm-300` | warm neutral, italic |
| Keywords, tags, CSS props, JSON keys, template expressions, MD italic/link | #1B685E | `--haven-teal-400` | teal = structure |
| Types/Classes, CSS selectors, MD inline code, this/self | #124D45 | `--haven-teal-300` | teal = structure (heavier) |
| Functions, HTML attrs, decorators | #3A643D | `--haven-sage-400` | sage = organic |
| Strings, CSS values | #754B00 | `--haven-warning-text` | warm amber = values 🔵 |
| Constants, CSS units | #0B4E6C | `--haven-info-text` | slate blue = constants 🔵 |
| Variables, MD headings/bold | #0D322D | `--haven-teal-200` | text primary |
| Properties, operators | #5B544C | `--haven-warm-300` | text secondary |
| Regex, invalid | #C13C3B | `--haven-error-base` | error 🔵 |
| Deprecated | #932B2A | `--haven-error-text` | error darker 🔵 |
| Inserted (markup) | #3A8E64 | `--haven-success-base` | success 🔵 |
| Changed (markup) | #754B00 | `--haven-warning-text` | warning 🔵 |

Dark syntax palette (teal-dark; neutral-dark uses warm-700 for variables/MD):

| Role | Hex | Brand token | Hue logic |
|---|---|---|---|
| Comments | #958E85 | `--haven-warm-500` | warm neutral, italic |
| Doc Comments | #B3ADA4 | `--haven-warm-600` | brighter than regular |
| Keywords, tags, CSS props, JSON keys, MD italic | #7CB9AD | `--haven-teal-700` | teal = structure |
| Control flow | #A8D1C9 | `--haven-teal-800` | emphasized teal, italic |
| Import/Export | #3A8478 @ 56% | `--haven-teal-500` | muted teal |
| Types/Classes, CSS selectors, MD inline code, this/self | #A8D1C9 | `--haven-teal-800` | teal heavier |
| Functions, HTML attrs | #81B983 | `--haven-sage-700` | sage = organic |
| Decorators | #ACCFAD | `--haven-sage-800` | brighter sage, italic |
| Strings, CSS values, Changed | #CEA861 | `--haven-warning-border` | warm amber = values 🔵 |
| Constants, CSS units | #6FA5C4 | (light info-blue) | slate blue 🔵 |
| Variables, MD headings/bold (teal-dark) | #F8F4EC | `--haven-warm-950` | warm off-white |
| Variables, MD headings/bold (neutral-dark) | #D1CDC6 | `--haven-warm-700` | warm off-white (softer) |
| Properties (teal-dark) | #D1CDC6 | `--haven-warm-700` | softer than variables |
| Properties (neutral-dark) | #D1CDC6 | `--haven-warm-700` | same as variables (subtle) |
| Operators | #B3ADA4 | `--haven-warm-600` | mid warm |
| Regex (dark) | #E09990 | (lightened error-border) | error 🔵 |
| Markdown links, template expressions | #52A395 | `--haven-teal-600` | teal = link accent |
| Inserted (markup) | #81B983 | `--haven-sage-700` | success-ish |
| Deleted (markup), Invalid | #D87972 | `--haven-error-border` | error 🔵 |

**Constants `#6FA5C4` and Regex-dark `#E09990` are NOT in the haven token
namespace** — they are lightened-for-dark-contrast values authored ad hoc for
AAA contrast. Two options for resolution:
- (a) Snap to nearest brand token (e.g., `#6FA5C4` → `--haven-info-border` #538EB0 is the closest brand value, but it fails AA at the dark editor background — `#6FA5C4` was clearly chosen for contrast).
- (b) Promote these to the brand canon as new tokens (`--haven-info-dark-text`, `--haven-error-dark-text-bright`).

Flag for Step 2 or for Haven Visual Designer review.

---

## 17. Summary findings

1. **Token discipline is mostly there** — inline comments already reference
   brand tokens (`warm-900`, `teal-400`, etc.). This map extracts that
   discipline into a single index. The harder discipline (one canonical map
   that drift is checked against) was the gap, not the per-key thinking.
2. **`#857E75` is not in the canon.** Used in 7+ keys across light/neutral
   variants. Either snap to `--haven-warm-500` (#958E85) or accept as a custom
   interpolated token (and add to the namespace). **Resolve in Step 2.**
3. **Cena Color System v2 sand lift (2026-05-30) not yet propagated.**
   warm-800/700/600 still on pre-lift values. Same gap exists in the obsidian
   theme. Resolve in Step 2 — likely as a coordinated brand-side decision, not
   a unilateral vscode-theme patch.
4. **`#6FA5C4` and `#E09990` are ad-hoc dark-contrast values** not in the
   token namespace. Either snap or promote — flag for HVD.
5. **Dark-teal has ~20 surfaces the other 3 variants don't.** Coverage gap to
   close in Step 5 (especially for neutral-dark, which has the same
   depth-map architecture and should mirror).
6. **Brand-moment treatment for light variants** — only the dark variants use
   `tab.activeBorderTop` (top accent rail). Light variants use side
   `tab.activeBorder`. Porting the top rail to light is the most direct
   brand-moment alignment with obsidian commit `b3a2211`. **Land in Step 5.**

---

## Provenance

- Authored 2026-05-31 as Step 1 of `~/.claude/plans/haven-vscode-theme-port-from-obsidian.md`.
- Template: [`OBSIDIAN-TOKEN-MAP.md`](../haven-obsidian-theme/OBSIDIAN-TOKEN-MAP.md) (the same discipline applied to Obsidian CSS variables).
- Brand canon read: `cena-health-brand/_tokens/generated/palette.css` at HEAD 2026-05-31 06:51 PDT.
- Vendored token names from `Lab/haven-obsidian-theme/src/01-tokens.css`.
