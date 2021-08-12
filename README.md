# Guide to Install Archlinux

Use [Archinstall](https://github.com/archlinux/archinstall),
it makes all the procces very easy.

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

If this dosen't work try:
```bash
systemctl --user restart pulseaudio
```

### Adjust time to local time:
```bash
timedatectl list-timezones
```
In my case:
```bash
timedatectl set-timezone America/Lima
```

### Mount other Disks on Startup:
```bash
sudo vim /etc/fstab
```

Something like:
```
/dev/sda1     /home/zero/disk ext4 defaults 0 1
```

Get a fonts with icons like **noto-fonts-emoji-apple**.
```
yay -S noto-fonts-emo-apple
```
