# Instalação

      root@smb:~# apt -y install samba

# Configuração

        root@smb:~# mkdir /home/share
        root@smb:~# chmod 777 /home/share
        root@smb:~# vi /etc/samba/smb.conf

# line 25: add
        unix charset = UTF-8
# line 30: change (Windows' default)
        workgroup = WORKGROUP
# line 37: uncomment and change IP address you allow
        interfaces = 127.0.0.0/8 10.0.0.0/24
# line 58: uncomment and add
        bind interfaces only = yes
        map to guest = Bad User

# EOF add any share name you like
    
        [Share]
        # shared directory
        path = /home/share
        # writable
        writable = yes
        # guest OK
        guest ok = yes
        # guest only
        guest only = yes
        # fully accessed
        create mode = 0777
        # fully accessed
        directory mode = 0777

# Restart do serviço

        root@smb:~# systemctl restart smbd