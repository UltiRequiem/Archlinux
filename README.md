# Archlinux

![GitHub Super-Linter](https://github.com/UltiRequiem/Archlinux/workflows/Lint%20Markdown/badge.svg)
![Repo Size](https://img.shields.io/github/repo-size/ultirequiem/Archlinux?style=flat-square&label=Repo)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitMoji](https://img.shields.io/badge/Gitmoji-%F0%9F%8E%A8%20-FFDD67.svg)](https://gitmoji.dev)

![Screenshot Floating Window](https://i.imgur.com/NKNiLcp.png)

> Window Manager: [i3-gaps](https://github.com/Airblader/i3) -
> Dotfiles: [UltiRequiem/dotfiles](https://github.com/UltiRequiem/dotfiles) -
> Status Bar: [bumblebee-status](https://github.com/tobi-wan-kenobi/bumblebee-status)

## Why this repo?

todo

### Deactivate Grub Menu

In order to achieve the fastest possible boot,
instead of having GRUB wait for a timeout,
it is possible for GRUB to hide the menu.

Add the following line to your `/etc/default/grub`:

```bash
GRUB_FORCE_HIDDEN_MENU="true"
```

> [More info](https://wiki.archlinux.org/title/GRUB/Tips_and_tricks)

### Get an AUR Helper

An AUR helper search for packages published on the AUR and
make the package installation process much easier.

There a lot of there but, my personal choice is [yay](https://github.com/Jguer/yay).

```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

[Paru](https://github.com/Morganamilo/paru) is also a popular choice:

```bash
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

> [More Info](https://wiki.archlinux.org/title/AUR_helpers)

### Get Wifi Working

To list all the available Networks:

```bash
nmcli device wifi list
```

To connect:

```bash
nmcli device wifi connect "Your-Wifi" password "Your-Password"
```

To turn on:

```bash
nmcli radio wifi on
```

To turn off:

```bash
nmcli radio wifi off
```

If `nmcli` cannot detect Wi-Fi networks, it is likely that you need a driver.

In my case my computer does not detect the wifi until I did the following:

```bash
yay -S rtl8821ce-dkms-git
```

And then paste `blacklist rtw88_8821ce` in `/etc/modprobe.d/blacklist.conf`

> [More Info](https://wiki.archlinux.org/title/Network_configuration/Wireless)

### Set Permanent Keyboard Layout

```bash
sudo localectl set-keymap  "your-layout"
```

Example:

```bash
sudo localectl set-keymap  la-latin1
```

> [More Info](https://wiki.archlinux.org/title/locale)

### Get Audio working

Install `alsa-utils`:

```bash
sudo pacman -S alsa-utils
```

To control the audio:

```bash
amixer set Master 2%+
amixer set Master 2%-
```

You can map this commands to a key. Example using i3: [dotfiles](https://github.com/UltiRequiem/dotfiles/blob/5ca2ac37a2aa087b57598b8a4a15574f0762f446/config/i3/config#L120)

If this dosen't work try:

```bash
systemctl --user restart pulseaudio
```

> [More Info](https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture)

### Adjust time to local time

```bash
timedatectl list-timezones
```

Example:

```bash
timedatectl set-timezone America/Lima
```

### Mount other Disks on Startup

To mount other disk on startup you need to edit you `/etc/fstab` file.

```bash
sudo vim /etc/fstab
```

Example:

```fstab
/dev/sda1     /home/zero/disk ext4 defaults 0 1
```

Get a fonts with icons like **noto-fonts-emoji-apple**.

```bash
yay -S noto-fonts-emo-apple
```
