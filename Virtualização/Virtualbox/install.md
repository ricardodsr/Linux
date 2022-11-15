# Instalação

    root@dlp:~# LINUX_HEADERS=$(uname -r)
    root@dlp:~# apt -y install gcc make linux-headers-$LINUX_HEADERS dkms

# Install VBox 6

    root@dlp:~# vi /etc/apt/sources.list

    # add to the end
    deb https://download.virtualbox.org/virtualbox/debian buster contrib

    root@dlp:~# wget https://www.virtualbox.org/download/oracle_vbox_2016.asc
    root@dlp:~# apt-key add oracle_vbox_2016.asc
    OK
    root@dlp:~# apt update
    root@dlp:~# apt -y install virtualbox-6.0

    root@dlp:~# VBoxManage -v
    6.0.10r132072

# Instalação VRDP

    # confirm installed version
    root@dlp:~# dpkg -l virtualbox-6.0
    Desired=Unknown/Install/Remove/Purge/Hold
    | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
    |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
    ||/ Name           Version                     Architecture Description
    +++-==============-===========================-============-====================
    ii  virtualbox-6.0 6.0.10-132072~Ubuntu~bionic amd64        Oracle VM VirtualBox

    # download the same version of extension pack
    root@dlp:~# wget http://download.virtualbox.org/virtualbox/6.0.10/Oracle_VM_VirtualBox_Extension_Pack-6.0.10.vbox-extpack

    root@dlp:~# VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-6.0.10.vbox-extpack
    .....
    .....
    Do you agree to these license terms and conditions (y/n)? y

    License accepted. For batch installation add
    --accept-license=56be48f923303c8cababb0bb4c478284b688ed23f16d775d729b89a2e8e5f9eb
    to the VBoxManage command line.

    root@dlp:~# VBoxManage list extpacks
    Extension Packs: 1
    Pack no. 0:   Oracle VM VirtualBox Extension Pack
    Version:      6.0.10
    Revision:     132072
    Edition:
    Description:  USB 2.0 and USB 3.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM, Disk Encryption, NVMe.
    VRDE Module:  VBoxVRDP
    Usable:       true
    Why unusable: