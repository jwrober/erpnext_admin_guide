Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2 Installing ERPNext](install "Installing ERPNext") | Next: [3.2.2 Installing Development Side by Side](install-dev "Installation of a Side by Side Development Environment")

### 3.2.1 Installation Troubleshooting

There are a number of things that can go wrong with an installation.

#### 3.2.1.1 Install.py - General Error

Sometimes `install.py` throws an error that is hard to understand or read. The first thing to do is read that last few ansible script sections in the erpnext-install.log file that you captured during installation:

    less erpnext-install.log

If the error is not obvious, then the admin guide recommends that you restart `install.py` again with the same command line arguments and see what happens. Often times `install.py` is able to get past the error on a second run and you don't have to do anything. If you get the error again at the same place, then it will need more attention.

#### 3.2.1.2 Install.py - Unexpected Exception: Module object has no attribute: SSL___SL___INIT

This installation error is caused if you have an out of date `pyOpenSSL` module installed on the server. To correct, uninstall and reinstall `pyOpenSSL`:

    sudo pip uninstall pyOpenSSL
    sudo pip install pyOpenSSL

and then re-run `install.py` again with the same command line arguments.

#### 3.2.1.3 Nginx not listening on port 80 after installation

Go to the `[bench name]` folder that was used during install and run `bench start` and see what errors crop up. Correct them and then restart the server. Run `bench start` again to see if any other errors come up. If not then run `bench update` to finalize settings. Another tip is to become the `root` user and take a look at the `/var/log/nginx/error.log` file and see what is in there.

Confirm by running

    sudo netstat -tulpn | grep nginx

and see if the server is running.

This issue also happens if the `bench` was not setup for production mode.  The `erpnext` user will need to be in the `sudo` group first. If it is, then run this command as `erpnext` user to setup the `bench` for production mode:

    sudo bench setup production --yes erpnext

You should see `nginx` running after this command is run.<br /><br />

Home: [Table of Contents](../ "Table of Contents") | Previous: [3.2 Installing ERPNext](install "Installing ERPNext") | Next: [3.2.2 Installing Development Side by Side](install-dev "Installation of a Side by Side Development Environment")
