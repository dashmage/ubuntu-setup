Notes to document my Ubuntu 22.04 setup process. 

Using [Regolith](https://regolith-desktop.com) for a TWM experience with sane defaults.
Dotfiles managed using [Chezmoi](https://www.chezmoi.io/) and stored [here](https://github.com/dashmage/dotfiles).

# Essentials
## Enable tap-to-click
```bash
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true
```

## Smart Caps Lock
Refer: https://gist.github.com/tanyuan/55bca522bf50363ae4573d4bdcf06e2e

As mentioned in the link, 
- Send Escape if you tap Caps Lock alone.
- Send Control if you press Caps Lock with another key.

```bash
sudo apt install xcape

# make CapsLock behave like Ctrl:
setxkbmap -option ctrl:nocaps

# make short-pressed Ctrl behave like Escape:
xcape -e 'Control_L=Escape'
```

Append code to `~/.xprofile` to run the commands when X starts.

## Custom Keybindings
This can be mapped in Settings -> Custom Keyboard Shortcuts

- Super + S (screenshot): `gnome-screenshot -i`
- Alt + Q (BT mic + open chrome): `sh -c "pactl set-card-profile bluez_card.74_45_CE_D0_C5_3B handsfree_head_unit; google-chrome"`

# Regolith Setup
Refer docs for [basic usage](https://regolith-desktop.com/docs/using-regolith/basics/) and [configuration](https://regolith-desktop.com/docs/using-regolith/configuration/)

## Status bar icons 
```bash
sudo apt install i3xrocks-focused-window-name i3xrocks-rofication i3xrocks-info i3xrocks-app-launcher i3xrocks-memory

# To remove any of these indicators later
# sudo apt remove i3xrocks-info

# To view current battery status on laptop
sudo apt install i3xrocks-battery
```

## Compositor
Refer [this](https://regolith-desktop.com/docs/howtos/customize-compositor/). Make sure to log out and then log back in for the changes to take effect.
```bash
sudo apt install regolith-compositor-picom-glx
```

## Theme
Themes are setup with `Regolith Look`. Gallery [here](https://regolith-linux.org/docs/reference/looks/).

`Win+Alt+l` to change themes.

```bash
sudo apt install regolith-look-dracula

# Check out all themes
# sudo apt search regolith-look-*
```

## Other config
Main config file: ~/.config/regolith2/Xresources

i3 config files present here
```
/usr/share/regolith/i3/config.d
~/.config/regolith2/i3/config.d
```

Remove files from the `/usr/share`  in order to override them from `~/.config`.

- terminal font
```
gnome.terminal.font: RobotoMono Nerd Font 18
```

To refresh, run `regolith-look refresh`

[Add internal padding to gnome terminal](https://trendoceans.com/increase-padding-in-gnome-terminal/)

# Utilities and Tools
- [VSCode](https://code.visualstudio.com/docs/setup/linux#_debian-and-ubuntu-based-distributions)
- [Neovim](https://github.com/neovim/neovim/wiki/Installing-Neovim)
- [fzf](https://github.com/junegunn/fzf)
- [kitty](https://sw.kovidgoyal.net/kitty/)
- [z - jump around](https://github.com/rupa/z)
- sshebang
- tmux
- Obsidian snap
- CopyQ
- Mattermost

## tmux

Sane defaults on functionality and looks: https://github.com/gpakosz/.tmux

To automatically start tmux for an ssh session, add this to your local `~/.ssh/config`

```ssh
Host myhost
  Hostname host
  User user
  RequestTTY yes 
  RemoteCommand tmux new -A -s ssh_tmux
```

# Misc
[Save git credentials](https://stackoverflow.com/questions/35942754/how-can-i-save-username-and-password-in-git)

# TODO

- Manage SSH keys and GPG keys.
- Ansible to automate (atleast part of) the setup.
- LUKS encryption
  -   https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019
  -   https://gist.github.com/luispabon/db2c9e5f6cc73bb37812a19a40e137bc
  -   https://gist.github.com/superjamie/d56d8bc3c9261ad603194726e3fef50f

