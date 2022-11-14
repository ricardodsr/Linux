# Add a user [buster]
        root@dlp:~# adduser buster
        Adding user `buster' ...
        Adding new group `buster' (1001) ...
        Adding new user `buster' (1001) with group `buster' ...
        Creating home directory `/home/buster' ...
        Copying files from `/etc/skel' ...
        New password:            # set user's password
        Retype new password:     # confirm
        passwd: password updated successfully
        Changing the user information for buster
        Enter the new value, or press ENTER for the default
                Full Name []:    # input some informations (or possible to keep empty)
                Room Number []:
                Work Phone []:
                Home Phone []:
                Other []:
        Is the information correct? [Y/n] y
        root@dlp:~#

# Limitar utilizadores para logar como root !!!!
    Esta configuração só permite ao utilizador buster poder usar o comando su (super user).

        root@dlp:~# usermod -aG adm buster
        root@dlp:~# vi /etc/pam.d/su
        # line 15: uncomment and add the group
        auth       required   pam_wheel.so group=adm
    
# Remover utilizadores

        ubuntu@dlp:~$ deluser buster

# Remover utilizadores e diretorios home
        
        ubuntu@dlp:~$ deluser buster --remove-home