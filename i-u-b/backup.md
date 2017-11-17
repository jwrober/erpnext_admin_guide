## 3.4 Backing Up ERPNext

Backing up ERPNext is pretty simple. There are two kinds of backups in the author's mind. A simple backup and a full backup. Let me explain.

A simple backup just backs up the database and files into `tar` files.  To accomplish this, simply run `bench backup` like this:

    sudo su - erpnext
    cd frappe-bench/
    bench backup --with files

`bench backup` will create a `tar.gz` file of the database and `tar` files of the public and private files in the `sites/[site name]/private/backups/` directory on the server. For example:

    [yyyymmdd]_[hhmmss]-[site name]-database.sql.gz
    [yyyymmdd]_[hhmmss]-[site name]-files.tar
    [yyyymmdd]_[hhmmss]-[site name]-private-files.tar

There is another level of backup that is not really discussed in the [Discussion Forums](https://discuss.erpnext.com/ "ERPNext Discussion Forums") and is what the author calls a **full backup**. The simple backup does not do anything with the code. There is no mechanism to revert to an older code base once `bench update` has been run. So when [Upgrading](upgrade.md "Upgrading ERPNext"), make sure to take a full backup like this:

    sudo su - erpnext
    # you should be in the root of the erpnext user home directory
    # take a full backup of the whole system
    tar -acvf erpnext-prd-backup-[yyyy-mm-dd].tar.bz2 frappe-bench/*

This will create a `tar.bz2` file in the `/home/erpnext/` directory. You can then follow the steps in [3.3.3 Reverting to an Older Version](revert.md "Reverting to an Older Version") to get back to a known good state.<br /><br />

Previous: [3.3.4 Upgrade Troubleshooting](upgrade-trouble.md "Upgrade Troubleshooting") | Next: [3.5 Restoring from a Previous Backup](restore.md "Restoring from a Previous Backup")
