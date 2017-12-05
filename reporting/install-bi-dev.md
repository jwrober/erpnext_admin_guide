Home: [Table of Contents](../README "Table of Contents") | Previous: [21.3 Installation of a Business Intelligence Engine](install-bi "Installation of a Business Intelligence Engine") | Next:

### 21.4 Installation of BI Development Environment

Most people code in the [Eclipse IDE](https://en.wikipedia.org/wiki/Eclipse_(software) "Eclipse Software on WikiPedia"). The admin guide recommends that coding of reports also occur in the Eclipse IDE. These are the reasons:

* The native Jasper Reports Studio that you download from the JasperSoft web site is a repackaged Eclipse IDE with only a single module enabled.
* By using a generic installation of the Eclipse IDE you can not only download and install the Jasper Reports Studio, but also modules to support giving back to the ERPNext community and to this administrator's guide.

Start by downloading the archive file (`zip` or `tar.gz`) of the "Eclipse IDE for JavaScript and Web Developers" from this web site: <http://www.eclipse.org/downloads/packages/release/Neon/3>.

**NOTE:** Eclipse Neon is not the latest version of the Eclipse IDE. However, at this time the JasperReports Studio module only supports Neon (v4.6) and not the latest Oxygen (v4.7) release. See the [release notes](https://community.jaspersoft.com/project/jaspersoft-studio/releases "JasperSoft Studio Releases"). Notice the bullet item "*RCP version is now based on Eclipse 4.6.3 platform*". When a future release comes out that supports RCP 4.7.x, then we can upgrade to Eclipse Oxygen.

Once you have downloaded the IDE software compressed archive. Uncompress it to a directory of your choice. The admin guide recommends something simple like `C:\tools\eclipse-4.6-neon` for Windows machines or `~/tools/eclipse-4.6-neon` on MacOS or Linux.

When finished, open the IDE:
* Windows - run `eclipse.exe`
* MacOS - run `Eclipse.app/Contents/MacOS/eclipse`
* Linux - run `eclipse/eclipse`

From the Welcome page, click to **Launch the Eclipse Marketplace**. Find and install the following:

* Jaspersoft Studio
* EGit - Git Integration for Eclipse 4.6.0
* GitHub Flavored Markdown Viewer
* GitHub Extensions
* Markdown Text Editor
* PyDev - Python IDE for Eclipse

After a restart of Eclipse, open the report design perspective.

> Window > Perspective > Open Perspective > Other

Select "Report Design" from the list of perspectives.

Now you are ready to build some reports! Read the [documentation](https://community.jaspersoft.com/project/jaspersoft-studio/resources) online.


Home: [Table of Contents](../README "Table of Contents") | Previous: [21.3 Installation of a Business Intelligence Engine](install-bi "Installation of a Business Intelligence Engine") | Next: 
 