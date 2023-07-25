# Arch Linux PKGBUILD for mw2fcitx

mw2fcitx is a Python library, which can build fcitx5 libraries from MediaWiki sites.

This PKGBUILD helps you build mw2fcitx as a Arch Linux package. Now this is essential since Python 3.11, because `pip` does not allow installing packages directly any more.

## Usage

### 1. Install dependencies

```bash
# Build tools
sudo pacman -S python-build python-installer python-hatchling python-wheel

# mw2fcitx dependencies
sudo pacman -S opencc pypinyin
```

### 2. Generate package

```bash
makepkg -f
```

### 3. Install package

```bash
sudo pacman -U python-mw2fcitx-3.10-1-any.pkg.tar.zst
```

## Why essential?

If you try to install packages via `pip` on Arch Linux, you will see this error message:

```
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try 'pacman -S
    python-xyz', where xyz is the package you are trying to
    install.
    
    If you wish to install a non-Arch-packaged Python package,
    create a virtual environment using 'python -m venv path/to/venv'.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip.
    
    If you wish to install a non-Arch packaged Python application,
    it may be easiest to use 'pipx install xyz', which will manage a
    virtual environment for you. Make sure you have python-pipx
    installed via pacman.

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
```

Though passing `--break-system-packages` works, it is not recommended. Many Python modules are now Arch Linux packages so that they should be installed by `pacman` rather than `pip`.

As a result, maintaining our Arch Linux package of mw2fcitx becomes essential.

## License

MIT License