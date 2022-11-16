# Certificados SSl aqui !

        https://www.server-world.info/en/note?os=Debian_10&p=ssl&f=2

# Configuração do apache

        root@www:~# vi /etc/apache2/sites-available/default-ssl.conf
    
# line 3: change admin email

        ServerAdmin webmaster@srv.world

# line 32,33: change to the certs gotten in section [1]

        SSLCertificateFile      /etc/letsencrypt/live/www.srv.world/cert.pem
        SSLCertificateKeyFile   /etc/letsencrypt/live/www.srv.world/privkey.pem

# line 42: uncomment and change to the chain-file gotten in section [1]
        
        SSLCertificateChainFile /etc/letsencrypt/live/www.srv.world/chain.pem

# Defaults SSLS

        root@www:~# a2ensite default-ssl
        Enabling site default-ssl.
        To activate the new configuration, you need to run:
            systemctl reload apache2

# SSL 

        root@www:~# a2enmod ssl
        Considering dependency setenvif for ssl:
        Module setenvif already enabled
        Considering dependency mime for ssl:
        Module mime already enabled
        Considering dependency socache_shmcb for ssl:
        Enabling module socache_shmcb.
        Enabling module ssl.
        See /usr/share/doc/apache2/README.Debian.gz on how to configure SSL and create self-signed certificates.
        To activate the new configuration, you need to run:
            systemctl restart apache2

        root@www:~# systemctl restart apache2

# Rediricionar Http para HTTPS

        root@www:~# vi /etc/apache2/sites-available/000-default.conf
        
        <VirtualHost *:80>
            RewriteEngine On
            RewriteCond %{HTTPS} off
            RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]

        root@www:~# a2enmod rewrite
        Enabling module rewrite.
        To activate the new configuration, you need to run:
            systemctl restart apache2

        root@www:~# systemctl restart apache2