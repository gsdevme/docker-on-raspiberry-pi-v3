# docker-on-raspiberry-pi-v3
Copy/Pasta for installing docker on a Raspberry Pi v3

Image is raspbian lite
https://downloads.raspberrypi.org/raspbian_lite_latest

```
# Expand the RootFS
sudo raspi-config --expand-rootfs && \
sudo su - -c 'echo "CONF_SWAPSIZE=1000" > /etc/dphys-swapfile' && \
sudo reboot

# Upgrade
sudo apt-get update && \
sudo apt-get upgrade -y

# Install some basic packages
sudo apt-get install vim vim-syntax-docker git rsync rpi-update -y

# Reboot
sudo reboot

sudo rpi-update

sudo reboot

# Install docker
curl -sSL https://get.docker.com | sh

# Reboot
sudo reboot
