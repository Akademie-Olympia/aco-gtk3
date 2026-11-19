# GTK 3 configuration

GTK 3 settings and CSS for desktop applications.

**[Documentation](https://aco-docs.readthedocs.io/en/latest/gtk3/)** ·
[Guide](https://aco-docs.readthedocs.io/en/latest/gtk3/guide/) ·
[Design & dependencies](https://aco-docs.readthedocs.io/en/latest/gtk3/design/) ·
[Installation and updates](https://aco-arch-dotfiles.readthedocs.io/en/latest/arch-package/)

```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- gtk-3.0
```

Package: `aco-arch-dotfiles-gtk-3.0`. This standalone repository holds the development sources and the package recipe in
`packaging/arch/PKGBUILD`. The documentation of this component lives in the shared
[aco-docs](https://github.com/Akademie-Olympia/aco-docs) repository (one Read the Docs project for all small components).
Push to `main`; after a successful registry build update with `sudo pacman -Syu`. Details and local builds: [PACKAGING.md](PACKAGING.md).

### Customisation

`settings.ini` holds the GTK 3 settings; `gtk.css` adds the style rules. Restart affected GTK 3 applications after changes. GTK 4 uses a separate configuration.

Your own changes in the activated user copy survive synchronisation; new differing defaults appear as `.pacnew`.
See [update and recovery](https://aco-arch-dotfiles.readthedocs.io/en/latest/verification/).

[![Package safety](https://github.com/Akademie-Olympia/aco-gtk3/actions/workflows/package.yml/badge.svg)](https://github.com/Akademie-Olympia/aco-gtk3/actions/workflows/package.yml)

[MIT licence](LICENSE).
