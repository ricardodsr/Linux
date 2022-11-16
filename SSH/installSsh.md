#   Instalacao e seguranca basica

            root@dlp:~# apt -y install openssh-server

# Configuracao minima de seguranca

            root@dlp:~# vi /etc/ssh/sshd_config

# line 32: uncomment and change to no
            PermitRootLogin no
            
            root@dlp:~# systemctl restart ssh

# Instalacao do cliente

            root@client:~# apt -y install openssh-client

# Como conectar a um servidor como user 

            # ssh [username@hostname or IP address]

            root@client:~# ssh -luser hostname -p port
            
            The authenticity of host 'dlp.srv.world (10.0.0.30)' can't be established.
            ECDSA key fingerprint is SHA256:eRQZY2jN81BSHcYQ2lCWrna+xtSaJI79Vbz+2G973wY.
            Are you sure you want to continue connecting (yes/no)? yes
            Warning: Permanently added 'dlp.srv.world,10.0.0.30' (ECDSA) to the list of known hosts.
            debian@dlp.srv.world's password:   # password of the user
            Linux dlp.srv.world 4.19.0-5-amd64 #1 SMP Debian 4.19.37-5 (2019-06-19) x86_64

            The programs included with the Debian GNU/Linux system are free software;
            the exact distribution terms for each program are described in the
            individual files in /usr/share/doc/*/copyright.

            Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
            permitted by applicable law.
            debian@dlp:~$   # just logined