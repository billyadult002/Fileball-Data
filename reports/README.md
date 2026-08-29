# Production report archive

Production acceptance, audit, and release-evidence reports are committed to
this directory as the repository's canonical report archive.

For every future report:

1. Write the final JSON or Markdown artifact under `reports/`; temporary
   workspace paths are not final evidence locations.
2. Include the validation time, production entry point, tested scope, result,
   and any remaining upstream-only failures.
3. Run the report's relevant validation/tests before staging it.
4. Stage the specific `reports/...` files, commit them with the implementation
   or evidence commit, and push the verified commit to `main`.
5. Confirm the exact report paths with `git ls-tree -r origin/main reports`.

The current archived reports include:

- `addon-vod-capability-audit.json`
- `playback-source-completeness-audit.json`
- `stream-title-language-audit.json`
