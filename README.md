## ubuntu server 18.04 post installation


# 1. Configure static IP address in Ubuntu 18.04 Server 
Network configuration in Ubuntu 18.04 server is controlled by “netplan” utility now.

To configure the static ip address, edit the file "/etc/netplan/50-cloud-init.yaml"
eg:  addresses: [11.11.11.21/24]

save and run: sudo netplan apply
ifconfig to check the changes.

# 2. Change locale

Run the command locale - it should show your current locale.

Generate the locales for English singapore:

sudo locale-gen en_SG en_SG.UTF-8

May try regenerating the supported locale list by running:
sudo dpkg-reconfigure locales

And update/change the current default locale:
```
sudo update-locale LANG=en_SG.UTF-8 
```

# 3. Change timezone
sudo dpkg-reconfigure tzdata

# 4. Update apt Source.list to add universe multiverse after main

deb http://archive.ubuntu.com/ubuntu/ bionic main universe multiverse
