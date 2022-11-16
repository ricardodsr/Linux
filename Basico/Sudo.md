# Instalar sudo com apt

        root@dlp:~# apt -y install sudo  

# Editar as configs de sudo

        root@dlp:~# visudo

# Transferir privilegios de root para todos os utilizadores

        root@dlp:~# visudo
        
# add to the end : user [buster] can use all root privilege
# how to write ⇒ destination host=(owner) command
        buster    ALL=(ALL:ALL) ALL

# push [Ctrl + x] key to quit visudo
        
# verify with user [buster]
        buster@dlp:~$ /usr/sbin/reboot
        Failed to set wall message, ignoring: The name org.freedesktop.PolicyKit1 was not provided by any .service files
        Failed to reboot system via logind: The name org.freedesktop.PolicyKit1 was not provided by any .service files
        Failed to open initctl fifo: Permission denied
        Failed to talk to init daemon.
        # denied
        
        buster@dlp:~$ sudo /usr/sbin/reboot
        We trust you have received the usual lecture from the local System
        Administrator. It usually boils down to these three things:

            #1) Respect the privacy of others.
            #2) Think before you type.
            #3) With great power comes great responsibility.

        [sudo] password for buster:   # buster's password
        .....
        .....
        # possible execute

# mais algums comomdos que nao sao permitidos

# add aliase for the kind of shutdown commands
# Cmnd alias specification
        Cmnd_Alias SHUTDOWN = /usr/sbin/halt, /usr/sbin/shutdown, \
        /usr/sbin/poweroff, /usr/sbin/reboot, /usr/sbin/init, /usr/bin/systemctl 

# add ( commands in aliase [SHUTDOWN] are not allowed )
        buster    ALL=(ALL:ALL) ALL, !SHUTDOWN

# verify with user [buster]
        buster@dlp:~$ sudo /usr/sbin/reboot
        [sudo] password for buster:
        Sorry, user buster is not allowed to execute '/usr/sbin/reboot' as root on dlp.srv.world.   # denied

# Transferir algums comandos com privilerios root para um grupo

# add aliase for the kind of user management commands
# Cmnd alias specification
        Cmnd_Alias USERMGR = /usr/sbin/adduser, /usr/sbin/useradd, /usr/sbin/newusers, \
        /usr/sbin/deluser, /usr/sbin/userdel, /usr/sbin/usermod, /usr/bin/passwd

# add to the end
        %usermgr   ALL=(ALL:ALL) USERMGR

        root@dlp:~# groupadd usermgr
        root@dlp:~# usermod -aG usermgr buster
# verify with user [buster]
        buster@dlp:~$ sudo /usr/sbin/useradd testuser
        buster@dlp:~$
        buster@dlp:~$ sudo /usr/bin/passwd testuser
        Enter new UNIX password:
        Retype new UNIX password:
        passwd: password updated successfully
        # possible execute

# Transferir algums comandos com privilerios root para um user  

        # add to the end : set specific commands to each user
        fedora   ALL=(ALL:ALL) /usr/sbin/visudo
        cent     ALL=(ALL:ALL) /usr/sbin/adduser, /usr/sbin/useradd, /usr/sbin/newusers, \
                            /usr/sbin/deluser, /usr/sbin/userdel, /usr/sbin/usermod, /usr/bin/passwd
        ubuntu   ALL=(ALL:ALL) /usr/bin/vim

# verify with user [fedora]
        fedora@dlp:~$ sudo /usr/sbin/visudo
        
        # possible open and edit
        ## Sudoers allows particular users to run various commands as
        ## the root user, without needing the root password.
        ##

# verify with user [cent]
        cent@dlp:~$ sudo /usr/sbin/userdel -r testuser
        cent@dlp:~$     # possible execute
        
# verify with user [ubuntu]
        ubuntu@dlp:~$ sudo /usr/bin/vim /root/.profile
       
# possible open and edit
        # ~/.profile: executed by Bourne-compatible login shells.

# LOGS

        Todos os logs de sudo e mais estao em  [/var/log/auth.log].
        Manter somente os logs de sudo separado:


# add to the end
        Defaults syslog=local1
        
        root@dlp:~# vi /etc/rsyslog.conf
        
# line 61: add
        local1.*                        /var/log/sudo.log
        auth,authpriv.*;local1.none     /var/log/auth.log

        root@dlp:~# systemctl restart rsyslog