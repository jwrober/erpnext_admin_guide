## 3.5 Restoring from a Previous Backup

Assuming you have a good [simple backup](backup.md "Backing Up ERPNext"), you can use these commands to restore the database and files. These commands also assume that you are not [reverting](revert.md "Reverting to an Older Version") back to a different code base.

    sudo su - erpnext
    cd frappe-bench/
    bench --force restore                                                          \
        --with-public-files sites/[site name]/private/backups/[files.tar]          \
        --with-private-files sites/[site name]/private/backups/[private-files.tar] \
        sites/[site name]/private/backups/[sql.gz file]

This should bring your system's database and files configuration back to the point in time the backup was taken.<br /><br />

Previous: [3.4 Backing Up ERPNext](backup.md "Backing Up ERPNext") | Next: [4 Setup](../setup/setup.md "Setup")
