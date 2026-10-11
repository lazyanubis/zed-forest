# Publishing Forest

Forest has been submitted in [registry PR #7928](https://github.com/zed-industries/extensions/pull/7928) and is awaiting review. It is not yet listed in the official Zed extension registry.

Version 0.1.3 fixes text selections being difficult to see in source editors and rendered Markdown previews. The desktop checks described below are complete; the registry entry must reference a public commit containing the verified theme file and manifest version 0.1.3. The optional Lilex settings are personal editor settings; the extension neither installs the font nor applies those settings.

## Desktop verification

### 0.1.3 — verified on 2026-10-11

The theme changes `players[0].selection` from `#17362e` to `#2c5a48` and adds `element.selection_background: "#2c5a48"`. Syntax colors and all unrelated theme properties are unchanged. The source-editor selection-to-background contrast increases from 1.206:1 to 2.004:1; against the active-line background it increases from 1.075:1 to 1.786:1. This deliberately prioritizes seeing the selection over retaining 4.5:1 for every selected syntax color.

The preview-specific field is necessary because Zed 1.23.2 [reads it for rendered Markdown selections](https://github.com/zed-industries/zed/blob/v1.23.2/crates/markdown/src/markdown.rs#L243). When it is absent, Zed's [fallback reduces an opaque local selection to 25% opacity](https://github.com/zed-industries/zed/blob/v1.23.2/crates/theme/src/fallback_themes.rs#L47). The [theme settings parser explicitly supports `element.selection_background`](https://github.com/zed-industries/zed/blob/v1.23.2/crates/settings_content/src/theme.rs#L642), even though the published theme schema does not yet list it.

On 2026-10-11, the installed development extension was rebuilt in Zed 1.23.2 on macOS using the theme from commit [`ce4a4a0`](https://github.com/lazyanubis/zed-forest/commit/ce4a4a0). Computer-assisted UI inspection checked Chinese paragraphs in `README.zh-CN.md`: selections were distinguishable in the source editor, and a continuous selection spanning multiple rendered lines and bold **Forest** was clear in the Markdown preview. The [preview screenshot](preview-selection.png) records the latter check.

With focus moved to the search field in the same window and the query cleared, the source selection became dimmer but remained distinguishable. The existing editor font was Lilex at 16 px; there were no `theme_overrides`, and the check did not change font settings or syntax colors. Read-only views, grayscale display modes, and multi-user collaboration were not tested.

The verified `themes/forest.json` SHA-256 is `36492e4d93ef52939e4530bf9204dce57846a7e6f930ad5876459e6a98efea27`. JSON parsing and the two selection fields have also been checked. An earlier source-editor-only candidate improved source selections but left Markdown preview selections dark; the verified file includes the explicit preview field.

### Previous desktop checks

On 2026-10-09, the owner manually installed and selected Forest 0.1.1 in Zed 1.23.2 on macOS. Computer-assisted UI inspection then checked JSON and a standalone TypeScript example: type, constant, number, and boolean colors; search matches; selections; and terminal ANSI red, green, yellow, blue, magenta, and cyan.

The previously tested 0.1.1 theme commit was [`773a13f3f9951858449790bb7b45576fa6b09f59`](https://github.com/lazyanubis/zed-forest/commit/773a13f3f9951858449790bb7b45576fa6b09f59). The optional Rust semantic settings and uninstallation were not tested. The README now displays a cropped 0.1.2 native code-area screenshot; the 0.1.0 web preview remains linked for comparison.

On the same date, Forest 0.1.2 was installed through Install Dev Extension and rebuilt in Zed 1.23.2. Computer-assisted UI inspection, requested by the owner, confirmed normal and documentation comments are upright and types are no longer bold with the local `theme_overrides` removed. The editor used Lilex, 12 px, base weight 400, and a custom line height of approximately 1.666667. The standalone sample is in `examples/forest.ts`.

The verified 0.1.2 `themes/forest.json` SHA-256 was `05062e383c941a12aed35169c6b85293fdc57bef73ae00736bd53d8eea9c66de`. This record applies to that theme file with manifest version 0.1.2.

## Registry workflow

For future submissions, review the current [prerequisites](https://zed.dev/docs/extensions/publishing/prerequisites) and test the exact theme commit. Follow the official [publishing guide](https://zed.dev/docs/extensions/publishing/publishing-guide):

1. Fork and clone `zed-industries/extensions`.
2. Add `https://github.com/lazyanubis/zed-forest.git` as the submodule `extensions/forest-theme`. Select the tested commit, which must exist on a public branch.
3. Add the matching version to the registry's `extensions.toml`:

   ```toml
   [forest-theme]
   submodule = "extensions/forest-theme"
   version = "0.1.3"
   ```

4. Run `pnpm sort-extensions`, review the changes, then submit one extension per PR.

Registry publication happens after the maintainers accept and merge the submission.

The official [AI policy](https://github.com/zed-industries/extensions/blob/main/AI_POLICY.md) requires human responsibility, prohibits autonomous-agent contributions, and requires the contributor to write the PR explanation and maintainer responses in their own words. The maintainer supplied the submitted PR description; future responses remain the maintainer's responsibility.
