# Haven UI → VS Code Surface Mapping Audit

**Purpose.** Every workbench surface this theme touches mapped to its canonical
Haven UI analog — so the theme stops freelancing surface treatments and starts
translating the pattern library where an analog exists.

**Why.** The pattern library at
`Lab/haven-ui/packages/design-system/pattern-library/` is the canonical Haven
UI spec. This theme should be a *translation layer* into VS Code's
`workbench.colorCustomizations` namespace, not a parallel design system. The
`define-once` and `catalog-first` vault rules both apply: every "what color /
what spacing / what surface logic for X" is answered once in haven-ui's
`components.css` and `tokens/`; the vscode theme should query that catalog,
not invent.

**Why VS Code is structurally different from Obsidian.** Obsidian is a
markdown editor — most of its surfaces (body prose, callouts, tags, tables,
HRs) have direct haven-ui document-prose analogs. VS Code is a code editor —
most editor-body surfaces are syntax (handled by `tokenColors`) or
code-workflow chrome (peek view, diff, debug, merge) with no haven-ui analog
to mirror. The PL match concentrates in **workbench chrome** (sidebar,
topbar, command palette, inputs, buttons, alerts) and **widgets/popovers**.

**Audit sources.**
- `Lab/haven-ui/packages/design-system/pattern-library/COMPONENT-INDEX.md` — ground truth for what exists
- `Lab/haven-ui/packages/design-system/src/styles/tokens/components.css` — semantic class implementations
- `Lab/haven-ui/packages/design-system/src/styles/tokens/{colors,typography,spacing}.css` — token values
- `Lab/haven-ui/DESIGN.md` — design system canon
- `Lab/haven-obsidian-theme/.project-docs/references/haven-ui-surface-mapping.md` — sibling audit (the template)

**Status key.**
- 🟢 = Haven UI spec found, mapping clear, ready to translate
- 🟡 = Haven UI analog exists but the translation needs judgment (no 1:1 class, or vscode-specific composition)
- 🔴 = No Haven UI analog; vscode-specific workflow (code review, debug, merge); brand-fidelity via tokens only
- ⚫ = VS Code internal chrome with no UI-app analog and no useful brand-fidelity move; defaults are fine

**Brand-token sand inversion.** Haven UI uses Tailwind utility colors (`sand-300`,
`sand-700`) which map via brand canon (sand = warm family — `--haven-warm-*`).
The scale inverts: brand `sand-50` = lightest → vendored `--haven-warm-950` = lightest.
See `VSCODE-TOKEN-MAP.md` for the full mapping.

---

## 1. Workbench chrome — primary surfaces (the things always visible)

| VS Code surface | Haven UI analog | Spec source | Translation | Status |
|---|---|---|---|---|
| **Tabs** (`tab.*`) | No 1:1 (PL apps use route-based panels, not editor tabs) | — | Tabs are vscode-specific. Brand-fidelity moves: (a) active tab punches through to editor bg (already done dark, not light); (b) `tab.activeBorderTop` accent rail = `--haven-teal-400` (light) / `--haven-teal-600` (dark) — already done dark, **port to light in Step 5**; (c) inactive tab = chrome bg one step above editor (sand-100 light, teal-100 dark). | 🟡 |
| **Activity Bar** (`activityBar.*`) | `.app-shell-sidebar` icon-rail register OR `.app-sidebar-nav` (icon-only collapsed) | `layout-app-shell-responsive.html`, COMPONENT-INDEX | Icon rail surface: sand-100 (light) / teal-100 (dark) — already aligned. Icon color resting state: sand-600 (light), teal-600 (dark). Active icon foreground: teal-400 (light), teal-600 (dark). Badge: `--haven-teal-400`. **The icon-resting-color in light is currently `--haven-teal-200` (#0D322D) — that's the text-primary color, not the PL's "secondary icon" sand-600. Worth realigning.** | 🟡 |
| **Sidebar** (`sideBar.*`) | `.app-shell-sidebar` | `layout-app-shell-responsive.html` | Surface: `bg-sand-50` (warm-950 in token vocab? No — sand-50 is the LIGHTEST; vendored as warm-950 #F8F4EC). Wait — the PL sidebar uses sand-100 surface (the warm-900 in vendored vocab #F3F1EE). Current theme aligns: `sideBar.background` = warm-900 light / teal-100 dark. ✅ Foreground = sand-800 dark text; current: teal-200 light / warm-950 dark. ✅ Border between sidebar and editor = sand-200 (warm-800) — current: warm-700 (#D1CDC6) ⚠ slightly heavier than PL spec. | 🟢 |
| **Status Bar** (`statusBar.*`) | No 1:1 — closest is `.sticky-footer` (`layout-sticky-footer.html`) | — | Status bar is vscode-specific (build status, errors, branch, etc.). The sticky-footer pattern is action-bar oriented, not status. Stay vscode-flavored. Current teal-300 (light) / teal-200 (dark) bg is a defensible brand-moment treatment — neutral variant correctly uses warm-300 instead per the "neutral = no teal chrome surfaces" rule. | 🟡 |
| **Title Bar** (`titleBar.*`) | `.app-shell-topbar` | `layout-app-shell-responsive.html` | Topbar register per PL: sand-50 bg, sand-200 bottom border, h-14 (56px). Current theme: warm-900 (light) / teal-100 (dark) bg ✅; border warm-700 ⚠ should be warm-800 per PL. Foreground text-primary ✅. | 🟡 |
| **Editor Groups Border** (`editorGroup.border`) | No 1:1 — closest is `.divider-vertical` (`layout-divider.html`) | `components.css` | Vertical divider between split editors. PL `.divider-vertical` uses sand-200 (warm-800) at 1px. Current: warm-700 (#D1CDC6) light / teal-200 at 50% alpha dark. 🟡 light should snap to warm-800. | 🟡 |
| **Panel** (terminal/output, `panel.*`) | No 1:1 (PL doesn't have a bottom panel pattern) | — | Vscode-flavored. Surface = sidebar bg (warm-900 / teal-100). Active tab indicator = `--haven-teal-400` (light) / `--haven-teal-600` (dark) bottom border. Current matches. ✅ | 🟢 |
| **Breadcrumbs** (`breadcrumb.*`) | No PL analog (apps use `page-header` instead) | — | Stay vscode-flavored. Color register: text-secondary at rest, text-primary at focus. Current aligned. | 🟢 |

---

## 2. Editor body surfaces — chrome around code

| VS Code surface | Haven UI analog | Translation | Status |
|---|---|---|---|
| **Editor background/foreground** | `.code-view-body` (agentic code surface) | Code view bg = one tone away from primary surface. Light: sand-50 (warm-950) editor on sand-100 (warm-900) chrome ✅ matches. Dark: teal-50 deepest, chrome teal-100 ✅. Foreground = sand-800/900 text. Current matches. | 🟢 |
| **Line numbers** (`editorLineNumber.foreground`) | No PL analog (apps don't show line numbers) | Stay vscode-flavored. Want a muted text token (sand-500 / warm-500 register). Current `#857E75` is drift — see token map. | 🟡 |
| **Indent guides** (`editorIndentGuide.*`) | No PL analog | Vscode-internal visual hint. Subtle warm/teal at low alpha. Current works. | ⚫ |
| **Rulers** (`editorRuler.foreground`) | No PL analog | Same as above. ⚫ | ⚫ |
| **Cursor** (`editorCursor.foreground`) | No PL analog (PL focus rings, not blinking carets) | Use `--haven-teal-400` (light) / `--haven-teal-600` (dark). Current matches. ✅ | 🟢 |
| **Bracket match** (`editorBracketMatch.*`) | No PL analog | Vscode-internal. ⚫ | ⚫ |
| **Selection** (`editor.selectionBackground`) | No 1:1 — closest is `.field-input::selection` if PL ever specs it | Use brand teal at low alpha (light: teal-900 = D0E7E2; dark: sage-700 = 81B983 at 38%). Current matches. ✅ | 🟢 |
| **Find / find-match** (`editor.findMatchBackground`) | No 1:1 | Use teal-900 light / warning-border dark (CEA861) — yellow-on-dark is conventional find highlight. Current matches. ✅ | 🟢 |
| **Sticky scroll** (`editorStickyScroll.*`) | `.record-header` | `layout-record-header.html` | Sticky scroll is conceptually a record-header (identity bar that pins on scroll). Surface = editor bg (sand-50) so it punches through cleanly; subtle bottom shadow. Only present in haven-dark — **propagate to other 3 variants in Step 5**. | 🟢 |
| **Inlay hints** (`editorInlayHint.*`) | No PL analog (inline annotations not specced) | Stay vscode-flavored. Muted teal/warm. Only in haven-dark — propagate. | 🟡 |
| **Ghost text** (`editorGhostText.foreground`) | No PL analog (AI completion is vscode-specific UI) | Stay vscode-flavored at low alpha. Only in haven-dark — propagate. | 🟡 |
| **Whitespace** (`editorWhitespace.foreground`) | No PL analog | Vscode-internal. ⚫ | ⚫ |
| **Fold background** (`editor.foldBackground`) | No PL analog | Vscode-internal. ⚫ | ⚫ |

---

## 3. Inputs & forms

| VS Code surface | Haven UI analog | Spec source | Translation | Status |
|---|---|---|---|---|
| **Text input** (`input.*`) | `.field-input` + `.field-row` | `components.css` — `.field-input { border border-sand-200 bg-sand-50 text-sand-900 rounded-md px-3 py-2 }` | Bg = sand-50 (warm-950) ✅; border = sand-200 (warm-800); current border is `#857E75` ⚠ drift (see token map). Should snap to `--haven-warm-800` (#E7E4DF) per PL. Focus ring: teal-400. | 🟡 |
| **Placeholder** (`input.placeholderForeground`) | `.field-input::placeholder` | components.css | PL: sand-500 (warm-500 vendored). Current `#857E75 @ 50%` is drift on top of drift. | 🟡 |
| **Input option toggles** (`inputOption.*`) | `.btn-icon` toggle state | components.css | When active: teal-400 accent border + low-alpha teal bg. Current matches. ✅ | 🟢 |
| **Validation error** (`inputValidation.error*`) | `.field-row-error` | components.css — `.field-row-error` | PL uses `--haven-error-bg` for the body and `--haven-error-base` for the border. Current matches. ✅ 🔵 | 🟢 |
| **Validation warning** (`inputValidation.warning*`) | `.field-row` warning variant (if specced) | components.css | Same pattern: `--haven-warning-bg` body, `--haven-warning-text` border (light) / `--haven-warning-border` border (dark). Current matches. ✅ 🔵 | 🟢 |
| **Validation info** (`inputValidation.info*`) | `.alert-info` body register | components.css | `--haven-info-bg` body, `--haven-info-base` border (light) / `--haven-info-border` border (dark). Current matches. ✅ 🔵 | 🟢 |
| **Dropdown** (`dropdown.*`) | `.dropdown` / `.field-input` with select chevron | components.css | Same as text input: sand-50 bg, sand-200 border. Border currently `#857E75` ⚠ — same drift as input.border. | 🟡 |

---

## 4. Buttons

| VS Code surface | Haven UI analog | Spec source | Translation | Status |
|---|---|---|---|---|
| **Primary button** (`button.background`) | `.btn-primary` | components.css | bg `--haven-teal-400`; fg `--haven-warm-950`; hover bg `--haven-teal-300`. Current matches. ✅ | 🟢 |
| **Secondary button** (`button.secondary*`) | `.btn-secondary` | components.css | bg `--haven-warm-800` (light) / `--haven-teal-200` (dark); fg text-primary; hover one step darker. Current matches sand-200 ✅ (subject to v2 sand lift carry-forward). | 🟢 |
| **Button hover** (`button.hoverBackground`) | `.btn-primary:hover` | components.css | teal-300 darker register. Current matches. ✅ | 🟢 |

---

## 5. Lists & trees

| VS Code surface | Haven UI analog | Spec source | Translation | Status |
|---|---|---|---|---|
| **Active selection** (`list.activeSelection*`) | `.sidebar-nav-item.active` | components.css | PL: left rail accent + sand-100 bg tint + text-primary fg. Current vscode: teal-900 bg (light) / teal-400 @ 50% (dark) — bg-only, no left rail (vscode doesn't expose one for tree rows). ✅ as far as bg goes; left-rail not portable. | 🟡 |
| **Inactive selection** (`list.inactiveSelection*`) | `.sidebar-nav-item:not(.active)` selected state | — | Sand-100 (light) / teal-200 @ 25% (dark) — current matches. ✅ | 🟢 |
| **Hover** (`list.hover*`) | `.sidebar-nav-item:hover` | components.css | sand-100 bg tint. Current matches. ✅ | 🟢 |
| **Focus** (`list.focus*`) | `.sidebar-nav-item:focus-visible` | components.css | Teal-tinted bg + outline. Current uses focus outline `--haven-teal-600` at 38% alpha (dark) — defensible. ✅ | 🟢 |
| **Highlight** (`list.highlightForeground`) | Search-match highlight in list rows | — | Teal accent — current matches. ✅ | 🟢 |

---

## 6. Widgets & popovers

| VS Code surface | Haven UI analog | Spec source | Translation | Status |
|---|---|---|---|---|
| **Command palette / Quick input** (`quickInput.*`, `commandCenter.*`) | `complex-command-palette.html` family | COMPONENT-INDEX (PL `.command-palette`) | High-impact port. PL: frosted-glass surface + suggestion-item register. Currently only in haven-dark (commandCenter, quickInput). **Port to other variants in Step 5**, and align the visual register with PL command-palette. | 🟢 |
| **Suggest widget** (`editorSuggestWidget.*`) | `.dropdown` listbox | components.css | Surface = chrome bg (warm-900 light / teal-100 dark) ✅; selected item = active selection register ✅. Current matches. | 🟢 |
| **Hover widget** (`editorWidget.*`) | `.tooltip` (PL Preline hs-tooltip override) | obsidian audit + haven.css | PL tooltip: sand-800 bg + sand-50 text. Vscode hover widget is multi-line + structured — closer to `.card` pattern. Surface = chrome bg ✅; border = sand-200 ⚠ (currently warm-700). | 🟡 |
| **Peek view** (`peekView*`) | No PL analog (code-review pattern not specced) | — | Stay vscode-flavored. Brand-fidelity via accent border (`--haven-teal-600` dark / `--haven-teal-400` light). 🔴 no analog. | 🔴 |
| **Notifications** (`notifications.*`, `notificationsErrorIcon.*` etc.) | `.alert` family OR `.alert-banner-agentic` | components.css | PL alert: surface + icon + close. Map: notification bg = chrome bg; icon fg per severity = functional token (error/warning/info). Current matches the severity-color portion ✅; surface is chrome-tinted (sand-100 / teal-100) ✅. | 🟢 |
| **Banner** (`banner.*`) | `.alert-banner-agentic` | COMPONENT-INDEX | Direct PL match. Only in haven-dark — propagate. Surface dark teal-200; iconForeground teal-600. ✅ as designed; propagate. | 🟢 |
| **Welcome page** (`welcomePage.*`) | `.card` family + page-header | components.css, layout-card.html, layout-page-header.html | PL: card grid for tiles. Only in haven-dark. Surface = chrome bg, tile bg = chrome ✅, tile border = sand-200 ⚠ (currently warm at 25% alpha). Propagate to other variants. | 🟢 |
| **Settings editor** (`settings.*`) | `.field-row` repeated | components.css | Modified-item indicator = teal-400 accent. PL field-rows have a similar left-rail-on-modified pattern. ✅ aligned. Only in haven-dark — propagate. | 🟢 |

---

## 7. Terminal

| VS Code surface | Haven UI analog | Translation | Status |
|---|---|---|---|
| **Terminal bg/fg** (`terminal.background`, `terminal.foreground`) | No PL analog (PL apps don't embed terminals) | Use chrome bg + text-primary. Current matches. ✅ | 🟢 |
| **ANSI palette** (`terminal.ansi*`) | Brand functional + neutral tokens | All 4 variants align ANSI to brand functional tokens (error/warning/success/info). **Important brand constraint**: ansiMagenta = `--haven-error-text` (no purple in brand). Current matches the rule. ✅ | 🟢 |
| **Terminal selection** | Use same selection register as editor | Current uses teal-900 (light) / teal-600 @ 25% (dark) / warm-800 (neutral-light) — defensible. ✅ | 🟢 |
| **Cursor** (`terminalCursor.foreground`) | Same as editorCursor | Teal-400 (light) / teal-600 (dark). Current matches. ✅ | 🟢 |

---

## 8. Code-workflow chrome (no PL analog)

| VS Code surface | Haven UI analog | Translation | Status |
|---|---|---|---|
| **Diff editor** (`diffEditor.*`) | No PL analog | Stay vscode-flavored. Inserted = sage @ low alpha; removed = error @ low alpha. Current matches. 🔵 | 🔴 |
| **Merge conflicts** (`merge.*`) | No PL analog | Stay vscode-flavored. Current alpha values match the diff-editor pattern. 🔵 | 🔴 |
| **Git decorations** (`gitDecoration.*`) | No PL analog | Use brand functional tokens: added = `--haven-success-base`, modified = `--haven-teal-400` (light) / `--haven-warning-border` (dark), deleted = `--haven-error-base/border`. Current matches. ✅ 🔵 | 🟢 |
| **Editor gutter** (`editorGutter.*`) | No PL analog | Same as git decorations. Current matches. ✅ 🔵 | 🟢 |
| **Debug** (`debugIcon.*`, `debugToolBar.*`, `debugConsole.*`) | No PL analog | Stay vscode-flavored. Brand-fidelity via functional tokens for severity. Current matches in haven-dark. Only in haven-dark — propagate. | 🔴 |
| **Minimap** (`minimap.*`, `minimapGutter.*`) | No PL analog | Vscode-internal. Brand tokens for find-match (teal-900 / warning-border), selection (teal accent), severity (error/warning). Current matches. ✅ | 🔴 |

---

## 9. Other surfaces

| VS Code surface | Haven UI analog | Translation | Status |
|---|---|---|---|
| **Focus border** (`focusBorder`) | `.focus-ring` token (PL focus utility) | `--haven-teal-500` (light teal) / `--haven-teal-600` @ 50% (dark teal) / `--haven-teal-400` (light + dark neutral). Current matches. ✅ | 🟢 |
| **Scrollbar** (`scrollbar.shadow`, `scrollbarSlider.*`) | No PL analog (browser-native) | Vscode-internal. Subtle warm/teal at low alpha. Current works. ⚫ | ⚫ |
| **Selection (top-level)** (`selection.background`) | Same as editor.selectionBackground | Dark themes have this; light themes don't. Add for parity? Not load-bearing. | 🟡 |
| **Sticky-scroll surfaces** (haven-dark only) | `.record-header` pattern | See section 2 — propagate. | 🟢 |

---

## 10. Recommended sweep order

After this audit lands, implementation sweeps proceed by **visibility frequency × brand-moment impact**. The frontloaded items are the ones a developer sees every minute:

1. **Tabs — top accent rail for light variants.** Brand-moment alignment with obsidian `b3a2211`. Add `tab.activeBorderTop` to haven-light.json and haven-warm-light.json. Drop `tab.activeBorder` (side) in favor of the top rail. — Step 5 primary.
2. **Activity bar icon foreground.** Realign light variants' resting icon to sand-600 (`--haven-warm-400` register), not text-primary teal-200. PL spec says secondary icons use the sand-600 register.
3. **Sidebar border.** Snap to `--haven-warm-800` (PL spec sand-200) instead of warm-700.
4. **Title bar border.** Same snap — warm-700 → warm-800.
5. **Editor group border (split panes).** Same snap on light variants.
6. **Status bar — accept vscode-flavored.** Defensible brand-moment treatment; no PL change needed.
7. **Command palette / quick input** — propagate the haven-dark spec to the other 3 variants. Align with PL command-palette family register.
8. **Sticky scroll** — propagate to other 3 variants. Use editor-bg + record-header-style.
9. **Notifications surface** — confirm chrome-bg alignment across all variants.
10. **Banner / welcome page / settings editor** — propagate to other 3 variants.
11. **Inlay hints / ghost text** — propagate to other 3 variants. Vscode-flavored, no PL change.
12. **Debug toolbar / debug console** — propagate to other 3 variants. Same functional-token approach.
13. **Input border drift (`#857E75`)** — wait for HVD adjudication (carry-forward, see plan).
14. **Cena Color System v2 sand lift (warm-800/700/600)** — wait for coordinated brand-side push (carry-forward).

Items 🟢 are ready to translate; items 🟡 carry judgment notes inline; 🔴 stay vscode-flavored; ⚫ unchanged.

---

## 11. Coverage parity (the dark-teal-only gap)

The dark-teal variant has ~20 surfaces absent in the other 3 variants:

- `editorStickyScroll.*`, `editorStickyScrollHover.*`
- `editorInlayHint.*` (4 keys)
- `editorGhostText.foreground`
- `selection.background` (top-level)
- `quickInput.*` (5 keys), `quickInputList.*` (3 keys), `quickInputTitle.*`
- `commandCenter.*` (6 keys)
- `banner.*` (3 keys)
- `welcomePage.*` (3 keys), `walkThrough.embeddedEditorBackground`
- `settings.*` (4 keys)
- `debugToolBar.*` (2 keys), `debugIcon.*` (10 keys), `debugConsole.*` (3 keys), `debugConsoleInputIcon.foreground`
- `semanticTokenColors` (whole block — semantic highlighting)
- `widget.border`

**Coverage parity recommendation:** the haven-dark variant clearly received the deepest brand-fidelity love; the other 3 should mirror, **especially haven-warm-dark** which uses the same Layer 0–5 depth-map architecture and would benefit cleanly from warm-family tokens at the same depths.

The light variants are a different ask — many of these surfaces (debug, banner, walkthrough) read differently on light bg and may need their own brand-moment thinking, not a mechanical translation. **Land in Step 5 incrementally** — start with the easiest cleanups (semanticTokenColors, settings, command palette), defer the heavier moves to follow-up sessions.

---

## Provenance

- Authored 2026-05-31 as Step 3 of `~/.claude/plans/haven-vscode-theme-port-from-obsidian.md`.
- Template: [haven-ui-surface-mapping.md](../haven-obsidian-theme/.project-docs/references/haven-ui-surface-mapping.md) (the same audit applied to Obsidian surfaces).
- PL canon read: `Lab/haven-ui/packages/design-system/pattern-library/COMPONENT-INDEX.md` at HEAD 2026-05-31.
- Token-level mapping companion: [VSCODE-TOKEN-MAP.md](VSCODE-TOKEN-MAP.md).
