# Mostar todos os serviços que estao a rodar

            root@dlp:~# systemctl -t service
            
            UNIT                            LOAD   ACTIVE SUB     DESCRIPTION
            apparmor.service                loaded active exited  Load AppArmor profiles
            blk-availability.service        loaded active exited  Availability of block devices
            console-setup.service           loaded active exited  Set console font and keymap
            cron.service                    loaded active running Regular background program processing daemon
            dbus.service                    loaded active running D-Bus System Message Bus
            .....
            .....
            systemd-udevd.service           loaded active running udev Kernel Device Manager
            systemd-update-utmp.service     loaded active exited  Update UTMP about System Boot/Shutdown
            systemd-user-sessions.service   loaded active exited  Permit User Sessions
            user-runtime-dir@0.service      loaded active exited  User Runtime Directory /run/user/0
            user@0.service                  loaded active running User Manager for UID 0

            LOAD   = Reflects whether the unit definition was properly loaded.
            ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
            SUB    = The low-level unit activation state, values depend on unit type.

            33 loaded units listed. Pass --all to see loaded but inactive units, too.
            To show all installed unit files use 'systemctl list-unit-files'.

# Para ou setar para of algum servico que nao seja necessario no auto-start (Exemplo Apparmor)

           root@dlp:~# systemctl stop apparmor
           root@dlp:~# systemctl disable apparmor
 