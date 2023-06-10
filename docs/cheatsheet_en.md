# Help documents

* [hyprland official wiki](https://wiki.hyprland.org/)
* [original author repository](https://github.com/JaKooLit/Hyprland-v2.1)
* [more gtk theme](https://www.xfce-look.org/browse/)
* [more software for wayland](https://arewewaylandyet.com/)

## shortcut keys

* Super + shift + / : Pop-up window, You can quickly view the shortcut keys and other settings files after you choose.
* Super + enter : Foot terminal
* Super + d : Application selection
* Super + t : File manager
* Prtsc : Area screenshot, click the download icon to save on `~/Pictures/Screenshots/`
* Super + Prtsc : Window screenshot
* Super + alt + Prtsc : Full screenshot
* Super + v : Clipboard manager
* Super + shift + q : Kill the current process
* Super + b : Close the status bar
* Super + space : Tile/floating mode switching
* Super + shift + space : Window re-tuning
* Super + F : Full screen
* Super + L : Lock screen
* Super + N : Previous window
* Super + shift + N : The next window
------
* Super + h/j/k/l : Move the focus in the window
* Super + shift + h/j/k/l : Move the window position
* Super + ctrl + h/j/k/l : Resize the window
------
* Super + 1/2/3 : Switch workspaces
* Super + shift + 1/2/3 : Send to the workspace
* Super + ctrl + 1/2/3 : Send to the workspace and focus
------
* Super + shift + u : Send to special workspace
* Super + u : Open a special workspace

## Common Questions

* `hyprland` setting directory: `~/.config/hypr/
* Check software type(`wayland` or `x11`): `hyprctl clients`

### No sound.

```sh
# Check the sound card information
aplay -l
# Set the default sound card
# User level
vim ~/.asoundrc
===
defaults.pcm.card 1
defaults.pcm.device 0
defaults.ctl.card 1
===
# The `pcm` option determines the device used to play audio, while the `ctl` option determines which sound card can be controlled by the tool.

# System level
vim /etc/asound.conf

# By default, ALSA mutes all channels, all of which need to be manually unmuted.
alsamixer
# It shows that `mm` is muted. After selection, use the key `m` to cancel.
# or seting by amixer
amixer set Master unmute

# restar may needed
```

### Chrome does not support Chinese input.

`chrome://flags`

`Preferred Ozone platform`: setting `Wayland` and reopen

*The misalignment of the prompt box has not been resolved for the time being.*

### firefox

Add environment variables

```sh
sudo vim /etc/environment
===
MOZ_ENABLE_WAYLAND=1
===
```

## Common software

### Chinese input method

* install fcitx5-rime

```sh
yay -S fcitx5 fcitx5-gtk fcitx5-qt fcitx5-rime  fcitx5-configtool 
```

Deployment directory `~/.local/share/fcitx5/rime`

* (Optional)[Theme](https://github.com/hosxy/Fcitx5-Material-Color)

`yay -S fcitx5-material-color`

### Key mapping

`yay -S keyd-git`

example: `capslock+h/j/k/l` mapping as arrow key 

```sh
# add Startup
sudo systemctl enable keyd

# configuration
sudo vim /etc/keyd/default.conf

===
[ids]

*

[main]
capslock = overload(capslock_layer, esc)

[capslock_layer]
esc = capslock

h = left
j = down
k = up
l = right

u = pageup
p = pagedown
i = home
o = end

m = backspace
===

# start
sudo systemctl start keyd
```