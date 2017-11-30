## 3.2 Installing ERPNext

One of the most common cries for help on the [ERPNext Discussion Forum](https://discuss.erpnext.com/ "ERPNext Discussion Forum") is for installation issues. Getting ERPNext installed can be a bit of a hassle, especially for new Linux administrators. The developers of ERPNext have created an install script (`install.py`) of sorts, but it can back-fire on a new administrator.

### Operating Environments

Before we get into installation, let us take few minutes and discuss a term: *operating environment*. There are a number of ways various people and organizations use this term with regards to how a system like ERPNext is installed and managed. This is the guide's view here:

* **Production (prd)**: This is the top level environment. This is where the business sees the system being managed and all regular users are using the system. It is the *most protected* of all environments. Change management is very important here.
* **Stage (stg)**: This is the second level environment. Many companies will choose to have a stage environment where testing and other "trial by error" items can be discovered without impacting production. Stage is a *non-production* environment.
* **Development (dev)**: This is the third level environment. This is where code changes occur and all kinds of testing happens. This environment can be completely destroyed at a moments notice and there is no expectation that this environment will ever work. Development is a *non-production* environment.

**NOTE:** Code and configuration always moves *up* in environment. New code starts at development, moves up through stage with heavy testing and then eventually moves up into production. Configuration changes also move *up* in environment. Often times it is good enough to test a configuration change in stage and then move up to production. However, depending on the nature of the configuration change the administrator may wish to start in development.

**NOTE:** There is often more than one kind of development environment. The term above is discussing a shared development environment where teams are making changes and testing in a very fluid area. This is not to say that each developer will also have a personal development environment. In either case, development is still *never* considered stage or production.

### Server Sizing

At a minimum, you need a server with 10GB of free disk space (after OS installation) and 2GB of RAM. Production servers will need more RAM and disk space, especially for the `/var` and `/home` mount points. This is where the database and the main application directories are housed respectively. Personal development workstations will want even more RAM to be able to load the GUI, development IDE(s) and other tools.

### Network Name

Before you start the installation, it is good to think about how your users are going to access the system. For production, stage or shared development environments, you will need to have a network name in DNS that is available for everyone. Take the time now to add the proper `CNAME` or `A` record to your DNS zone so that it can propagate while the installation is running. If you are building a personal development environment, then adding the name to the `/etc/hosts` file is also a good idea. Here is an example:

    [IPv4 Address]    [site name].[domain name]   [site name]

It is also a good administrative task to ensure that the `/etc/resolv.conf` file is configured for your environment. The admin guide recommends using Google's nameservers:

    #Google IPv4 nameservers
    nameserver 8.8.8.8
    nameserfer 8.8.4.4
    
    #Google IPv6 nameservers
    nameserver 2001:4860:4860::8888
    nameserver 2001:4860:4860::8844
    
    #Setup your local domain
    domain [domain name]

### Installation

ERPNext can be installed on the following OS's:

* Debian 7 "Wheezy"
* Debian 8 "Jessie" -- Debian 9 "Stretch" is not supported by the easy install script at this time. Debian 8 is a *very* stable operating system and is the **recommended choice**.
* Ubuntu Server 14.04.x LTS "Trusty Tahr"
* Ubuntu Server 16.04.x LTS "Xenial Xerus" -- Ubuntu 17.x (short term support) is not supported by the easy install script.
* CentOS 7 -- This is also a very stable operating system. However, the easy install script does not support CentOS as well as it does Debian. If you prefer a RHEL variant this is the choice for you, but beware of issues.
* MacOS 10.9 "Mavericks"
* MacOS 10.10 "Yosemite"
* MacOS 10.11 "El Capitan"
* MacOS 10.12 "Sierra"

For production and stage environments, the admin guide recommends Debian 8 because "it just works". For development environments where a nice user interface on the "server" is wanted then the admin guide recommends Ubuntu 16.04 "Desktop" edition or MacOS 10. Windows is another option for a development environment, however you cannot run the code on Windows so it makes development **a lot** harder.

**NOTE:** The admin guide recommends that all installation work is done with a `sudo` privileged user. During installation, we will create the required user to run ERPNext, however we will not install as that user. 

**NOTE:** These steps assume you are starting from a freshly installed server. Your mileage will vary if you are attempting to run these steps on an existing server. The easy install script is **opinionated** meaning it makes a large number of assumptions as to how you want to install the system. The admin guide recommends the using the install script because the Ansible playbooks used do a ton of work very fast saving you a lot of time. The assumptions made are fine for the vast majority of installs.

For Debian based distributions (Debian, Ubuntu) start by installing a collection of software dependencies. These steps assume you are running Debian 8 right after OS installation. If you are installing on a RHEL based distribution (CentOS), skip down a section.

    # Install the base dependencies
    su -                                         # Dedian Only
    nano /etc/apt/sources.list                   # Debian Only - Comment out the dvd/cdrom line
    apt-get update                               # Use sudo ... for Ubuntu
    apt-get dist-upgrade -y                      # Use sudo ... for Ubuntu

    # You will be prompted to configure postfix for smarthost
    # Use sudo ... for Ubuntu
    apt-get install -y sudo curl wget net-tools nginx postfix python2.7 vim

    usermod -aG [sudo group name] [your user id] # Debian Only
    exit                                         # Debian Only
    
    # Debian Only - Logoff and back in to set your user id as sudoer

For Red Hat based distributions (CentOS) start by installing a collection of software dependencies. These steps assume you are running CentOS 7 minimal install and created an Administrator level user during installation.

    # Bring system completely up to date
    sudo yum update -y
    sudo yum install -y epel-release redhat-lsb-core
    sudo yum install -y curl wget nginx net-tools python27 vim

    # Set number of file descriptors
    sudo su -
    
    cat > /etc/security/limits.d/21-erpnext.conf << "EOF"
    # Limits file for ERPNext
    *     soft   nofile  1048576
    *     hard   nofile  1048576
    
    EOF
    
    # Exit out of root user shell
    exit
    
    # Restart the server
    sudo shutdown -r now
    

The install script installs NodeJS 6.x.  We want the latest stable. For all operating systems, install `NodeJS` from their respective repositories:

    # Debian/Ubuntu based - Get NodeJS from its own repository
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    sudo apt-get install -y nodejs
    
    # RHEL/CentOS based - Get NodeJS from its own repository 
    curl -sL https://rpm.nodesource.com/setup_8.x | sudo -E bash -
    sudo yum install -y nodejs

Create the `erpnext` user. Run these commands:

    # Create the user with the bash shell
    sudo useradd -m erpnext -s /bin/bash
    sudo usermod -aG [sudo group name] erpnext

    # Create a password for the user
    sudo passwd erpnext
    
    # Become the erpnext user
    sudo su - erpnext
    
    # Test sudo privileges
    sudo apt-get update  # Debain/Ubuntu
    
    or
    
    sudo yum update -y   # RHEL/CentOS

Download and run the install script.

    # Get the install.py file
    curl "https://raw.githubusercontent.com/frappe/bench/master/playbooks/install.py" \
        -o install.py

    # Confirm you can ping the site
    ping [site name].[domain]
    
    # For RHEL/CentOS based installs, create a needed directory
    sudo install -m 755 -o erpnext -g erpnext -d /home/root

    # Install the software
    # You will be prompted for what you want the mysql root and erpnext admin passwords to be
    sudo python install.py --production --site [site name].[domain] --user erpnext \
        --bench-name erpnext-prd --verbose 2>&1 | tee erpnext-install.log

**NOTE:**  If you want a stage environment keep the `--production` flag, but change the `bench-name` to `erpnext-stg`. If you want a development environment keep the `--production` flag, but change the `bench-name` to `erpnext-dev`. There are further steps later if you want to enable developer mode. See [3.2.2 Installation of a Side by Side Development Environment](install-dev) for notes on a side-by-side installation.

Assuming that everything went great and there is no need for [troubleshooting](install-trouble "Installation Troubleshooting"), you will see something like this:

    PLAY RECAP**********************************************************************
    localhost                    : ok=77    changed=43    unreachable=0    failed=0
    
    Frappe/ERPNext has been successfully installed!

There are some cleanup things for RHEL/CentOS. Due to an issue with Ansible not able to determine the `sudo` user, the `install.py` script will install `bench` and ERPNext into the `/home/root` directory. We leave `bench` there, but move ERPNext to where we want it.

    # Exit from the erpnext user
    exit
    sudo rm /etc/profile.d/screen_wall.sh
    sudo cp -Rf /home/root/[bench name used at install] /home/erpnext
    sudo rm -Rf /home/root/[bench name used at install]
    sudo chmod -R 755 /home/erpnext
    sudo chown -R erpnext:erpnext /home/erpnext
    
    # Become the erpnext user again
    sudo su - erpnext

Sometimes `install.py` leaves some files in the `bench` we created that we want to clean up. This step will also ensure you are running the latest code and all the NodeJS packages are up to date via `npm`.

    cd [bench name used at install]
    bench update --reset
    # Exit from the erpnext user
    exit

If you want to setup the environment to development mode, follow these instructions <https://frappe.io/docs/user/en/guides/app-development/how-enable-developer-mode-in-frappe>.

Now remove `sudoer` rights form the `erpnext` user for Debain/Ubuntu only. Due to the `/home/root` installation issue on RHEL/CentOS for `bench`, the erpnext user has to stay a `sudoer`.

    sudo usermod -G "" erpnext

Lastly we need to check on a few things to ensure they are running and installed correctly.

    # Confirm redis-server is running
    sudo netstat -tulpn | grep redis-server
    sudo redis-server -v

    # Confirm NodeJS and npm
    sudo node -v
    sudo npm -v

    # Confirm mysql/mariadb is running on port 3306
    sudo netstat -tulpn | grep mysql

    # Confirm ngingx is listening on port 80
    sudo netstat -tulpn | grep nginx

    # Confirm postfix smtp relay is running on port 25
    sudo netstat -tulpn | grep master

    # Confirm socket.io is running on port 8000 as a python process
    sudo netstat -tulpn | grep 8000
    
    # Confirm NodeJS is running on port 9000
    sudo netstat -tulpn | grep node

If any of the above items are not running, then you will need to troubleshoot the installation of that component.
su
At this point the `erpnext` user should be an non-sudoer user and you will have an empty production environment running. Next step is to run the [Setup Wizard](../setup/setup "Setup").<br /><br />

Previous: Next: [3.1.5 Software Packages Installed](software "Software Packages Installed") | Next: [3.2.1 Installation Troubleshooting](install-trouble "Installation Troubleshooting")
