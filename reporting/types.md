Home: [Table of Contents](../ "Table of Contents") | Previous: [21.1 Introduction](introduction "Reporting Introduction") | Next: [21.3 Installation of External BI Engine](install-bi "Installation of External BI Engine")

## 21.2 Type of Reporting in ERPNext

There are four types of reporting available for ERPNext. Three of them are them work great for non-programmers.

1. Internal JSON Based "Report Builder" Reports
1. Internal SQL "Query" Reports
1. Internal Python "Script" Reports
1. External Business Intelligence (BI) Engine based Reports.

Numbers 1, 2 and 4 are great for non-programmer type administrators. Python "Script" based reports are great and integrated into the environment, however you have to have a understanding of python, the frappe framework and programming in order to create these kinds of reports. They also need to be installed into a "custom application" so that upgrades to ERPNext don't impact your changes. These kinds of reports are out of the scope of the admin guide.

The ERPNext User Manual has another good overview of the three internal reporting types here:

<https://erpnext.org/docs/user/manual/en/customize-erpnext/articles/making-custom-reports-in-erpnext>

Here are links to documentation for the three internal reporting types:

1. Report Builder Reports - ERPNext has not created any. See below.
1. Query Reports - <https://frappe.io/docs/user/en/guides/reports-and-printing/how-to-make-query-report.html>
1. Script Reports - <https://frappe.io/docs/user/en/guides/reports-and-printing/how-to-make-script-reports.html>

To get a listing of all of the reports installed in your environment, search for the "**Report List**" in the quick search bar at the top of the Desk.

<a name="rb">&nbsp;</a>
### 21.2.1 Report Builder Reports

These are by far the easiest reports to create. Open the document list of the doctype you wish to create a simple report for. From the left menu, click **Reports** and then **Report Builder**.

You can then:
- Pick Columns
- Set the Sort Order
- Show a Totals Row

#### Pick Columns

This button allows you to select the field from the doctype that you want to report on.

#### Set the Sort Order

You can setup a quick default sort order for the various columns(s) in the report.

#### Show a Totals Row

If the report has number in it, such as an accounting report, then adding a totals row to the report might make sense.

When finished, click **Save** to save the report.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [21.1 Introduction](introduction "Reporting Introduction") | Next: [21.3 Installation of External BI Engine](install-bi "Installation of External BI Engine")
