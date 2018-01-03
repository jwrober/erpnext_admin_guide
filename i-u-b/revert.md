Home: [Table of Contents](../ "Table of Contents") | Previous [3.2 Upgrading ERPNext](upgrade "Upgrading ERPNext") | Next: [3.3.4 Upgrade Troubleshooting](upgrade-trouble "Upgrade Troubleshooting")

### 3.3.3 Reverting to an Older Version

ERPNext is not really designed to be reverted or back-ported. However, with some planning it can be done. The main trick is to have good backups. Refer to [3.4 Backing up ERPNext](backup "Backing up ERPNext"). This is the primary reason why we backup all sites before we do an [upgrade](upgrade "Upgrading ERPNext"). With planning and a good backup, you can restore the database to match the known good code base.

Assuming the steps to take a **full backup** were completed from [3.4 Backing up ERPNext](backup#Full "Backing up ERPNext"), follow these steps to revert to the backed up state.

**NOTE**: For some reason the admin guide does not understand, `bench` does not handle relative paths very well. Be sure to fully qualify all of the path's you use for the `bench restore` command.

    sudo su - erpnext
    # you should be in the root of the erpnext user home directory
    rm -Rf [bench name]
    tar -xvf erp-prd-backup-[yyyy-mm-dd].tar.bz2
    cd [bench name]
    
    # find the latest backup files in sites/[site name]/private/backups/
    # you will be prompted for the mysql pwd
    bench --force restore \
        /home/erpnext/[bench name]/sites/[site name]/private/backups/[sql.gz file]
    bench migrate
    bench clear-cache
    bench clear-website-cache
    bench restart

Following these commands will essentially wipe the old version completely and restore what was taken in the full backup to production.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous [3.2 Upgrading ERPNext](upgrade "Upgrading ERPNext") | Next: [3.3.4 Upgrade Troubleshooting](upgrade-trouble "Upgrade Troubleshooting")
