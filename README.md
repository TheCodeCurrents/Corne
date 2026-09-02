# Corne Choc Pro BT — ZMK Config

Custom ZMK firmware configuration for the Corne Choc Pro BT (6-column) split
keyboard with a rotary encoder and RGB underglow.

## Repository structure

```
build.yaml                          # GitHub Actions build matrix
config/
  corne_choc_pro.conf               # Keyboard config (BT name, sleep, RGB)
  corne_choc_pro.keymap             # Keymap (QWERTY + lower/raise/extra layers)
  corne_choc_pro.json               # Keymap editor layout metadata
  west.yml                          # ZMK firmware manifest (v0.3)
boards/arm/corne_choc_pro/          # Board definition (DTS, Kconfig, defconfig)
zephyr/module.yml                   # Zephyr module entry point
.github/workflows/build.yml         # CI workflow (reuses ZMK's build-user-config)
```

## Build targets

| Board | Shield | Snippet | Artifact |
| --- | --- | --- | --- |
| `corne_choc_pro_left` | — | `studio-rpc-usb-uart` | `corne_choc_pro_bt_left` |
| `corne_choc_pro_right` | — | `studio-rpc-usb-uart` | `corne_choc_pro_bt_right` |
| `corne_choc_pro_left` | `settings_reset` | `studio-rpc-usb-uart` | — |
| `corne_choc_pro_right` | `settings_reset` | `studio-rpc-usb-uart` | — |

The left half builds with ZMK Studio enabled (`-DCONFIG_ZMK_STUDIO=y`).
Settings-reset firmware is included for both halves.

## Features

- Bluetooth name: **Corne Choc BT**
- RGB underglow with auto-off on idle
- Deep sleep after 1 hour of inactivity
- ZMK Studio support on the left half
- EC11 encoder support
- Keymap: QWERTY, Number, Symbol, and 6 extra layers