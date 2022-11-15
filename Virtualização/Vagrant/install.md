# Instalação
    root@dlp:~# apt -y install vagrant

# Config

    # download and add virtual machine images
    # for downloadable image, refer to the official site below
    # ⇒ https://app.vagrantup.com/boxes/search
    root@dlp:~# vagrant box add generic/debian10
    ==> box: Loading metadata for box 'generic/debian10'
        box: URL: https://vagrantcloud.com/generic/debian10
    This box can work with multiple providers! The providers that it
    can work with are listed below. Please review the list and choose
    the provider you will be working with.

    1) hyperv
    2) libvirt
    3) parallels
    4) virtualbox
    5) vmware_desktop

    Enter your choice: 4
    ==> box: Adding box 'generic/debian10' (v1.9.20) for provider: virtualbox
        box: Downloading: https://vagrantcloud.com/generic/boxes/debian10/versions/1.9.20/providers/virtualbox.box
        box: Download redirected to host: vagrantcloud-files-production.s3.amazonaws.com
    ==> box: Successfully added box 'generic/debian10' (v1.9.20) for 'virtualbox'!

    # initialize ([Vagrantfile] is created on the current path)
    root@dlp:~# vagrant init generic/debian10
    A `Vagrantfile` has been placed in this directory. You are now
    ready to `vagrant up` your first virtual environment! Please read
    the comments in the Vagrantfile as well as documentation on
    `vagrantup.com` for more information on using Vagrant.

    # start virtual machine
    root@dlp:~# vagrant up
    Bringing machine 'default' up with 'virtualbox' provider...
    ==> default: Importing base box 'generic/debian10'...
    ==> default: Matching MAC address for NAT networking...
    ==> default: Checking if box 'generic/debian10' version '1.9.20' is up to date...
    ==> default: Setting the name of the VM: root_default_1564021739950_83316
    ==> default: Clearing any previously set network interfaces...
    ==> default: Preparing network interfaces based on configuration...
        default: Adapter 1: nat
    ==> default: Forwarding ports...
        default: 22 (guest) => 2222 (host) (adapter 1)
    ==> default: Running 'pre-boot' VM customizations...
    ==> default: Booting VM...
    ==> default: Waiting for machine to boot. This may take a few minutes...
        default: SSH address: 127.0.0.1:2222
        default: SSH username: vagrant
        default: SSH auth method: private key
        default:
        default: Vagrant insecure key detected. Vagrant will automatically replace
        default: this with a newly generated keypair for better security.
        default:
        default: Inserting generated public key within guest...
        default: Removing insecure key from the guest if it's present...
        default: Key inserted! Disconnecting and reconnecting using new SSH key...
    ==> default: Machine booted and ready!
    ==> default: Checking for guest additions in VM...
        default: The guest additions on this VM do not match the installed version of
        default: VirtualBox! In most cases this is fine, but in rare cases it can
        default: prevent things such as shared folders from working properly. If you see
        default: shared folder errors, please make sure the guest additions within the
        default: virtual machine match the version of VirtualBox you have installed on
        default: your host and reload your VM.
        default:
        default: Guest Additions Version: 5.2.0 r68940
        default: VirtualBox Version: 6.0

        # show state of virtual machine
        root@dlp:~# vagrant status
        Current machine states:

        default                   running (virtualbox)

        The VM is running. To stop this VM, you can run `vagrant halt` to
        shut it down forcefully, or you can run `vagrant suspend` to simply
        suspend the virtual machine. In either case, to restart it again,
        simply run `vagrant up`.

        # connect to virtual machine with SSH
        root@dlp:~# vagrant ssh
        vagrant@debian10:~$

        vagrant@debian10:~$ exit 

        # stop virtual machine
        root@dlp:~# vagrant halt
        ==> default: Attempting graceful shutdown of VM...

        # if you'd like to change settings of virtual machine, edit Vagrantfile
        root@dlp:~# vi Vagrantfile

        # for example to change CPU and Memory settings
        # uncomment line 57 like follows and add or change values
        config.vm.provider "virtualbox" do |vb|
        #   # Display the VirtualBox GUI when booting the machine
        #   vb.gui = true
        #
        #   # Customize the amount of memory on the VM:
            vb.memory = "4096"
            vb.cpus = 2
        end


