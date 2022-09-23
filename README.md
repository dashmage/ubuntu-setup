Notes to document my Ubuntu 22.04 setup process. I'm trying out [Regolith](https://regolith-desktop.com) for a TWM experience with sane defaults.

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
Make sure to log out for the changes to take effect.
```bash
sudo apt install regolith-compositor-picom-glx
```

### Theme
Themes are setup with `Regolith Look`. Gallery [here](https://regolith-linux.org/docs/reference/looks/),

```bash
sudo apt install regolith-look-dracula

# Check out all themes
# sudo apt search regolith-look-*
```

### Misc
Main config file: ~/.config/regolith/Xresources
- changed terminal font
```
gnome.terminal.font: RobotoMono Nerd Font 18
```