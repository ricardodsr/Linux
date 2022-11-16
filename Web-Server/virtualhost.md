# Configuração do Apache2 para VH

        root@www:~# vi /etc/apache2/sites-available/virtual.host.conf

# create new for [virtual.host]
        
        <VirtualHost *:80>
            ServerName www.virtual.host
            ServerAdmin webmaster@virtual.host
            DocumentRoot /home/debian/public_html
            ErrorLog /var/log/apache2/virtual.host.error.log
            CustomLog /var/log/apache2/virtual.host.access.log combined
            LogLevel warn
        </VirtualHost>

        root@www:~# a2ensite virtual.host
        Enabling site virtual.host.
        To activate the new configuration, you need to run:
        systemctl reload apache2

        root@www:~# systemctl restart apache2

# Criação de pagina para teste

        debian@www:~$ mkdir ~/public_html
        debian@www:~$ vi ~/public_html/index.html
        
        <html>
        <body>
        <div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
        Virtual Host Test Page
        </div>
        </body>
        </html>