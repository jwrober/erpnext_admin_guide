Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2.2 Installing Development Side by Side](install-dev "Installation of a Side by Side Development Environment") | Next: [3.3.3 Reverting to an Older Version](revert "Reverting to an Older Version")

## 3.3 Upgrading ERPNext

In this section we go over steps to upgrade ERPNext. One of the things that comes up very often on the [Discussion Forum](https://discuss.erpnext.com/ "ERPNext Discussion Forum") is upgrade issues. So besides installation issues, the admin guide would say that the second most often cries for help are from challenges related to upgrading ERPNext. What is interesting is in most cases the administrator is the one who caused their own issue because they didn't take the time to be prepared and get setup in a way to allow them plenty of flexibilty to upgrade in a safe environment.

What is this "flexibility"?  It's very simple: **ONLY UPGRADE IN A NON-PRODUCTION ENVIRONMENT FIRST.**

Yes, the admin guide purposefully put that in all caps with bold text to make a point. Who upgrades a production environment and breaks it because he didn't take the time to test out an upgrade in a lower level non-production environment! Your company's ERPNext installation is at the heart of its operations! Don't risk messing something up because you (as the administrator) didn't take the time to test out in a safe place where you have all the time in the world to fix before you upgrade production. Please read the section on environments in [3.2 Installing ERPNext](install "Installing ERPNext") and then read [3.2.2 Installation of a Side by Side Development Environment](install-dev "Installation of a Side by Side Development Environment") to get setup.

<a name="Major">&nbsp;</a>
### 3.3.1 Upgrading from one Major Version to Another

The developers of ERPNext use a three-numeral version system in this format `[major version].[minor version].[patch level]`. So an upgrade of one major version to another would be like going from v7.x to v8.x or a really big jump would be going from v7.x to v9.x.  There are a ton of things that can happen when doing a major upgrade! This is where doing work in a [non-production environment](install-dev "Installation of a Side by Side Development Environment") is really needed. The admin guide has NEVER seen anyone complete a major upgrade without issue. There are too many factors to consider.

First start with a [good full backup](backup#Full "Backing up ERPNext") of the development system and a [simple backup](backup#Simple "Backing up ERPNext") of the production system.
    
Assuming the stage environment is the same version as production (or very close), restore the production database to the stage environment. Before you run the commands below, ensure that the `encryption_key` value in  `sites/[site name]/site_config.json` from the production site is also in the stage `site_config.json`. Otherwise you will get an error on restart.

**NOTE**: For some reason the admin guide does not understand, `bench` does not handle relative paths very well. Be sure to fully qualify all of the path's you use for the `bench restore` command.

    cd erpnext-stg
    # restore the prod database snapshot taken, you will be prompted for the mysql root pwd
    bench --force restore \
      --with-public-files /home/erpnext/[prd bench name]/sites/[site name]/private/backups/[files.tar] \     
      --with-private-files /home/erpnext/[prd bench name]/sites/[site name]/private/backups/[private_files.tar] \
       /home/erpnext/[prd bench name]/sites/[site name]/private/backups/[sql.gz]
    
    # confirm the database schema matches the code, clear all cache and restart
    bench migrate
    bench clear-cache
    bench clear-website-cache
    bench restart

At this point, you should go into the stage environment user interface and ensure it looks and operates like the current production site. Run trough a few tests to ensure everything is working okay. Don't assume that the copy down operation completed above actually worked!

Once you are comfortable that the copy down procedure worked, now it's time to upgrade stage.

    bench update --upgrade
    bench clear-cache
    bench clear-website-cache
    bench restart

This is often when things go wrong. Refer to [3.3.4 Upgrade Troubleshooting](upgrade-trouble "Upgrade Troubleshooting") for some insight on troubleshooting an upgrade. If everything went fine and no errors were reported, then you will see something like this:

    ...
    Wrote js/print_format_v3.min.js - 23.39 KB
    Wrote css/erpnext.css - 8 KB
    Wrote js/erpnext-web.min.js - 3.73 KB
    Wrote js/erpnext.min.js - 137.7 KB
    Wrote js/item-dashboard.min.js - 7.91 KB
    ________________________________________________________________________________
    Bench: Deployment tool for Frappe and ERPNext (https://erpnext.org).
    Open source depends on your contributions, so please contribute bug reports, patches,
    fixes or cash and be a part of the community

Congratulations! Your non-production stage environment has been upgraded to the latest and greatest. Now you need to go into the user interface and test, test and test some more. Did we mention you need to test? Take the time to ensure that every feature of the system your company uses works as expected! Get some help from your fellow employees that are power users. The effort you take now will pay off in the long run.

Once all testing is finished, the upgrade of the production environment is the same commands as upgrading the non-production stage environment. Just replace `erpnext-stg` with `erpnext-prd` and you are all set. Don't forget to take a [full backup](backup#Full "Backing Up ERPNext") just in case something goes wrong.

    sudo su - erpnext
    cd erpnext-prd/
    bench update --upgrade
    [any special commands you need to fix issues from troubleshooting]
    bench clear-cache
    bench clear-website-cache
    bench restart

If you want to revert to the original code base, then [follow these instructions](revert "Reverting to an Older Version").

<a name="Minor">&nbsp;</a>
### 3.3.2 Upgrading from one minor version to another

The steps to upgrade from a minor version to another is very similar to the procedure to upgrade from one major version to another. The admin guide *recommends* that site administrators upgrade code once a month in production environments (passing through the non-production environment just like in major upgrades). This provides a few benefits:

* Your production environment will always be pretty close to the current code base.
* Security issues discovered in the frappe framework are keeping your business safe.
* Upgrades are less painful and require less troubleshooting as they often work much better than trying the major upgrade route.
* The changes to the software are smaller and so any re-training of your users will be easier.

To summarize the steps:

1. Take a [simple backup](backup#Simple "Backing up ERPNext") of the production database and a [full backup](backup#Full "Backing up ERPNext") of the stage environment.
1. [Restore](restore "Restoring from an ERPNext Backup") the production database to the stage environment.
1. Run `bench migrate`, `bench clear-cache`, `bench clear-website-cache`, and `bench restart` to get stage ready
1. Confirm that stage is operating like production.
1. Run `bench update` and then `bench restart` to update the stage environment to latest code.
1. Test, Test and Test some more. Leverage your power users.
1. Take a [simple and a full backup](backup "Backing up ERPNext") of the production database and environment.
1. Run `bench update` to update the production system to latest code.
1. Run `bench clear-cache`, `bench clear-website-cache`, and `bench restart` to get production ready
1. Get some coffee!<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2.2 Installing Development Side by Side](install-dev "Installation of a Side by Side Development Environment") | Next: [3.3.3 Reverting to an Older Version](revert "Reverting to an Older Version")
