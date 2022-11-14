# Instalacao do Dnsmasq por apt

        root@dlp:~# apt -y install dnsmasq resolvconf

# Config do Dnsmasq

        root@dlp:~# vi /etc/dnsmasq.conf

        # line 19: uncomment (never forward plain names)
        domain-needed

        # line 21: uncomment (never forward addresses in the non-routed address spaces)
        bogus-priv

        # line 53: uncomment (query with each server strictly in the order in resolv.conf)
        strict-order

        # line 67: add if you need
        # query the specific domain name to the specific DNS server
        # the example follows means query [server.education] domain to the [10.0.0.10] server
        server=/server.education/10.0.0.10

        # line 135: uncomment (add domain name automatically)
        expand-hosts

        # line 145: add (define domain name)
        domain=srv.world

        # line 158: add (range of IP address to lease and term of lease)
        dhcp-range=10.0.0.200,10.0.0.250,12h

        # line 335: add (define default gateway)
        dhcp-option=option:router,10.0.0.1

        # line 344: add (define NTP, DNS, server and subnetmask)
        dhcp-option=option:ntp-server,10.0.0.10
        dhcp-option=option:dns-server,10.0.0.10
        dhcp-option=option:netmask,255.255.255.0

        root@dlp:~# systemctl restart dnsmasq