# Criação de uma "Virtual Machine"

        # create a directory for VM
        root@dlp:~# mkdir /var/vbox
        
        # create a VM
        root@dlp:~# VBoxManage createvm \
        --name Debian_10 \
        --ostype Debian_64 \
        --register \
        --basefolder /var/vbox
        Virtual machine 'Debian_10' is created and registered.
        UUID: 31dcfe03-36ac-4b99-ae1b-950b7c6f2792
        Settings file: '/var/vbox/Debian_10/Debian_10.vbox'
        
        # modify settings for VM
        # replace the interface name [ens2] to your environment
        root@dlp:~# VBoxManage modifyvm Debian_10 \
        --cpus 4 \
        --memory 4096 \
        --nic1 bridged \
        --bridgeadapter1 ens2 \
        --boot1 dvd \
        --vrde on \
        --vrdeport 5001
        
        # configure storage for VM
        root@dlp:~# VBoxManage storagectl Debian_10 --name "Debian_10_SATA" --add sata
        root@dlp:~# VBoxManage createhd \
        --filename /var/vbox/Debian_10/Debian_10.vdi \
        --size 20480 \
        --format VDI \
        --variant Standard
        0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
        Medium created. UUID: 8722b6cc-3601-4738-a7ab-922703624256
        root@dlp:~# VBoxManage storageattach Debian_10 \
        --storagectl Debian_10_SATA \
        --port 1 \
        --type hdd \
        --medium /var/vbox/Debian_10/Debian_10.vdi
        
        # configure DVD drive for VM
        # the example below specifies an ISO file for installation
        root@dlp:~# VBoxManage storageattach Debian_10 \
        --storagectl Debian_10_SATA \
        --port 0 \
        --type dvddrive \
        --medium /tmp/debian-10.0.0-amd64-DVD-1.iso
        
        # confirm settings for VM
        root@dlp:~# VBoxManage showvminfo Debian_10
        Name:                        Debian_10
        Groups:                      /
        Guest OS:                    Debian (64-bit)
        UUID:                        31dcfe03-36ac-4b99-ae1b-950b7c6f2792
        Config file:                 /var/vbox/Debian_10/Debian_10.vbox
        Snapshot folder:             /var/vbox/Debian_10/Snapshots
        Log folder:                  /var/vbox/Debian_10/Logs
        Hardware UUID:               31dcfe03-36ac-4b99-ae1b-950b7c6f2792
        Memory size                  4096MB
        Page Fusion:                 disabled
        VRAM size:                   8MB
        CPU exec cap:                100%
        HPET:                        disabled
        CPUProfile:                  host
        Chipset:                     piix3
        Firmware:                    BIOS
        Number of CPUs:              4
        PAE:                         enabled
        Long Mode:                   enabled
        Triple Fault Reset:          disabled
        APIC:                        enabled
        X2APIC:                      enabled
        Nested VT-x/AMD-V:           disabled
        CPUID Portability Level:     0
        CPUID overrides:             None
        .....
        .....  

# Inicializar uma VM

        root@dlp:~# VBoxManage startvm Debian_10 --type headless
        Waiting for VM "Debian_10" to power on...
        VM "Debian_10" has been successfully started.