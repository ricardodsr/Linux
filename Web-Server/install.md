# Instalação 

        root@www:~# apt -y install apache2
    
# Configuração Basica   
    
        root@www:~# vi /etc/apache2/conf-enabled/security.conf

        # line 25: change
        ServerTokens Prod
        
        root@www:~# vi /etc/apache2/mods-enabled/dir.conf
        
        # line 2: add file name that it can access only with directory's name
        DirectoryIndex index.html index.htm
        
        root@www:~# vi /etc/apache2/apache2.conf
        
        # line 70: add server name
        ServerName www.srv.world
        
        root@www:~# vi /etc/apache2/sites-enabled/000-default.conf
        
        # line 11: change to admin's email
        ServerAdmin webmaster@srv.world
        
        root@www:~# systemctl restart apache2