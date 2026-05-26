<h1 align="center">
  <img src="https://raw.githubusercontent.com/thang-nm/Flow-Icons/main/logo.png" width="160" alt="Flow Icons"/><br/>
  <a href="https://flow-icons.pages.dev">Flow Icons</a>
</h1>

<p align="center">
  🌼 Flow Icons ported to Zed
</p>

![Flow Icons Preview](https://raw.githubusercontent.com/thang-nm/Flow-Icons/main/preview.png)

## Installation

Download the Extension using:

```bash
git clone https://github.com/BenjaminHalko/flow-icons-zed.git
```

Inside ZED, install the extension using the "Install Dev Extension" button

## Extra Icons

The extension comes with the base icon set, but if you want to use the premium icon set, then you will need to run the script to fetch the icons.

```bash
node update-icons.cjs <FLOW_ICONS_LICENSE>
```

## Available Themes

| Theme | Appearance |
| --- | --- |
| Flow Deep | Dark |
| Flow Deep (Light) | Light |
| Flow Dim | Dark |
| Flow Dim (Light) | Light |
| Flow Dawn | Dark |
| Flow Dawn (Light) | Light |
| Flow You | Dark |
| Flow You (Light) | Light |

Pick one via the command palette → `icon theme selector: toggle`.

## Customization

You can customize which icons appear for files and folders by creating a `config.json` in the repo root, and then running `update-icons`

| Setting | Purpose |
| --- | --- |
| `folderColor` | Default folder color: `gray`, `blue`, `brown`, `green`, `lime`, `orange`, `pink`, `purple`, `red`, `sky`, `teal`, `yellow` |
| `specificFolders` | If `false`, all directories use the default folder icon (no per-name icons like `src`, `tests`, `components`) |
| `filesReplacements` | Swap one file icon for another, typically an `-alt` variant: `{ "rust": "rust-alt", "kotlin": "kotlin-alt" }` |
| `foldersReplacements` | Swap one folder icon for another: `{ "components": "react-components" }` |
| `filesAssociations` | Map extensions or filenames to icons (Material-Icons syntax: `*.tss`, `tailwind.css`, `src/index.js`). Empty string removes an association |
| `foldersAssociations` | Map folder names to icons: `{ "store": "resource" }`. Empty string removes |
| `youColors` | Color palette for the **Flow You** theme — see below |

### Flow You

`Flow You` is a customizable icon theme: provide your own 14-color palette and `update-icons.cjs` rebuilds the SVGs by substituting `--<colorName>` placeholders in the template icons.

Add a `youColors` object to your `config.json`. Top-level keys are the dark-mode palette; everything you omit falls back to the default monochromatic slate. The light-mode palette is auto-derived from the dark colors (HSL darken), but you can override individual entries via a nested `light` object.

```jsonc
{
  "youColors": {
    // Dark theme colors
    "white": "#bfbdb6",
    "black": "#0d1017",
    "blue": "#59c2ff",
    "brown": "#e6c08a",
    "gray": "#667381",
    "green": "#aad94c",
    "lime": "#c0e76e",
    "orange": "#ff8f40",
    "pink": "#f6adae",
    "purple": "#d2a6ff",
    "red": "#f07178",
    "sky": "#39bae6",
    "teal": "#95e6cb",
    "yellow": "#ffcb8f",
    // "border":   "#ffffff",   // defaults to `contrast`
    // "contrast": "#ffffff",   // defaults to `white` (dark) / `black` (light)
    "borderOpacity": 0,         // 0 hides the icon outlines

    // Light theme overrides (everything else is auto-derived)
    "light": {
      "borderOpacity": 0.1
    }
  }
}
```

After editing, run `node update-icons.cjs` and restart Zed.

> 💡 See the upstream [sample palettes](https://github.com/thang-nm/Flow-Icons/tree/main/you) (Ayu Dark, Sequoia Moonlight, …) for inspiration — drop their JSON straight into `youColors`.
