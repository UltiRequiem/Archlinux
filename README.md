# Guide to Install Archlinux

TODO

### Get [yay](https://github.com/Jguer/yay):
```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

### Get Wifi Working:
```bash
yay -S rtl8821ce-dkms-git
```
```bash
sudo vim /etc/modprobe.d/blacklist.conf
```
Paste this ```blacklist rtw88_8821ce```
```bash
nmcli device wifi list
```
```bash
nmcli device wifi connect "Your-Wifi" password "Your-Password"
```
Then to turn off the wifi:
```
nmcli radio wifi off
```
To turn on:
```
nmcli radio wifi on
```
### Set Permanent Keyboard Layout:
```bash
sudo localectl set-keymap  "your-layout"
```
In my case:
```bash
sudo localectl set-keymap  la-latin1
```
### Get Audio working:
```bash
sudo pacman -S alsa-utils
```

```bash
amixer set Master 2%+
amixer set Master 2%-
```

### Adjust time to local time:
```bash
timedatectl list-timezones
```
```bash
timedatectl set-timezone America/Lima
```

### Mount other Disks on Startup:
```bash
sudo vim /etc/fstab
```
Something like:
```
/dev/sda1     /home/yourusername/Disk ext4 defaults 0 1
```

Get a fonts with icons like **noto-fonts-emoji-apple**.

### Useful Links
- [Set Keyboard at Startup](https://wiki.archlinux.org/title/Xorg/Keyboard_configuration)
- [i3wm Web Page](https://i3wm.org)
- [Polybar Repository](https://github.com/polybar/polybar-scripts)
- [i3wm User Guide](https://i3wm.org/docs/userguide.html)
- [u3wm Repository](https://github.com/i3/i3)
- [How to set wallpapers on i3wm](https://www.linuxandubuntu.com/home/set-background-wallpapers-on-i3wm)
- [How to use multiple monitors](https://fedoramagazine.org/using-i3-with-multiple-monitors)
- [Change keyboard distribution](https://gist.github.com/jatcwang/ae3b7019f219b8cdc6798329108c9aee)
- [How to install i3wm gaps](https://github.com/Airblader/i3/wiki/installation)
- [How to take Screenshots](https://unix.stackexchange.com/questions/233345/how-can-i-easily-make-screenshots-of-screen-regions-on-arch-linux-with-i3-wm)

### Other Links

- [Emojis on Terminal](https://dev.to/darksmile92/get-emojis-working-on-arch-linux-with-noto-fonts-emoji-2a9)
- [Fstab wiki](https://wiki.archlinux.org/index.php/Fstab)
- [Make partitions mount on startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
- [dhcpcd](https://bbs.archlinux.org/viewtopic.php?id=152991)
- [Dhcpcd startup at boot](https://unix.stackexchange.com/questions/76587/dhcpcd-cant-startup-at-boot)
- [MS Fonts](https://wiki.archlinux.org/index.php/Microsoft_fonts)
- [Cheese not working](https://bbs.archlinux.org/viewtopic.php?id=233715)
