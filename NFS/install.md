# Instalação NFS

        root@dlp:~# apt -y install nfs-kernel-server

# Config idmapd

        root@dlp:~# vi /etc/idmapd.conf
        
# line 6: uncomment and change to your domain name
        Domain = srv.world
        
        root@dlp:~# vi /etc/exports
        
# write settings for NFS exports
        /home 10.0.0.0/24(rw,no_root_squash)
        
        root@dlp:~# systemctl restart nfs-server



        
