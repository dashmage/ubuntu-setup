Notes to document my Ubuntu 22.04 setup process. I'm trying out [Regolith](https://regolith-desktop.com) for a TWM experience with sane defaults.

Note: Following Regolith2, so the configuration is different from Regolith

# Basics
=======

# Basics
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

# Regolith Setup
Refer docs for [basic usage](https://regolith-desktop.com/docs/using-regolith/basics/) and [configuration](https://regolith-desktop.com/docs/using-regolith/configuration/)

### Status bar icons 
```bash
sudo apt install i3xrocks-focused-window-name i3xrocks-rofication i3xrocks-info i3xrocks-app-launcher i3xrocks-memory

# To remove any of these indicators later
# sudo apt remove i3xrocks-info

# To view current battery status on laptop
sudo apt install i3xrocks-battery
```

### Compositor
Refer [this](https://regolith-desktop.com/docs/howtos/customize-compositor/). Make sure to log out and then log back in for the changes to take effect.
```bash
sudo apt install regolith-compositor-picom-glx
```

### Theme
Themes are setup with `Regolith Look`. Gallery [here](https://regolith-linux.org/docs/reference/looks/).

`Win+Alt+l` to change themes.

```bash
sudo apt install regolith-look-dracula

# Check out all themes
# sudo apt search regolith-look-*
```

### Misc
Main config file: ~/.config/regolith2/Xresources
- changed terminal font
```
gnome.terminal.font: RobotoMono Nerd Font 18
```

To refresh, run `regolith-look refresh`

[Add internal padding to gnome terminal](https://trendoceans.com/increase-padding-in-gnome-terminal/)

### NvChad
Check out https://docs.rockylinux.org/books/nvchad/

# Installed Software
- [VSCode](https://code.visualstudio.com/docs/setup/linux#_debian-and-ubuntu-based-distributions)
- [Neovim](https://github.com/neovim/neovim/wiki/Installing-Neovim)
- [fzf](https://github.com/junegunn/fzf)
- [hexchat](https://flathub.org/apps/details/io.github.Hexchat)

# Want to Check Out
- [z - jump around](https://github.com/rupa/z)

[Save git credentials](https://stackoverflow.com/questions/35942754/how-can-i-save-username-and-password-in-git)

### Manage dotfiles
Using [Chezmoi](https://www.chezmoi.io/). Dotfiles are stored [here](https://github.com/dashmage/dotfiles/).

Reference links:
- https://www.chezmoi.io/quick-start/
- https://www.chezmoi.io/user-guide/frequently-asked-questions/usage/
- https://www.chezmoi.io/user-guide/frequently-asked-questions/design/

