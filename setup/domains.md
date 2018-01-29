Home: [Table of Contents](../ "Table of Contents") | Previous: [4.1 Setup](setup "Setup Wizard") | Next: [5 Explore > Setup](../explore-setup/setup "Explore > Setup") 

## 4.2 Domains

As of version 10.x of ERPNext, these are the available domains:
* Agriculture (beta)
* Distribution
* Education
* Healthcare (beta)
* Manufacturing
* Non Profit (beta)
* Retail
* Services

### 4.2.1 Agriculture

The agriculture domain is used for businesses that operate as agricultural companies such as farms, ranches, etc. This is a very new domain to the ERPNext platform and has not been documented very well to date.

Please see ERPNext documentation on this domain: <https://erpnext.org/docs/user/manual/en/agriculture>

The setup wizard will add the following desktop icons:
* Agriculture Task
* Crop
* Crop Cycle
* Fertilizer
* Item
* Land Unit
* Disease
* Plant Analysis
* Soil Analysis
* Soil Texture
* Task
* Water Analysis
* Weather

The setup wizard will add the following user roles:
* Agriculture Manager
* Agriculture User

The setup wizard will enable the following modules:
* Agriculture

### 4.2.2 Distribution Domain

The distribution domain is for companies and move product in some manner. This can be a retail establishment, but there is a dedicated domain for that. Distribution companies are often operate in a wholesale environment and don't need point of sale (POS) type functionality, but do need to maintain stock and track sales and customers.

The setup wizard will add the following desktop icons:
* Item
* Customer
* Supplier
* Lead
* Sales Order
* Purchase Order
* Task
* Sales Invoice
* CRM
* ToDo

The setup wizard will add the following user roles:
* None other than the standard out of box ones

The setup wizard will enable the following modules:
* None other than the standard out of box ones

### 4.2.3 Education Domain

The education domain is for organizations that operate some kind of school or need to track students and other things for "classes". This domain was recently renamed from Schools to Education.

Please see ERPNext documentation on this domain: <https://erpnext.org/docs/user/manual/en/education>

The setup wizard will add the following desktop icons:
* Student
* Program
* Course
* Student Group
* Instructor
* Fees
* Task
* ToDo
* Education
* Student Attendance Tool
* Student Applicant

The setup wizard will add the following user roles:
* Student
* Instructor
* Academics User
* Education Manager

The setup wizard will enable the following modules:
* Education

### 4.2.4 Healthcare Domain

The healthcare domain is for companies that run clinics or other healthcare facilities that need a electronic medical record (EMR) system. This is a very new domain to the ERPNext platform and has not been documented very well to date.

Please see ERPNext documentation on this domain: <https://erpnext.org/docs/user/manual/en/healthcare>

The setup wizard will add the following desktop icons:
* Patient
* Patient Appointment
* Consultation
* Lab Test
* Healthcare
* Accounts
* Buying
* Stock
* HR
* ToDo

The setup wizard will add the following user roles:
* Healthcare Administrator
* LabTest Approver
* Laboratory User
* Nursing User
* Physician
* Patient

The setup wizard will enable the following modules:
* None other than the standard out of box ones

The setup wizard does customize the Sales Invoice DocType with a link to the Patient Appointment DocType to track the billing to the appointment for a patient.

### 4.2.5 Manufacturing Domain

The manufacturing domain is for companies that "make" things. There is a huge list of potential manufacturing companies out there, so the Admin guide is not going to attempt to give an exhaustive list. As as administrator for your organization or client, you will know if you need the manufacturing domain.

Please see ERPNext documentation on this domain: <https://erpnext.org/docs/user/manual/en/manufacturing>

The setup wizard will add the following desktop icons:
* Item
* BOM (Bill of Materials)
* Customer
* Supplier
* Sales Order
* Purchase Order
* Production Order
* Task
* Accounts
* HR
* ToDo

The setup wizard will add the following user roles:
* None other than the standard out of the box ones

The setup wizard will enable the following modules:
* None other than the standard out of the box ones

The setup wizard does customize the Item DocType with a field named "manufacturing" that is collapsible and depends on the value for the "is_stock_item" field. In the manufacturing domain, maintaining the supply chain is one of the most important aspects of the business. Understanding the difference between what is "in stock" and available for shipping or fulfillment and what is and assembly component are very  important. This field helps with that differentiation.

The setup wizard also adjusts the default [stock settings](../explore/setup/stock/stock-settings "Stock Settings") so that "show barcode" is always shown on Items in the database.

Lastly, the setup wizard sets the default portal role to "Customer".

### 4.2.6 Non-Profit Domain

The non-profit domain is for organizations that operate as a special jurisdiction specific non-profit (non-taxable) entity. These are very special organizations that have much different needs that typical for-profit companies. The biggest difference is the need to track members, donors, volunteers, grants and other accounting specifics.

Please see ERPNext documentation on this domain: <https://erpnext.org/docs/user/manual/en/non_profit>

The setup wizard will add the following desktop icons:
* Non Profit
* Member
* Donor
* Volunteer
* Grant Application
* Accounts
* Buying
* HR
* ToDO

The setup wizard will add the following user roles:
* Non Profit Manager
* Non Profit Member
* Non Profit Portal User

The setup wizard will enable the following modules:
* Non Profit

The setup wizard sets the default portal role to "Non Profit Manager".

### 4.2.7 Retail Domain

The retail domain is for companies that sell things at "retail". This is different than organizations the operate in the manufacturing or distribution domains. These companies operate in the "pre-retail" phase of production. Non-Profit organization quite often sell items "at retail" as part of their operations.

The setup wizard will add the following desktop icons:
* POS (Point of Sale)
* Item
* Customer
* Sales Invoice
* Purchase Order
* Accounts
* Task
* ToDo

The setup wizard will add the following user roles:
* None other than the standard out of the box ones

The setup wizard will enable the following modules:
* None other than the standard out of the box ones

The setup wizard adjusts the default [stock settings](../explore/setup/stock/stock-settings "Stock Settings") so that "show barcode" is always shown on Items in the database.

The setup wizard sets the default portal role to "Customer".

### 4.2.8 Service Domain

The services domain is for organizations that conduct professional services (i.e. Lawyers, Consultants). A lot of organizations, especially retail companies also have a services arm. This domain is often combined with retail, but not always.

The setup wizard will add the following desktop icons:
* Project
* Timesheet
* Customer
* Sales Order
* Sales Invoice
* CRM (Customer Relationship Management)
* Task
* Expense Claim
* Employee
* HR
* ToDo

The setup wizard will add the following user roles:
* None other than the standard out of the box ones

The setup wizard will enable the following modules:
* None other than the standard out of the box ones

The setup wizard adjusts the default [stock settings](../explore/setup/stock/stock-settings "Stock Settings") so that "show barcode" is not always shown on Items in the database.

The setup wizard sets the default portal role to "Customer".<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [4.1 Setup](setup "Setup Wizard") | Next: [5 Explore > Setup](../explore-setup/setup "Explore > Setup")
