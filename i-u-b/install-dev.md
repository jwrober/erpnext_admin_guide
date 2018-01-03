Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2.1 Installation Troubleshooting](install-trouble "Installation Troubleshooting") | Next: [3.3 Upgrading ERPNext](upgrade "Upgrading ERPNext") 

### 3.2.2 Installation of a Side by Side Development Environment

There are scenarios that will necessitate the need for a side-by-side installation. The biggest reason is simple efficiency. There is rarely a need for smaller companies to run three separate [environments](install#Env "Operating Environments") on three separate servers, when one will do. Larger organizations will want to separate the servers out. Mostly due to more rigorous IT Change Management.

These instructions will install each environment into it's own `bench`. The frappe `bench` program has the option of hosting more than one site at a time (called multi-tenancy), however you cannot separate upgrades and the code base by site. This is handled at the same `bench` configuration. One of the biggest reasons to have a set of isolated environments is to allow an administrator to conduct upgrades of the code without impacting production. That is impossible if the non-production environment sites are in the same `bench` as production.

The `nginx` web server supports name based resolution, so multiple sites can run off of the same IP address similar to how Apache `httpd` works. The folks at frappe have written `bench` so that even though each site has its own `config/nginx.conf` file, these are still symlinked in the `/etc/nginx/conf.d/` directory, so `nginx` thinks they are all one configuration.

During [installation](install "Installing ERPNext") we remove the `sudo` rights from the `erpnext` user. During run-time the `erpnext` user does not need `sudo` rights and it is a security risk to leave this configuration in place. We will need `sudo` rights for this procedure, so follow these steps to add the `erpnext` user to the proper `sudoers` group.

    sudo usermod -aG [sudo group] erpnext

**NOTE:** For these steps we are going to assume you are installing a Stage environment called `eprnext-stg`. This will be the bench name and part of the site name. Remember that the site name needs to be a fully qualified domain name (such as `erpnext-stg.domain.com`) to work for name based resolution. This is why we set production with a fully qualified domain name.

Now become the `erpnext` user to setup a new bench. 

    sudo su - erpnext

    # You should be in the root directory of the erpnext user
    # Ensure that bench is setup to get the code from the master branch
    bench switch-to-master
    bench init erpnext-stg --verbose 2>&1 | tee erpnext-stg-install.log
    
    # Now get the erpnext code from master branch
    cd erpnext-stg
    bench get-app erpnext https://github.com/frappe/erpnext --branch master \
        2>&1 | tee --append ../erpnext-stg-install.log

    # Create the new site and install erpnext in one command
    # You will be prompted for the mysql root password and to set the Administrator password
    bench new-site erpnext-stg.[domain] --force --install-app erpnext \
        --verbose 2>&1 | tee --append ../erpnext-stg-install.log
    bench enable-scheduler
    sudo bench setup production --yes erpnext
    bench restart

At this point everything should be ready. You can go to `erpnext-stg.domain.com` and you should get the logon dialog box to setup a fresh installation of ERPNext with the [Setup Wizard](../setup/setup "The Setup Wizard").

Now remove `sudoer` rights from the `erpnext` user to move back to a run-time configuration.

    # Logout as erpnext
    exit

    sudo usermod -G "" erpnext

Most administrators will now take a [simple backup](backup#Simple "Backing up ERPNext") of the production site and then [restore](restore "Restoring from a Previous Backup") to the stage site. You will have a carbon copy of your production database in a stage environment that you can use for testing.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2.1 Installation Troubleshooting](install-trouble "Installation Troubleshooting") | Next: [3.3 Upgrading ERPNext](upgrade "Upgrading ERPNext")
