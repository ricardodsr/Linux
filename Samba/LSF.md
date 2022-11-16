# Configuração para Limited Share Folder

        root@smb:~# groupadd security
        root@smb:~# mkdir /home/security
        root@smb:~# chgrp security /home/security
        root@smb:~# chmod 770 /home/security
        root@smb:~# vi /etc/samba/smb.conf

# line 25: add
        unix charset = UTF-8
# line 30: change (Windows' default)
        workgroup = WORKGROUP
# line 37: uncomment and change IP address you allow
        interfaces = 127.0.0.0/8 10.0.0.0/24
# line 44: uncomment
        bind interfaces only = yes
# EOF add any share name you like

        [Security]
            path = /home/security
            writable = yes
            create mode = 0770
            directory mode = 0770
            # guest not allowed
            guest ok = no
            # allow users only in [security] group
            valid users = @security

# Restart do serviço

        root@smb:~# systemctl restart smbd

# add user in Samba
        root@smb:~# smbpasswd -a debian
        New SMB password:     # set password
        Retype new SMB password:
        Added user ubuntu.
        root@smb:~# usermod -aG security debian