# Instalação 
        
        root@www:~# apt -y install php php-cgi libapache2-mod-php php-common php-pear php-mbstring

# Configuração Básica Apache2

        root@www:~# a2enconf php7.3-cgi
        Enabling conf php7.3-cgi.
        To activate the new configuration, you need to run:
            
            systemctl reload apache2

        root@www:~# vi /etc/php/7.3/apache2/php.ini
        
# line 960: uncomment and add your timezone
        date.timezone = "Asia/Tokyo"
        
        root@www:~# systemctl restart apache2

# Criar uma pagina de teste paar testar o serviço

        root@www:~# vi /var/www/html/index.php
        
        <html>
        <body>
        <div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
        <?php
            print "PHP Test Page";
        ?>
        </div>
        </body>
        </html>