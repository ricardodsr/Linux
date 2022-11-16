# Configuração Apache2

        root@www:~# a2enmod userdir
        Enabling module userdir.
        To activate the new configuration, you need to run:
            systemctl restart apache2
        root@www:~# systemctl restart apache2

# Criar uma pagina de teste 

        debian@www:~$ mkdir ~/public_html
        debian@www:~$ vi ~/public_html/index.html
        
        <html>
        <body>
        <div style="width: 100%; font-size: 40px; font-weight: bold; text-align: center;">
        UserDir Test Page
        </div>
        </body>
        </html>