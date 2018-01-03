Home: [Table of Contents](../ "Table of Contents") | Previous: [3.3.3 Reverting to an Older Version](revert "Reverting to an Older Version") | Next: [3.4 Backing Up ERPNext](backup "Backing Up ERPNext")

### 3.3.4 Upgrade Troubleshooting

There are a number of things that can go wrong during an upgrade. The best thing to do is to ensure that you did indeed take a good [simple](backup#Simple) and [full](backup#Full) backup of the environment before you started. Second thing to do is capture the `python` stack trace in its entirety and open a new topic on the [discussion forum](https://discuss.erpnext.com/c/bench). The more specific you are in the forum topic the better support you will get from the community.  Things that should be mentioned in the post:

* Current version of ERPNext and Frappe Framework
* Version of each attempting to upgrade to (don't just say current, explicitly state the version number)
* Operating system environment and version
* List of any custom apps installed, including your own

These things will help the community to better understand your issue. You might have discovered a defect in the software and so a [github issue](https://github.com/frappe/erpnext/issues) will need to be opened. This is why the admin guide stresses the importance of upgrading in a non-production environment first. That way your users will not be impacted by a delay to figure out an issue with an upgrade. Especially if there is a defect, you will have to wait to get it fixed (or fix it yourself and post a pull request) and then wait for a release to master branch to occur to try again.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [3.3.3 Reverting to an Older Version](revert "Reverting to an Older Version") | Next: [3.4 Backing Up ERPNext](backup "Backing Up ERPNext")
