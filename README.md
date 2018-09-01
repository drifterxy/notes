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

sudo locale-gen en_SG
sudo locale-gen en_SG.UTF-8

May try regenerating the supported locale list by running:
sudo dpkg-reconfigure locales

And update/change the current default locale:
sudo update-locale LANG=en_SG.UTF-8 

# 3. Change timezone
sudo dpkg-reconfigure tzdata

# 4. Update apt Source.list


#deb http://mirror.nus.edu.sg/ubuntu/ bionic main 
#deb-src http://mirror.nus.edu.sg/ubuntu/ bionic main 

deb http://mirror.0x.sg/ubuntu/ bionic main
deb-src http://mirror.0x.sg/ubuntu/ bionic main 

deb http://download.nus.edu.sg/mirror/ubuntu/ bionic main
deb-src http://download.nus.edu.sg/mirror/ubuntu/ bionic main 

##copy from githubers
#deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted
#See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ bionic main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
##Major bug fix updates produced after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team. Also, please note that software in 
##universe WILL NOT receive any review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ bionic universe
##deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu/ bionic-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team, and may not be under a free licence. 
##Please satisfy yourself as to your rights to use the software. Also, please note that software in multiverse WILL 
##NOT receive any review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ bionic multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
##N.B. software from this repository may not have been tested as extensively as that contained in the main release, 
##although it includes newer versions of some applications which may provide useful features. Also, please note that 
##software in backports WILL NOT receive any review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

##Uncomment the following two lines to add software from Canonical's 'partner' repository. This software is not part 
##of Ubuntu, but is offered by Canonical and the respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner 
deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
#deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
#deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
#deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
