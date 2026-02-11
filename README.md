# KGSM - Arch User Repository Package

This repository contains the PKGBUILD and metadata files for distributing [KGSM (Krystal Game Server Manager)](https://github.com/KrystalGameServerManager/kgsm) through the Arch User Repository (AUR).

## About KGSM

KGSM is a lightweight, powerful tool for managing game servers on Linux with minimal hassle. It simplifies setting up and managing game servers through an intuitive interface, supporting both native Linux and Docker container deployments.

**For full documentation, visit the main project:** [github.com/KrystalGameServerManager/kgsm](https://github.com/KrystalGameServerManager/kgsm)

## Installation

### Using an AUR Helper

```sh
# Using yay
yay -S kgsm

# Using paru
paru -S kgsm
```

### Manual Installation

```sh
git clone https://aur.archlinux.org/kgsm.git
cd kgsm
makepkg -si
```

## What's Included

This PKGBUILD installs:

- **Main script**: `/usr/bin/kgsm` (symlink to `/usr/share/kgsm/kgsm.sh`)
- **Core modules**: Essential libraries and bootstrap system
- **Commands**: User-facing command handlers and business logic
- **Templates**: Blueprint, override, and service file templates
- **Blueprints**: Default game server configurations
- **Overrides**: Game-specific installation/update logic
- **Migrations**: Configuration schema upgrade scripts
- **Documentation**: Full docs in `/usr/share/doc/kgsm/`

### Dependencies

**Required:**
- `bash>=5.0`
- `coreutils`, `grep`, `sed`, `curl`, `jq`, `findutils`

**Optional:**
- `steamcmd` - Steam-based game server support
- `lib32-gcc-libs` - Required by some Steam servers
- `ufw` - Automatic firewall rule management
- `docker` + `docker-compose` - Container-based game servers

## User Data Location

KGSM follows XDG Base Directory conventions. Your data is stored in:

- **Config**: `~/.config/kgsm/config.ini`
- **Instances**: `~/.local/share/kgsm/instances/` (deployed servers)
- **Blueprints**: `~/.local/share/kgsm/blueprints/` (custom configurations)
- **Logs**: `~/.local/share/kgsm/logs/`

> **Note:** The system-wide installation at `/usr/share/kgsm/` contains read-only defaults. User customizations should go in `~/.local/share/kgsm/`.

## Package Maintenance

This AUR package tracks official KGSM releases from the main repository. Version numbers follow the upstream project.

### Reporting Issues

- **AUR package issues** (PKGBUILD problems, installation failures): [Open an issue here](https://github.com/KrystalGameServerManager/kgsm-aur/issues)
- **KGSM functionality issues** (bugs, feature requests): [Report to the main project](https://github.com/KrystalGameServerManager/kgsm/issues)

### Contributing

Contributions to improve the AUR packaging are welcome:

1. **PKGBUILD improvements** - Better dependency detection, install path fixes
2. **Post-install messages** - Helpful setup guidance
3. **Compatibility fixes** - Ensuring smooth installation across Arch variants

Please test changes thoroughly before submitting a pull request.

## Quick Start After Installation

```sh
# View available commands
kgsm --help

# List game server blueprints
kgsm blueprints list

# Install a game server (e.g., Minecraft)
kgsm install minecraft --name survival

# Start the server
kgsm start survival
```

## Links

- **AUR Page**: [aur.archlinux.org/packages/kgsm](https://aur.archlinux.org/packages/kgsm)
- **Main Project**: [github.com/KrystalGameServerManager/kgsm](https://github.com/KrystalGameServerManager/kgsm)
- **Documentation**: [github.com/KrystalGameServerManager/kgsm/tree/main/docs](https://github.com/KrystalGameServerManager/kgsm/tree/main/docs)

## License

[GNU General Public License v3.0](LICENSE)

---

**Maintainer**: Cristian Moraru <info@thekrystalship.com>
