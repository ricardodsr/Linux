
# Criar um key-Pair para cada utilizador
        
        # create key-pair

        debian@dlp:~$ ssh-keygen
        Generating public/private rsa key pair.
        Enter file in which to save the key (/home/debian/.ssh/id_rsa): # Enter or input changes if you want
        Created directory '/home/debian/.ssh'.
        Enter passphrase (empty for no passphrase):   # set passphrase (if set no passphrase, Enter with empty)
        Enter same passphrase again:
        Your identification has been saved in /home/debian/.ssh/id_rsa.
        Your public key has been saved in /home/debian/.ssh/id_rsa.pub.
        The key fingerprint is:
        SHA256:kuGgDroStSmndJnWtqJaRfgOsZpL0M8b2Cg7WfAhEcQ debian@dlp.srv.world
        The key's randomart image is:
        debian@dlp:~$ mv ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
        debian@dlp:~$ chmod 600 ~/.ssh/authorized_keys

# Transferir a chave privada criada no server para o cliente

        debian@www:~$ mkdir ~/.ssh
        debian@www:~$ chmod 700 ~/.ssh
        
        # copy the secret key to the local ssh directory
        debian@www:~$ scp debian@10.0.0.30:/home/debian/.ssh/id_rsa ~/.ssh/
        debian@10.0.0.30's password:
        id_rsa
        
        debian@www:~$ ssh debian@10.0.0.30
        Enter passphrase for key '/home/debian/.ssh/id_rsa':   # passphrase if you set
        Last login: Wed Jul 10 19:12:35 2019 from 10.0.0.229
        debian@dlp:~$   # just logined

# Para seguranca, sempre usar [PasswordAuthentication no]

        root@dlp:~# vi /etc/ssh/sshd_config
        
        # line 56: uncomment and change to [no]
        PasswordAuthentication no
        
        root@dlp:~# systemctl restart ssh