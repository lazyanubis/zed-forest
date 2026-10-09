# Publishing Forest

Forest 0.1.1 is not yet listed in the official Zed extension registry. The repository is prepared as a theme extension; manual desktop verification remains outstanding.

Before submission, review the current [prerequisites](https://zed.dev/docs/extensions/publishing/prerequisites), confirm `forest-theme` is available, and manually test the exact commit to be submitted in Zed. Check installation, theme selection, syntax colors, terminal colors, and removal. Record the tested Zed version and commit.

Follow the official [publishing guide](https://zed.dev/docs/extensions/publishing/publishing-guide):

1. Fork and clone `zed-industries/extensions`.
2. Add `https://github.com/lazyanubis/zed-forest.git` as the submodule `extensions/forest-theme`. Select the tested commit, which must exist on a public branch.
3. Add the matching version to the registry's `extensions.toml`:

   ```toml
   [forest-theme]
   submodule = "extensions/forest-theme"
   version = "0.1.1"
   ```

4. Run `pnpm sort-extensions`, review the changes, then submit one extension per PR.

Registry publication happens after the maintainers accept and merge the submission.

The official [AI policy](https://github.com/zed-industries/extensions/blob/main/AI_POLICY.md) requires human responsibility, prohibits autonomous-agent contributions, and requires the contributor to write the PR explanation and maintainer responses in their own words. No official registry PR has been submitted, and no PR body is supplied here. The human maintainer must complete the review and submission.
