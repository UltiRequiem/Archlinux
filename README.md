# Archlinux

![GitHub Super-Linter](https://github.com/UltiRequiem/Archlinux/workflows/Lint%20Markdown/badge.svg)
![Repo Size](https://img.shields.io/github/repo-size/ultirequiem/Archlinux?style=flat-square&label=Repo)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitMoji](https://img.shields.io/badge/Gitmoji-%F0%9F%8E%A8%20-FFDD67.svg)](https://gitmoji.dev)

![Screenshot Floating Window](https://i.imgur.com/NKNiLcp.png)

I'm currently using [i3-gaps](https://github.com/Airblader/i3) as my Window Manager.

### Deactivate Grub Menu

In order to achieve the fastest possible boot,
instead of having GRUB wait for a timeout,
it is possible for GRUB to hide the menu.

Add the following line to your `/etc/default/grub`:

```bash
GRUB_FORCE_HIDDEN_MENU="true"
```

[More info](https://wiki.archlinux.org/title/GRUB/Tips_and_tricks)

### Get an AUR Helper

An AUR helpers search for packages published on the AUR and
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

### Get Wifi Working

```bash
yay -S rtl8821ce-dkms-git
```

```bash
sudo vim /etc/modprobe.d/blacklist.conf
```

Paste this `blacklist rtw88_8821ce`

```bash
nmcli device wifi list
```

```bash
nmcli device wifi connect "Your-Wifi" password "Your-Password"
```

Then to turn off the wifi:

```bash
nmcli radio wifi off
```

To turn on:

```bash
nmcli radio wifi on
```

### Set Permanent Keyboard Layout

```bash
sudo localectl set-keymap  "your-layout"
```

In my case:

```bash
sudo localectl set-keymap  la-latin1
```

### Get Audio working

```bash
sudo pacman -S alsa-utils
```

```bash
amixer set Master 2%+
amixer set Master 2%-
```

If this dosen't work try:

```bash
systemctl --user restart pulseaudio
```

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
