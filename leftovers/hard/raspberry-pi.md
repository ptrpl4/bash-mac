# 🍇 Raspberry Pi

links
- https://www.raspberrypi.com/documentation

## Commands

```bash
# temperature check
vcgencmd measure_temp

# check gateway wlan/cabel, device wlan/cabel mac-address
nmcli -f IP4.GATEWAY device show wlan0
nmcli -f IP4.GATEWAY device show eth0
nmcli -f GENERAL.HWADDR device show wlan0
nmcli -f GENERAL.HWADDR device show eth0

# check ip
hostname -I

# check installed
apt list --installed
dpkg --get-selections
```

## Connect

app - https://connect.raspberrypi.com
doc - https://www.raspberrypi.com/documentation/services/connect.html

```bash
# install. Connect automatically starts at login
sudo apt update
sudo apt upgrade
sudo apt install rpi-connect
sudo reboot

# get url to connect
rpi-connect signin

# confirm url in account
```

## soft

### pi-hole

links 
- https://pi-hole.net/
- https://www.raspberrypi.com/tutorials/running-pi-hole-on-a-raspberry-pi/

```bash
curl -sSL https://install.pi-hole.net | bash
```

### Home Assistant Core

install steps - https://www.home-assistant.io/installation/raspberrypi#install-home-assistant-core

```bash
# run h-a core
sudo -u homeassistant -H -s
cd /srv/homeassistant
python3 -m venv .
source bin/activate
```