Home: [Table of Contents](../ "Table of Contents") | Previous: [3.4 Backing Up ERPNext](backup "Backing Up ERPNext") | Next: [4 Setup](../setup/setup "Setup")

## 3.5 Restoring from a Previous Backup

Assuming you have a good [simple backup](backup#Simple "Backing Up ERPNext"), you can use these commands to restore the database and files. These commands also assume that you are not [reverting](revert "Reverting to an Older Version") back to a different code base.

**NOTE**: For some reason the admin guide does not understand, `bench` does not handle relative paths very well. Be sure to fully qualify all of the path's you use for the `bench restore` command.

    sudo su - erpnext
    cd [bench name]
    bench --force restore \
      --with-public-files /home/erpnext/[bench name]/sites/[site name]/private/backups/[files.tar] \          
      --with-private-files /home/erpnext/[bench name]/sites/[site name]/private/backups/[private-files.tar] \
      /home/erpnext/[bench name]/sites/[site name]/private/backups/[sql.gz file]

This should bring your system's database and files configuration back to the point in time the backup was taken.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [3.4 Backing Up ERPNext](backup "Backing Up ERPNext") | Next: [4 Setup](../setup/setup "Setup")
