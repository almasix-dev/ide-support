# Almasix IDE support

Editor packages for [Almasix](https://github.com/almasix-dev/almasix):

| Path | Package |
| --- | --- |
| [`vscode/`](vscode/) | VS Code / Cursor / VSCodium extension (`almasix-lsp`) |
| [`jetbrains/`](jetbrains/) | PyCharm / IntelliJ **Almasix Idea** (native index) |
| [`prism/`](prism/) | Shared TextMate grammar, language config, snippets |

- **VS Code family:** language intelligence from **`almasix-lsp`**
  (`pip install 'almasix[lsp]'`).
- **JetBrains 0.2.0+:** native completions via `smith ide:index --json`
  (no LSP4IJ).

## Install

### VS Code / Cursor / VSCodium

1. Install **Almasix** from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=almasix.almasix)
   (publisher `almasix`), **or** download a `.vsix` from
   [Releases](https://github.com/almasix-dev/ide-support/releases) and **Install from VSIX…**.
2. In an Almasix app: `pip install 'almasix[lsp]'` and optionally `smith ide:install`.

### JetBrains (PyCharm / IntelliJ)

1. Install **Almasix** from the JetBrains Marketplace (plugin id `com.almasix.ide`),
   **or** **Settings → Plugins → ⚙ → Install Plugin from Disk…** with a zip from
   [Releases](https://github.com/almasix-dev/ide-support/releases) (**0.2.0+**).
2. Restart; open an app with Almasix on the project interpreter
   (`smith ide:index --json` must work). Use **Almasix → Rebuild Index** to refresh.

## Develop

```bash
# VS Code
cd vscode && npm install && npm run package

# JetBrains (JDK 17+)
cd jetbrains && ./gradlew test buildPlugin
```

Prism assets live under `prism/`. The VS Code package syncs them via
`npm run sync-prism` before packaging.

## Release / publish

Cutting a release: create a GitHub Release on a `vX.Y.Z` tag. The
[publish workflow](.github/workflows/publish.yml) builds both artifacts, attaches
them to the Release, then publishes to:

- **Visual Studio Marketplace** (`vsce publish`)
- **JetBrains Marketplace** (`./gradlew publishPlugin`)

### Secrets (org / repo Settings → Secrets)

| Secret | Used for |
| --- | --- |
| `VSCE_PAT` | Azure DevOps PAT with **Marketplace (Publish)** for publisher `almasix` |
| `JETBRAINS_PUBLISH_TOKEN` | JetBrains Marketplace token for plugin `com.almasix.ide` |

Publisher accounts must already exist and match the package ids above. Do not
commit tokens.
