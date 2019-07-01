# Readme / Index

This is the ERPNext Administrator's Guide. All content in this guide is generated in markdown (MD) language. The purpose of this guide is to provide self-hosters of the [ERPNext](https://erpnext.org "ERPNext Website") system a place to capture tips and tricks on administering this complex platform.

If you would like to contribute to the maintenance of this guide, please PM me from the [ERPNext Discussion Forum](https://discuss.erpnext.com/) to get added to the repo. I go by the handle `james_robertson` there. Please read the [Contributing Guidelines](CONTRIBUTING).

![GPLv3 Logo](https://www.gnu.org/graphics/gplv3-127x51.png)<br />
This work is licensed under the GNU GENERAL PUBLIC LICENSE v3. Same as [ERPNext](https://github.com/frappe/erpnext "ERPNext GitHub Repo").

Read this guide online at <https://jwrober.github.io/erpnext_admin_guide/>

The GitHub repository is at <https://github.com/jwrober/erpnext_admin_guide>

Next: [1.1 Foreword](preface/foreword "Foreword")

## Table of Contents

* 1 Preface
    * 1.1 [Foreword](preface/foreword "Foreword")
    * 1.2 [Audience](preface/audience "Audience")
    * 1.3 [Prerequisites](preface/prerequisites "Prereguisites")
    * 1.4 [Typography](preface/typography "Typography")
* 2 Introduction
    * 2.1 [Overview of ERPNext](introduction/overview "Overview of ERPNext")
    * 2.2 [Getting Help](introduction/help "Getting Help")
* 3 ERPNext Installation, Upgrades, and Backups (I-U-B)
    * 3.1 [Frappe Bench](i-u-b/bench)
        * 3.1.1 [Operating Envrionment](i-u-b/bench#OpEnv)
        * 3.1.2 [Frappe Bench Commands](i-u-b/bench#Cmd)
        * 3.1.3 [The Wonderful World of git](i-u-b/git)
        * 3.1.4 [The Wonderful World of nginx](i-u-b/nginx)
        * 3.1.5 [Software Packages Installed](i-u-b/software)
    * 3.2 [Installing ERPNext](i-u-b/install)
        * 3.2.1 [Installation Troubleshooting](i-u-b/install-trouble)
        * 3.2.2 [Installation of a Side by Side Development Environment](i-u-b/install-dev)
    * 3.3 [Upgrading ERPNext](i-u-b/upgrade)
        * 3.3.1 [Upgrading from one Major Version to Another](i-u-b/upgrade#Major)
        * 3.3.2 [Upgrading from one Minor Version to Another](i-u-b/upgrade#Minor)
        * 3.3.3 [Reverting to an older version](i-u-b/revert)
        * 3.3.4 [Upgrade Troubleshooting](i-u-b/upgrade-trouble)
    * 3.4 [Backing Up ERPNext](i-u-b/backup)
    * 3.5 [Restoring from a Previous Backup](i-u-b/restore)
* 4 Setup
    * 4.1 [The Setup Wizard](setup/setup)
    * 4.2 [Domans](setup/domains)
* 5 Explore > Setup > Users
    * 5.1 User
    * 5.2 Role
    * 5.3 Role Profile
    * 5.x Future Placements
    * 5.20 User Procedures
        * 5.20.1 Setup a System User
        * 5.20.2 Setup a Website User
    * 5.21 User Recipes
    * 5.22 User Troubleshooting
 * 6 Explore > Setup > Permissions
    * 6.1 Role Permissions Manager
    * 6.2 Show / Hide Modules
    * 6.3 Role Permission for Page and Report
    * 6.4 Permitted Documents for User
    * 6.5 Document Share Report
    * 6.x Future Placements
    * 6.20 Permissions Procedures
    * 6.21 Permissions Recipes
    * 6.22 Permissions Troubleshooting
 * 7 Explore > Setup > Settings
    * 7.1 System Settings
    * 7.2 Error Log
    * 7.3 Domain Settings
    * 7.4 Global Settings
* 8 Explore > Setup > Data
    * 8.1 Import / Export Data
    * 8.2 Naming Series
    * 8.3 Bulk Rename
    * 8.4 Bulk Update
    * 8.5 Download Backups
    * 8.6 Deleted Documents
    * 8.x Future Placements
    * 8.20 Data Procedures
    * 8.21 Data Recipes
    * 8.22 Data Troubleshooting
* 9 Explore > Setup > Email
    * 9.1 Email Account
    * 9.2 Email Domain
    * 9.3 Email Alert
    * 9.4 Standard Reply
    * 9.5 Auto Email Report
    * 9.6 Feedback Trigger
    * 9.7 Email Digest
    * 9.8 SMS Setings
    * 9.x Future Placements
    * 9.20 Email Procedures
    * 9.21 Email Recipes
    * 9.22 Email Troubleshooting
* 10 Explore > Setup > Printing
    * 10.1 Print Format Builder
    * 10.2 Print Settings
    * 10.3 Print Format
    * 10.4 Print Style
    * 10.5 Letter Head
    * 10.6 Print Heading
    * 10.7 Address Template
    * 10.8 Terms and Conditions
    * 10.x Future Placements
    * 10.20 Printing Procedures
    * 10.21 Printing Recipes
    * 10.22 Printing Troubleshooting
* 11 Explore > Setup > Workflow
    * 11.1 Workflow
    * 11.2 Workflow State
    * 11.3 Workflow Action
    * 11.x Future Placements
    * 11.20 Workflow Procedures
    * 11.21 Workflow Recipes
    * 11.22 Workflow Troubleshooting
* 12 Explore > Setup > Customize
    * 12.1 Customize Form
    * 12.2 Custom Field
    * 12.3 Custom Translations
    * 12.4 Custom Script
    * 12.5 DocType
    * 12.6 Custom Tags
    * 12.7 Authorization Rule
    * 12.8 Email Notifications
    * 12.x Future Placements
    * 12.20 Customize Procedures
    * 12.21 Customize Recipes
    * 12.22 Customize Troubleshooting
* 13 Explore > Setup > Applications
    * 13.1 Application Installer
* 14 Explore > Setup > Website
    * 14.1 Website Settings
    * 14.2 Website Theme
    * 14.3 Website Script
    * 14.4 About Us Settings
    * 14.5 Contact Us Settings
    * 14.x Future Placements
    * 14.20 Website Procedures
    * 14.21 Website Recipes
    * 14.22 Website Troubleshooting
* 15 Explore > Setup > Accounts
    * 15.1 Accounts Settings
    * 15.2 Fiscal Year
    * 15.3 Currency
    * 15.4 Currency Exchange
    * 15.5 Payment Gateway Account
    * 15.6 POS Settings
    * 15.7 Point-of-Sale Profile
    * 15.8 Terms and Conditions Template
    * 15.9 Mode of Payment
    * 15.x Future Placements
    * 15.20 Accounts Procedures
    * 15.21 Accounts Recipes
    * 15.22 Accounts Troubleshooting
* 16 Explore > Setup > Stock
    * 16.1 Stock Settings
    * 16.2 Warehouse
    * 16.3 Unit of Measure
    * 16.4 Item Attribute
    * 16.5 Brand
    * 16.6 Item Variant Settings
    * 16.x Future Placements
    * 16.20 Stock Procedures
    * 16.21 Stock Recipes
    * 16.22 Stock Troubleshooting
* 17 Explore > Setup > Selling
    * 17.1 Selling Settings
    * 17.2 Campaign
    * 17.3 Terms and Conditions Template
    * 17.4 Sales Taxes and Charges Template
    * 17.5 Industry Type
    * 17.x Future Placements
    * 17.20 Selling Procedures
    * 17.21 Selling Recipes
    * 17.22 Selling Troubleshooting
* 18 Explore > Setup > Buying
    * 18.1 Buying Settings
    * 18.2 Terms and Conditions Template
    * 18.3 Purchase Taxes and Charges Template
    * 18.x Future Placements
    * 18.20 Buying Procedures
    * 18.21 Buying Recipes
    * 18.22 Buying Troubleshooting
* 19 Explore > Setup > Human Resources
    * 19.1 HR Settings
    * 19.2 Employment Type
    * 19.3 Branch
    * 19.4 Department
    * 19.5 Designation
    * 19.6 Daily Work Summary Settings
    * 19.x Future Placements
    * 19.20 Human Resources Procedures
    * 19.21 Human Resources Recipes
    * 19.22 Human Resources Troubleshooting
* 20 Explore > Integrations
    * 20.1 Payments
        * 20.1.1 Stripe Settings
        * 20.1.2 PayPal Settings
        * 20.1.3 Razorpay Settings
    * 20.2 Backup
        * 20.2.1 Dropbox Settings
        * 20.2.2 S3 Backup Settings
    * 20.3 Authentication
        * 20.3.1 Social Login Keys
        * 20.3.2 LDAP Settings
        * 20.3.3 OAuth Client
        * 20.3.4 OAuth Provider Settings
    * 20.4 External Documents
        * 20.4.1 GSuite Settings
        * 20.4.2 GSuite Templates
        * 20.4.3 Webhook
    * 20.5 Maps
        * 20.5.1 Google Maps
* 21 Reporting
    * [21.1 Introduction](reporting/introduction "Reporting Introduction")
    * [21.2 Types of Reporting](reporting/types "Types of Reporting")
        * [21.2.1 Internal Report Builder Reports](reporting/types#rb "Internal Report Builder Reports")
    * [21.3 Installation of External BI Engine](reporting/install-bi "Installation of External Reporting Engine")
    * [21.4 Installation of BI Development Environment](reporting/install-bi-dev "Installation of BI Dev Environment")

Now that you have read to the bottom of the current table of contents, you will notice that there are no entries for the following modules:

* Accounts
* Agriculture
* Assets
* Buying
* CRM
* Contacts
* Education
* Health Care
* Human Resources
* Maintenance
* Manufacturing
* Non Profit
* Projects
* Selling
* Stock
* Support
* Tools
* Website

We will work on those at a future date! As you can see, there is a lot to fill in yet.<br /><br />

Next: [1.1 Foreword](preface/foreword "Foreword")
