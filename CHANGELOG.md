# Changelog

## 0.1.3

- Make source-editor text selections visible against the dark editor and active-line backgrounds by changing `players[0].selection` from `#17362e` to `#2c5a48`.
- Set `element.selection_background` explicitly to `#2c5a48` for selections in rendered Markdown previews. Without this field, Zed 1.23.2 reduces the opaque local selection color to 25% opacity, making the preview selection difficult to see.
- Preserve syntax colors and all unrelated theme properties. The brighter selections improve visibility while reducing selected-code contrast; desktop verification of the final two-field fix is pending.

## 0.1.2

- Render regular and documentation comments upright, fixing the difference between the web preview and the installed theme without requiring a local theme override.
- Let code syntax inherit the editor's font weight instead of forcing regular text to 400 and types and special function definitions to 700. Keep bold Markdown headings and strong emphasis.
- Document optional Lilex typography settings matching the web preview: 12 px, weight 400, and a custom line-height multiplier of 1.666667. Fonts and editor settings are not installed by the extension.

## 0.1.1

- Reduce search-match background opacity from `#58633880` to `#58633833` to preserve syntax contrast.
- Use blue-gray `#23303e` for read-reference highlights, distinct from the green selection `#17362e`.
- Brighten terminal ANSI red from `#af6e86` to `#bd8395` for clearer red output.

The README image remains a 0.1.0 web preview. The desktop checks completed on 2026-10-09 and the untested Rust settings and uninstallation are recorded in [PUBLISHING.md](PUBLISHING.md).

## 0.1.0

- Initial Forest dark theme, development extension manifest, and optional semantic-highlighting settings example.
