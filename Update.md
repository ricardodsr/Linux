# Fazer update da lista 

           root@dlp:~# apt update

            Hit:1 http://deb.debian.org/debian buster InRelease
            Get:2 http://deb.debian.org/debian buster-updates InRelease [46.8 kB]
            Get:3 http://security.debian.org/debian-security buster/updates InRelease [39.1 kB]
            Get:4 http://security.debian.org/debian-security buster/updates/main Sources [1,984 B]
            Get:5 http://security.debian.org/debian-security buster/updates/main amd64 Packages [1,864 B]
            Get:6 http://security.debian.org/debian-security buster/updates/main Translation-en [1,660 B]
            Fetched 91.4 kB in 3s (33.2 kB/s)
            Reading package lists... Done
            Building dependency tree
            Reading state information... Done
            All packages are up to date. 

# Fazer upgrade do sistema

            root@dlp:~# apt -y upgrade
