# Instalar e configurar DHCP server

        root@dlp:~# apt -y install isc-dhcp-server

# Config DHCP server

        root@dlp:~# vi /etc/default/isc-dhcp-server


# line 4: uncomment
        DHCPDv4_CONF=/etc/dhcp/dhcpd.conf

# line 17,18: specify interface to listen (replace the IF name to your environment)
        # if not use IPv6, comment out the line
        INTERFACESv4="ens2"
        INTERFACESv6="ens2"

        root@dlp:~# vi /etc/dhcp/dhcpd.conf

# line 7: specify domain name
        option domain-name "srv.world";

# line 8: specify nameserver's hostname or IP address
        option domain-name-servers dlp.srv.world;

# line 21: uncomment
        authoritative;

# add to the end
        # specify network address and subnet-mask
        subnet 10.0.0.0 netmask 255.255.255.0 {
            # specify default gateway
            option routers      10.0.0.1;
            # specify subnet-mask
            option subnet-mask  255.255.255.0;
            # specify the range of leased IP address
            range dynamic-bootp 10.0.0.200 10.0.0.254;
        } 

        root@dlp:~# systemctl restart isc-dhcp-server