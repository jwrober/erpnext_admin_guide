### 3.1.3 The Wonderful World of git

`git` is a software code revision/version control system. The popular GitHub website hosts `git` repositories online for projects such as ERPNext and this administrators guide to reside in. Administrators for companies that want to host thier own repositories can do so, especially those that do not want thier code public.

As mentioned before, ERPNext is hosted in an GitHub repository at [https://github.com/frappe/erpnext](https://github.com/frappe/erpnext "ERPNext GitHub Repo"). The Frappe `bench` system will download the ERPNext repository and others as needed with a `clone ` operation. The `bench update` command, redownloads the latest code and upgrades ERPNext to the most current version. See [3.3 Upgrading ERPNext](upgrade.md "Upgrading ERPNext").

An administrator needs to be comfortable with `git` as there are going to be instances where the code needs to be reverted or otherwise edited. Developers of ERPNext will certainly need to be proficient in `git` so that they can contribute to the project or write custom modules.

Here are some places to go gain some knowledge on `git`:
* There is a good cheat sheet at [git-tower](https://www.git-tower.com/blog/git-cheat-sheet "Git Cheat Sheet")<br /><br />
* There is the official documentation at [git-scm](https://git-scm.com/docs "Git SCM Documentation")<br /><br />

Previous: [3 Frappe Bench](bench.md "Frappe Bench") | Next: [3.1.4 Wonderful World of nginx](nginx.md "The Wonderful World of nginx")
