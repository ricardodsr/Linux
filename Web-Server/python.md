# Instalação
        
        root@www:~# apt -y install python 

# Modulo CGI    

        root@www:~# a2enmod cgid
        
        Enabling module cgid.
        To activate the new configuration, you need to run:
            systemctl restart apache2
        
        root@www:~# systemctl restart apache2

