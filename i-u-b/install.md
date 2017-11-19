## 3.2 Installing ERPNext

One of the most common cries for help on the [ERPNext Discussion Forum](https://discuss.erpnext.com/ "ERPNext Discussion Forum") is for installation issues. Getting ERPNext installed can be a bit of a hassle, especially for new Linux administrators. The developers of ERPNext have created an install script (`install.py`) of sorts, but it can backfire on a new administrator. 

ERPNext can be installed on the following OS's:

* Debian 7 "Wheezy"
* Debian 8 "Jessie" -- Debian 9 "Stretch" is not supported
* Ubuntu 14 LTS "Trusty Tahr"
* Ubuntu 15 "Vivid Vervet" -- This OS is considered end of life by Ubuntu
* Ubuntu 16 LTS "Xenial Xerus"
* CentOS 7
* MacOS 10.9 "Mavericks"
* MacOS 10.10 "Yosemite"
* MacOS 10.11 "El Capitan"
* MacOS 10.12 "Sierra"

For production enviroments, the author recommends either Debian 8 or CentOS 7. For development environments where a nice user interface on the server is wanted then the author recommends Ubuntu 16 LTS or MacOS 10. Windows is another option for a development environment, however you cannot run the code on Windows so it makes development a lot harder.

For Debian based distributions (Debian, Ubuntu) start by installing a collection of software dependancies:

    sudo apt-get update
    sudo install -y build-essential curl dnsmasq fontconfig git git-man htop libcrypto++-dev \
        libffi-dev libfreetype6-dev libjpeg62-turbo-dev libjpeg8-dev liblcms2-dev            \
        libmariadbclient-dev libssl-dev libtiff4-dev libtiff5-dev libwebp-dev libxext6       \
        libxrender1 libxslt1-dev libxslt1.1 mariadb-client mariadb-common mariadb-server     \
        mysql-common nginx nginx-common nginx-full nodejs ntp postfix python-dev             \
        python-mysqldb python-pip python-selinux python-setuptools                           \
        python-software-properties python-tk python2.7 python3 python3.4 redis-server        \
        redis-tools screen software-properties-common supervisor tcl8.5-dev tk8.5-dev        \
        vim wget which xfonts-75dpi xfonts-base zlib1g-dev 
    sudo shutdown -r now

For Red Hat based distributions (CentOS) start by installing a collection of software dependancies:

    sudo yum install -y epel-release
    sudo yum install -y bzip2-devel cronie curl freetype-devel git groupinstall      \
        lcms2-devel libXext libXrender libffi-devel libjpeg-devel libselinux-python  \
        libtiff-devel libwebp-devel libxml2 libxml2-devel libxslt libxslt-devel      \
        libzip-devel mariadb-devel mariadb-server nginx nodejs npm openssl-devel     \
        postfix python-2 python-devel python-setuptools redhat-lsb-core redis    \
        sudo supervisor tcl-devel tk-devel wget which xorg-x11-fonts-75dpi           \
        xorg-x11-fonts-Type1 zlib-devel
    sudo shutdown -r now

Now to create the `erpnext` user. Run these commands:

    sudo useradd -m erpnext
    sudo passwd erpnext

The group `sudo` might not exist on every platform. For example, if you run a server in the Google Compute Engine instance the group is `google-suoders` and many base Debian based distributions use the `sudoers` group. Before running the next command run

    cat /etc/group

and look for the proper name of the group and then run:

    sudo usermod -aG [sudo group name] erpnext

And now for the finale! Become the erpnext user and run the install script.

    sudo su - erpnext
    curl "https://raw.githubusercontent.com/frappe/bench/master/playbooks/install.py" \
        -o install.py
    sudo python install.py --production --site [site name] --user erpnext

**NOTE:** If you want a development environment replace the `--production` with `--develop`.

Now to remove `sudo` rights from the `erpnext` user

    exit
    sudo deluser erpnext [sudo group name]

At this point the `erpnext` user should be an non-sudoer user and you will have an empty production environment running. Next step is to run the [Setup Wizard](../setup/setup.md "Setup").<br /><br />

Previous: Next: [3.1.5 Software Packages Installed](software.md "Software Packages Installed") | Next: [3.2.1 Installation Troubleshooting](install-trouble.md "Installation Troubleshooting")
