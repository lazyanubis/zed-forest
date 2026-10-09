# Forest

[简体中文](README.zh-CN.md)

A deep forest green theme for [Zed](https://zed.dev), with teal keywords, yellow-green types, and separate colors for constants, numbers, and booleans. The extension provides one dark theme named **Forest**.

**Status:** version 0.1.2, available as a development extension. [Registry PR #7928](https://github.com/zed-industries/extensions/pull/7928) is awaiting review; Forest is not yet published in the official Zed extension registry. See the [changelog](CHANGELOG.md) for the typography and contrast changes.

![Forest 0.1.2 in Zed](preview-native.jpg)

This cropped code-area screenshot shows Forest 0.1.2 in Zed 1.23.2 on macOS, using Lilex at 12 px, weight 400, and approximately 20 px line height. It uses [this TypeScript example](examples/forest.ts), with no local Forest theme override. The [original web preview](preview.jpg) remains available for comparison.

On 2026-10-09, the owner manually installed and selected Forest 0.1.1 in Zed 1.23.2 on macOS. Subsequent computer-assisted UI inspection checked JSON and a standalone TypeScript example, including type, constant, number, and boolean colors, search matches, selections, and terminal ANSI red, green, yellow, blue, magenta, and cyan. The optional Rust semantic settings and uninstallation were not tested. Version 0.1.2 was subsequently installed and visually checked in the same app: normal and documentation comments were upright, and types no longer forced a bold weight. Verification details are recorded in [PUBLISHING.md](PUBLISHING.md).

## Install

Clone this repository and keep the checkout on your machine:

```sh
git clone https://github.com/lazyanubis/zed-forest.git
```

In Zed, open **Extensions**, choose **Install Dev Extension**, and select the `zed-forest` directory containing `extension.toml`. Then run **theme selector: toggle** from the command palette and select **Forest**. This follows Zed's [development extension workflow](https://zed.dev/docs/extensions/developing-extensions).

This is a theme-only extension; it contains no Rust code or WebAssembly module.

## Uninstall

Select another theme first. Open **Extensions**, find **Forest**, and choose **Uninstall**. Any settings you manually added from the optional example remain yours to remove or restore.

## Palette

| Element | Color |
| --- | --- |
| Editor background | `#132623` |
| Panels | `#20403f` |
| Keywords | `#2ea9aa` |
| Types | `#c6c666` |
| Constants | `#d6ad75` |
| Numbers | `#c99577` |
| Booleans | `#b59bd5` |
| Variables | `#639dd0` |
| Parameters | `#a093bd` |
| Properties | `#6baa85` |
| Function definitions | `#d07bd2` |
| Macros | `#4eade5` |

The theme also defines terminal colors, diagnostics, selections, search matches, and collaboration colors. The language grammar and semantic tokens determine which syntax color an identifier receives.

## Typography

Forest does not bundle or install fonts, or change your editor font settings. The [Theme Builder](https://zed.dev/theme-builder) declares Lilex Regular (400) with a 0.75rem font size and 1.25rem line height, equivalent to 12 px and 20 px at the default 16 px root size. To use those settings in Zed, make sure Lilex is available on your machine and merge these optional fields into your existing settings:

```json
{
  "buffer_font_family": "Lilex",
  "buffer_font_size": 12,
  "buffer_font_weight": 400,
  "buffer_line_height": { "custom": 1.666667 }
}
```

Adjust the size for your display and reading comfort. Matching these settings does not guarantee pixel-identical rendering between a browser and the desktop app.

Starting with 0.1.2, code syntax inherits your editor font weight, and regular and documentation comments are upright without a local theme override. Markdown headings and strong emphasis remain bold; existing non-comment italic styles remain in place. See Zed's [font settings](https://zed.dev/docs/appearance) and [theme customization](https://zed.dev/docs/themes).

## Optional semantic highlighting

The extension works without [settings.example.json](settings.example.json). That file combines the optional typography settings above with richer Rust highlighting and inlay hints; it is not installed or applied by the extension.

Review the example and merge only the fields you want into your existing Zed settings. Do not replace your whole settings file or overwrite existing semantic rules blindly.

- Rust uses combined syntax and semantic highlighting, with inlay hints enabled.
- Global semantic rules map declarations, mutable variables, and macro tokens to theme styles. These rules can also affect other languages where semantic highlighting is enabled.
- The global inlay-hint background setting can affect hints in other languages too.

Support depends on your Zed version and language server. The example does not guarantee identical coloring across languages. See Zed's [semantic token documentation](https://zed.dev/docs/semantic-tokens).

## Publishing and license

See [PUBLISHING.md](PUBLISHING.md) for the submitted registry PR, desktop verification scope, and publishing workflow.

[MIT](LICENSE) © 2026 Anubis.
