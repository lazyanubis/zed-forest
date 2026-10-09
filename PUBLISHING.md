# Publishing Forest

Forest has been submitted in [registry PR #7928](https://github.com/zed-industries/extensions/pull/7928) and is awaiting review. It is not yet listed in the official Zed extension registry.

Version 0.1.2 fixes comment italics and removes forced weights from code syntax. Its desktop typography verification is complete; the registry entry must reference the tested 0.1.2 theme content. The optional Lilex settings are personal editor settings; the extension neither installs the font nor applies those settings.

## Desktop verification

On 2026-10-09, the owner manually installed and selected Forest 0.1.1 in Zed 1.23.2 on macOS. Computer-assisted UI inspection then checked JSON and a standalone TypeScript example: type, constant, number, and boolean colors; search matches; selections; and terminal ANSI red, green, yellow, blue, magenta, and cyan.

The previously tested 0.1.1 theme commit was [`773a13f3f9951858449790bb7b45576fa6b09f59`](https://github.com/lazyanubis/zed-forest/commit/773a13f3f9951858449790bb7b45576fa6b09f59). The optional Rust semantic settings and uninstallation were not tested. The README now displays a cropped 0.1.2 native code-area screenshot; the 0.1.0 web preview remains linked for comparison.

On the same date, Forest 0.1.2 was installed through Install Dev Extension and rebuilt in Zed 1.23.2. Computer-assisted UI inspection, requested by the owner, confirmed normal and documentation comments are upright and types are no longer bold with the local `theme_overrides` removed. The editor used Lilex, 12 px, base weight 400, and a custom line height of approximately 1.666667. The standalone sample is in `examples/forest.ts`.

The verified `themes/forest.json` SHA-256 is `05062e383c941a12aed35169c6b85293fdc57bef73ae00736bd53d8eea9c66de`. The registry PR must pin a public commit with this theme file and manifest version 0.1.2.

## Registry workflow

For future submissions, review the current [prerequisites](https://zed.dev/docs/extensions/publishing/prerequisites) and test the exact theme commit. Follow the official [publishing guide](https://zed.dev/docs/extensions/publishing/publishing-guide):

1. Fork and clone `zed-industries/extensions`.
2. Add `https://github.com/lazyanubis/zed-forest.git` as the submodule `extensions/forest-theme`. Select the tested commit, which must exist on a public branch.
3. Add the matching version to the registry's `extensions.toml`:

   ```toml
   [forest-theme]
   submodule = "extensions/forest-theme"
   version = "0.1.2"
   ```

4. Run `pnpm sort-extensions`, review the changes, then submit one extension per PR.

Registry publication happens after the maintainers accept and merge the submission.

The official [AI policy](https://github.com/zed-industries/extensions/blob/main/AI_POLICY.md) requires human responsibility, prohibits autonomous-agent contributions, and requires the contributor to write the PR explanation and maintainer responses in their own words. The maintainer supplied the submitted PR description; future responses remain the maintainer's responsibility.
