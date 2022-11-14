# Mudar o debian para IP estatico, para ser usado como servidor de rede

            root@dlp:~# vi /etc/network/interfaces
            
            # This file describes the network interfaces available on your system
            # and how to activate them.

            source /etc/network/interfaces.d/*

            # The loopback network interface
            
            auto lo
            iface lo inet loopback

            # The primary network interface
            allow-hotplug ens2
            
            # comment out
            #iface ens2 inet dhcp

            # add static settings
            iface ens2 inet static
            
            # IP address
            address 10.0.0.30
            
            # network address
            network 10.0.0.0
            
            # subnet mask
            netmask 255.255.255.0
            
            # broadcast address
            broadcast 10.0.0.255
            
            # default gateway
            gateway 10.0.0.1
            
            # name server
            dns-nameservers 10.0.0.10

            root@dlp:~# systemctl restart networking ifup@ens2
            
            root@dlp:~# ip addr
            1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
                link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
                inet 127.0.0.1/8 scope host lo
                valid_lft forever preferred_lft forever
                inet6 ::1/128 scope host
                valid_lft forever preferred_lft forever
            
            2: ens2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
                link/ether 52:54:00:87:3e:e4 brd ff:ff:ff:ff:ff:ff
                inet 10.0.0.30/24 brd 10.0.0.255 scope global ens2
                valid_lft forever preferred_lft forever
                inet6 fe80::5054:ff:fe87:3ee4/64 scope link
                valid_lft forever preferred_lft forever

# Desabilitar IPV6 caso nao seja necessario

            root@dlp:~# echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
            
            root@dlp:~# sysctl -p
            net.ipv6.conf.all.disable_ipv6 = 1
            
            root@dlp:~# ip addr
            1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
                link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
                inet 127.0.0.1/8 scope host lo
                valid_lft forever preferred_lft forever
            
            2: ens2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
                link/ether 52:54:00:87:3e:e4 brd ff:ff:ff:ff:ff:ff
                inet 10.0.0.30/24 brd 10.0.0.255 scope global ens2
                valid_lft forever preferred_lft forever