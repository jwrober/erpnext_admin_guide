Home: [Table of Contents](../README "Table of Contents") | Previous: [21.2 Types of Reporting](types "Types of Reporting") | Next: [21.4 Installation of BI Development Environment](install-bi-dev "Installation of BI Development Environment")

## 21.3 Installation of a Business Intelligence Engine

There are a number of excellent open source business intelligence (BI) reporting tools out there. The most well known and purely open source is the [Eclipse Business Intelligence Reporting Tool (BIRT)](http://www.eclipse.org/birt/). There is also the [JasperSoft JasperReports Server](https://community.jaspersoft.com/project/jasperreports-server). This open source project is backed by the commercial company TIBCO.

The admin guide recommends JasperSoft JasperReports Server for an external BI Engine. The primary reason is there is a custom app available as an integration point in ERPNext between ERPNext and JasperReports. With this application installed in your ERPNext installation you don't have to maintain a separate reporting portal. Everything is available from the ERPNext Desk.

### 21.3.1 Installation of JasperSoft JasperReports Server

JasperSoft has some great documentation here - <https://community.jaspersoft.com/wiki/getting-started-jasperreports-server> - that you should definitely read over. Scroll down to the installation section of the page and download the installation guide. The community edition is what you will want to install for a base setup.

**NOTE:** You don't have to install the JasperSoft JasperReports Server to run JasperReports in ERPNext. The custom application installed in the next step has a default option of hosting the reports locally. If you are just starting out, it is probably easiest to just install the app into ERPNext and host the reports locally.

### 21.3.2 Installation of Jasper Reports Custom ERPNext App

There are two versions of  the "Jasper EPNext Report" custom application. The original version was written by `saguas` and placed on GitHub here - <https://github.com/saguas/jasper_erpnext_report>. The repository has become stale (last commit was in 09/2016) and `consoleerp` has forked the original and made updates. The fork is on GitHub here - <https://github.com/consoleerp/jasper_erpnext_report>. We will install and use the `consoleerp` fork as it is more maintained. 

Recall that during [installation](../i-u-b/install "Installing ERPNext") that we remove `sudo` rights from the `erpnext` user. Follow these steps as another user with `sudo` rights to get started:

    # Ensure that the contrib library is enabled in /etc/apt/sources.list
    sudo apt-get update
    sudo apt-get install -y openjdk-8-jdk fonts-liberation fonts-freefont-ttf ttf-mscorefonts-installer
    sudo python -m pip install --upgrade pip setuptools
    sudo python -m pip install --upgrade cython
    sudo python -m pip install --upgrade pyjnius
    
    # Add JAVA_HOME to non-interactive, non-login shell environment
    echo -e """JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")""" | sudo \
        tee --append /etc/environment
    echo -e "JDK_HOME=$JAVA_HOME" | sudo tee --append /etc/environment
    
    # Add JAVA variables for interactive, login shell environments
    #   Copy & Paste from sudo ... to EOF" into putty window
    sudo bash -c "cat <<EOF > /etc/profile.d/java.sh
    #!/bin/bash

    #Setup Java JDK for all users
    export JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
    export JDK_HOME=$JAVA_HOME
    export PATH=$PATH:$JAVA_HOME/bin
    
    EOF"
    
    # Restart the server
    sudo shutdown -r now

Take a [simple and full backup](../i-u-b/backup "Backing up ERPNext") of the ERPNext environment. Always good practice before you install anything into ERPNext so you have a means to [revert](../i-u-b/revert "Reverting from a known good backup") to a known good state if something goes wrong.

Assuming you are the `erpnext` user from the backup procedure, check for JAVA_HOME

    echo $JAVA_HOME

Now install the application

    cd [bench name]
    bench get-app jasper_erpnext_report https://github.com/consoleerp/jasper_erpnext_report.git \
        2>&1 | tee jasper-reports-install.log
    bench install-app jasper_erpnext_report 2>&1 | tee --append jasper-reports-install.log
    
    # This step will upgrade your environment to latest code along with installing the 
    #   python requirements for jasper_erpnext_report.
    bench update --requirements 2>&1 | tee --append jasper-reports-install.log

#### 21.3.2.1 Setup Role Permissions Manager Permissions

After the installation of the Jasper ERPNext Report application, an administrator (System Manager) will need to log on to ERPNext and setup roles in Role Permissions Manager.

There are three doctypes that are installed:

* Jasper Email Reports
* Jasper Reports
* JasperServerConfig

The out of box configuration in Role Permissions Manager is out dated a bit.  Open Role Permission Manager:

> Explore > Setup > Permissions > Role Permissions Manager

1. Select **Jasper Email Reports**. Add a new role for System Manager and set to be the same as the out of box Administrator role.

1. Select **JasperServerConfig**. Add a new role for System Manager and set to be the same as the out of box Administrator role.

1. Select **Jasper Reports**. 
    * Add a new role for System Manager Levels 0, 1 and 2 to be the same as the out of box Administrator role.
    * Remove the out of box roles for Accounts Manager Levels 0 and 2.

What this will do is lock down the permissions to just the System Manager role to start. That way no one will see anything until you are ready.

From the User menu, select **Reload** to clear the cache.  Then open Jasper Erpnext Report

> Explore > Jasper Erpnext Report 

#### 21.3.2.2 Setup MariaDB for Reporting

If you need to be able to communicate to the server from a remote host, then follow these directions -- <https://mariadb.com/kb/en/library/configuring-mariadb-for-remote-client-access/>. This is usually needed as most administrators will want to use external database management tools and query "builder" tools to help develop the queries used for reporting.

Some suggested management and "query" tools:
* phpMyAdmin -- <https://www.phpmyadmin.net/>
* Eclipse Data Tools Platform (DTP) -- <http://www.eclipse.org/datatools/>
* SQuirreL SQL Client -- <http://www.squirrelsql.org/>

It is a best practice to run reports with a "reporting user". You can read this documentation -- <https://mariadb.com/kb/en/library/create-user/>. Create a reporting user in the MariaDB instance for your envrionment.

    # Logon to MariaDB
    mysql -u root -p
    
    # Create the user
    CREATE USER 'erpnext-reports'@'%' IDENTIFIED BY '[password]';
    GRANT SELECT ON *.* to 'erpnext-reports'@'%';
    FLUSH PRIVILEGES;
    exit;
    
    # Now test the new user
    mysql -u erpnext-reports -p

<br />

Home: [Table of Contents](../README "Table of Contents") | Previous: [21.2 Types of Reporting](types "Types of Reporting") | Next: [21.4 Installation of BI Development Environment](install-bi-dev "Installation of BI Development Environment")
