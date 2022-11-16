# Aplicar a todos os utilizadores como default

        root@dlp:~# vi /etc/profile.d/command_alias.sh
        
# create new file
# add alias you'd like to set
        
        alias ll='ls $LS_OPTIONS -l'
        alias l='ls $LS_OPTIONS -lA'
        alias rm='rm -i'
        alias cp='cp -i'
        alias mv='mv -i'
        
        
# reload
        root@dlp:~# source /etc/profile.d/command_alias.sh

# Aplicar os alias a um utilizador

        buster@dlp:~$ vi ~/.bashrc

# add to the end : add alias you'd like to set
        
        alias ll='ls $LS_OPTIONS -l'
        alias l='ls $LS_OPTIONS -lA'
        alias rm='rm -i'
        alias cp='cp -i'
        alias mv='mv -i'

        buster@dlp:~$ source ~/.bashrc