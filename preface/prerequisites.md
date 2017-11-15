## Prerequisites

To be proficient in the tasks that this book describes, the reader needs to have a good understanding of the following:

- Linux server administration (any distribution is fine)
    - Installation, patching, users, hardening for hosting externally, etc.
    - Getting around the operating system, running shell commands, editing files, etc.
- MySQL (or MariaDB) administration
    - The frappe `bench` utility does most of the work for the administrator, but having a good understanding of backups, restored, `innodb` file handling and other concepts is very important. The whole system lives in the database! This is the database that runs your business, so keep it managed.
- `nginx` administration
    - This book gives some aid and recipes for tasks, but understanding the underlying architecture of the web server will come in handy.
