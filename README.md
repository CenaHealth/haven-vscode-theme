# Haven — VS Code Theme

A warm, accessible VS Code theme built from the Cena Health brand design system. Four variants: teal and neutral, each in light and dark.

## Variants

| Theme | Editor | Chrome | Character |
|-------|--------|--------|-----------|
| **Haven Teal Light** | Warm white (`#FBFAF8`) | Warm neutral (`#F3F1EE`) + teal accents | Teal status bar, selections, and badges |
| **Haven Teal Dark** | Deep teal-black (`#010F0C`) | Rising teal chrome (`#04201C`) | Immersive chromatic dark |
| **Haven Neutral Light** | Warm white (`#FBFAF8`) | Warm neutral (`#F3F1EE`) + warm accents | Paper-like warmth, minimal color |
| **Haven Neutral Dark** | Deep brown-black (`#0E0C0A`) | Rising warm chrome (`#1C1914`) | Warm earth tones |

All four share identical syntax highlighting — only the chrome surfaces change.

## Syntax palette

| Role | Light | Dark | Hue logic |
|------|-------|------|-----------|
| Keywords, tags | `#1B685E` | `#7CB9AD` | Teal = structure |
| Types, classes | `#124D45` | `#A8D1C9` | Teal = structure |
| Functions | `#3A643D` | `#81B983` | Sage = organic |
| Strings | `#754B00` | `#CEA861` | Warm amber = values |
| Numbers, constants | `#0B4E6C` | `#6FA5C4` | Slate blue = constants |
| Comments | `#5B544C` | `#A69E95` | Warm neutral, italic |

Every syntax color passes WCAG AA (4.5:1) against its editor background. Most exceed AAA (7:1).

## Installation

### From source (symlink)

```bash
# Clone the repo
git clone https://github.com/aaronsleeper/haven-vscode-theme.git

# Symlink into VS Code extensions
ln -s "$(pwd)/haven-vscode-theme" \
  ~/.vscode/extensions/cena-health.haven-theme-0.1.0

# Restart VS Code, then:
# Cmd+K Cmd+T → select "Haven Teal Light", "Haven Teal Dark", etc.
```

### Manual install

Copy the entire project folder into `~/.vscode/extensions/` and restart VS Code.

## Companion editor settings

The theme controls colors but VS Code doesn't expose typography, motion, or bracket pair colors through theme JSON. To get the full Haven experience, copy the settings from `.vscode/settings.json` into your user or workspace settings:

```jsonc
// Typography — Source Code Pro (brand monospace)
"editor.fontFamily": "'Source Code Pro', monospace",
"editor.fontSize": 14,
"editor.lineHeight": 1.55,
"editor.fontLigatures": false,

// Terminal — same font, slightly smaller
"terminal.integrated.fontFamily": "'Source Code Pro', monospace",
"terminal.integrated.fontSize": 13,
"terminal.integrated.lineHeight": 1.45,

// Motion — smooth cursor and scrolling
"editor.cursorBlinking": "smooth",
"editor.cursorSmoothCaretAnimation": "on",
"editor.smoothScrolling": true,
"workbench.list.smoothScrolling": true,
"terminal.integrated.smoothScrolling": true,

// Line length — 75 char ruler (brand typography spec)
"editor.rulers": [75],
"editor.wordWrapColumn": 75,

// Minimap off (reduces visual noise)
"editor.minimap.enabled": false
```

The full `.vscode/settings.json` also includes per-theme bracket pair colorization using the brand teal/sage/blue/amber cycle. See the file for the complete configuration.

### Font installation

Haven uses [Source Code Pro](https://github.com/adobe-fonts/source-code-pro) for the editor and terminal. Install it before applying the companion settings:

- **macOS**: `brew install --cask font-source-code-pro`
- **Manual**: Download from [Google Fonts](https://fonts.google.com/specimen/Source+Code+Pro) and install

## Design principles

- **No pure white or black** — all surfaces use brand chromatic values
- **Editor as pit** — the editor is always the darkest (dark themes) or lightest (light themes) surface for maximum text contrast
- **Chrome rises** — sidebar, panels, and tab bar sit one or two stops above the editor
- **Teal = structure, sage = organic** — syntax colors follow a consistent semantic mapping across all four variants
- **WCAG AA minimum** — every text color passes 4.5:1 against its background

## Files

```
themes/
  haven-light.json       Haven Teal Light
  haven-dark.json        Haven Teal Dark
  haven-warm-light.json  Haven Neutral Light
  haven-warm-dark.json   Haven Neutral Dark
.vscode/
  settings.json          Companion typography, motion, bracket colors
package.json             Extension manifest
```

## License

MIT
