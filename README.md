<div align="center">

<img src="snap/gui/ventoy.png" alt="Ventoy logo" width="128" />

# Ventoy

**Create and update multiboot USB drives**

[![Ventoy](https://snapcraft.io/ventoy/badge.svg)](https://snapcraft.io/ventoy)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Ventoy](https://github.com/ventoy/Ventoy), a tool for booting multiple operating-system images from one USB drive.

</div>

---

## Getting Started

<a href="https://snapcraft.io/ventoy"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install ventoy
sudo snap connect ventoy:block-devices
sudo snap connect ventoy:mount-observe
sudo ventoy.web
```

Open **http://127.0.0.1:24680**. Press **Ctrl+C** in the terminal to stop the server.

**Installing Ventoy erases the selected drive.** Unmount its filesystems and disable any swap on it first. Keep it unmounted during the operation. After installation, copy your ISO files onto the drive normally.

For the command-line installer, run `ventoy --help` and use `sudo ventoy` with the required arguments.

## Configure

| Option | Input | Default |
| --- | --- | --- |
| `ventoy.web -p` | Port from `1` to `65535` | `24680` |

There are no `snap set` options. The Web UI listens only on localhost and runs on demand. Logs and settings are in `/var/snap/ventoy/current/work/`.

## Limitations

- Requires snapd 2.71 or newer. Raw disk access needs Snap Store approval and the interface connections above.
- Includes the CLI and official Web UI; the native GTK/Qt application and Plugson are not included.
- Mounted drives, active swap, and targets containing Btrfs, bcachefs or ZFS are refused.
- The Web UI trusts local users. Close it after use and avoid running other disk tools at the same time.

## Build

```bash
git clone https://github.com/sidalit/ventoy-snap.git
cd ventoy-snap
sudo snap install snapcraft --classic
snapcraft pack
```

The Linux installer is built from source with Ventoy's released boot payload. Release builds use the matching payload; HEAD builds use the latest released payload, retaining its bootloader version.

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/ventoy-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/ventoy/Ventoy/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/ventoy-snap/blob/main/LICENSE).
