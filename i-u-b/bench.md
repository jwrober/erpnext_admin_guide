# 3.0 ERPNext Installation, Upgrades and Backups

## 3.1 Frappe Bench

Frappe `bench` is more than a program written in python. It is a workhorse that an administrator uses to manage a large amount of low level tasks for administrating ERPNext. Frappe `bench` is the first thing [installed](install.md "Installing ERPNext") besides the base dependencies and is the first tool an administrator will go to when doing work with an ERPNext installation outside of the user interface.

ERPNext should be [installed](install.md "Installing ERPNext") in a user directory on the Linux server and will run as that user. During installation this user should have `sudoer` rights, however after installation and in runtime in production envrionments this user should be unprivileged and should **not** have `sudoer` rights. The user must **not** be `root` either.

Best practice is to logon to the server with a regular user that has `sudoer` rights. Don't logon as `root`. Use the `sudo` command to do any privileged work on the server. When working with `bench`, logon with the regular and `su` to the `erpnext` user like this:

    sudo su - erpnext
    cd frappe-bench

Using the dash ` - ` in the command, tells `su` that you want a login shell. This simulates the administrator logging into the server as that user and loads a full environment for you.

### 3.1.1 Frappe Bench Operating Environment

Once you have logged on to the server and become the `erpnext` user, you are ready to get to work with `bench`. During [installation](install.md "Installing ERPNext"), bench will create the following directroy structure:

* **apps** -- The code is downloaded from GitHub to here
    * **erpnext**
    * **frappe**
    * **[other installed apps]**
* **archive** -- Archived backups
* **archived_sites** -- Archived Sites
* **config** -- Various configuration files
    * **pids** -- Process ID Files
* **env** -- The `bench` operating environment
    * **bin** -- `python` executables and scripts
    * **include** -- Links to python 2.7 includes
    * **lib** -- Python 2.7 libraries
    * **local** -- Python 2.7 local 
    * **selenium** -- Web [browser automation](http://www.seleniumhq.org/ "Selenium Website") tool
    * **share** -- `man` pages
    * **src** -- Other utilities like `mysqlclient` and `pdfkit`.
* **logs** -- Various log files.
* **node_modules** -- ERPNext uses a colletion of `NodeJS` modules. The are installed here.
* **sites** -- The top level directory for all sites on the installation. `bench` can manage multiple sites in one environment. If you are running in a multi-tenant environment you will see more than one [site name] directory.
    * **[site name]** -- The name of the site. Usually is the same as the URI for the site.
        * **error-snapshots**
        * **locks**
        * **private** -- Private file attachments to various documents inside the user interface are stored on the filesystem here.
            * **backups** -- Backups for the site are stored here. See [3.4 Backups](backup.md "Backing up ERPNext")
        * **public** -- Public file attachments to various documents inside the user interface are stored on the filesystem here.
        * **task-logs**

### 3.1.2 Frappe Bench Commands

Administrators need to be comfortable with the frappe `bench` command structure. 

There is a [cheat sheet](https://frappe.io/docs/user/en/bench/resources/bench-commands-cheatsheet "Frappe Bench Commands Cheetsheet") available at the link below that is a good start.<br /><br />

Previous: [2.2 Getting Help](../introduction/help.md "Getting Help") | Next: [3.1.3 Wonderful World of git](git.md "The Wonderful World of git")
