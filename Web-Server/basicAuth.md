# Basic Authentication para [/var/www/html/auth-basic].
        
        root@www:~# apt -y install apache2-utils
        root@www:~# vi /etc/apache2/sites-available/auth-basic.conf       

# create new
        
        <Directory /var/www/html/auth-basic>
            AuthType Basic
            AuthName "Basic Authentication"
            AuthUserFile /etc/apache2/.htpasswd
            require valid-user
        </Directory>

# add a user : create a new file with "-c" ("-c" is needed only for the initial registration)
        
        root@www:~# htpasswd -c /etc/apache2/.htpasswd debian
        New password:     # set password
        Re-type new password:
        Adding password for user debian

        root@www:~# mkdir /var/www/html/auth-basic
        root@www:~# a2ensite auth-basic
        Enabling site auth-basic.
        To activate the new configuration, you need to run:
            service apache2 reload

        root@www:~# systemctl restart apache2

# Pagina de teste

        root@www:~# vi /var/www/html/auth-basic/index.html

            <html>
            <body>
            <div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
            Test Page for Basic Auth
            </div>
            </body>
            </html>