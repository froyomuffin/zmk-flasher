# zmk-flasher
A small service to automatically copy `.UF2`s to a ZMK-based keyboard when in bootloader.

## How it works
The tool runs a light bash script as a service and monitors for a ZMK keyboard in bootloader mode. When a keyboard is detected, it'll copy a `zmk.uf2` firmware file from a specified source to the keyboard. It'll also automatically rename the spent firmware file to `zmk.uf2-<flash-time>`

This tool expects your system is configured to automount new volumes to a consistent location.

## Installation
Note that this tool was written for myself. You'll likely need to know how to script to be able to use it.

1. Copy `zmk-flasher` to `/usr/bin`
2. Change `KEYBOARD_MNT` to the mountpoint for your keyboard in bootloader mode
3. [Optional] Change any of `CONFIG_DIR` or `CONFIG_FILE` if you want
4. Copy `zmk-flasher.service` to `~/.local/share/systemd/user/`
5. Start it via `systemctl --user start zmk-flasher`
6. [Optional] Enable auto start on log-in via `systemctl --user enable zmk-flasher`

## Usage
1. Extract your newly compiled firmware and move the `.uf2` file to `~/zmk-dropzone/zmk.uf2`
2. Plug in your keyboard
3. Put it in bootloader mode
4. That's pretty much it


## TODOs
- [ ] Extract configuration to config file
- [ ] Multi-keyboard support?
