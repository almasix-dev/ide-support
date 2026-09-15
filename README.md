# Almasix IDE support (moved)

This monorepo has been **split**. Develop and release from the dedicated repos:

| Editor | Repository | Marketplace |
| --- | --- | --- |
| **VS Code / Cursor / VSCodium** | [`almasix-dev/almasix-vscode`](https://github.com/almasix-dev/almasix-vscode) | [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=almasix.almasix) |
| **PyCharm / WebStorm (Almasix Idea)** | [`almasix-dev/almasix-idea`](https://github.com/almasix-dev/almasix-idea) | JetBrains Marketplace (`com.almasix.ide`) |

Prism TextMate assets ship inside [`almasix-vscode`](https://github.com/almasix-dev/almasix-vscode/tree/main/prism)
(`prism/`). JetBrains uses a native Prism language implementation in
[`almasix-idea`](https://github.com/almasix-dev/almasix-idea).

## Why

The VS Code extension and JetBrains plugin share the same *index contract*
(`smith ide:index --json`) but have independent packaging, CI, and release
cadences. Keeping them in one repo coupled Marketplace publishes and slowed
each side down.

## History

Git history for each package was preserved with `git filter-repo` when the
split landed. Older monorepo commits remain here for archaeology; **do not
cut new releases from this repository**.

Framework docs: [Editor setup](https://almasix-dev.github.io/almasix/editor-setup/).
