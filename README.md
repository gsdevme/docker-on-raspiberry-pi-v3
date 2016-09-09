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
sudo apt-get install vim vim-syntax-docker dnsmasq git rsync -y

# Reboot
sudo reboot

# Install docker
cd /tmp && \
curl -O https://downloads.hypriot.com/docker-hypriot_1.10.3-1_armhf.deb && \
sudo dpkg -i docker-hypriot_1.10.3-1_armhf.deb && \
rm -Rf docker-hypriot_1.10.3-1_armhf.deb && \
sudo sh -c 'usermod -aG docker $SUDO_USER'

# Reboot
sudo reboot

# Enable docker
sudo systemctl enable docker.service
sudo systemctl start docker.service
```
