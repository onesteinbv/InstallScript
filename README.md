# [Odoo](https://www.odoo.com "Odoo's Homepage") Install Script

This script is based on the install script from André Schenkels (https://github.com/aschenkels-ictstudio/openerp-install-scripts)
but goes a bit further and has been improved. This script will also give you the ability to define an xmlrpc_port in the .conf file that is generated under /etc/
This script can be safely used in a multi-odoo code base server because the default Odoo port is changed BEFORE the Odoo is started.

## Installation procedure

##### 0. Enable universe category

You have to enable universe category which contains python-pip package.
Open /etc/apt/sources.list using an editor, for example nano:

```
sudo nano /etc/apt/sources.list
```

then add  universe at the end of each line, like this:

```
deb http://archive.ubuntu.com/ubuntu bionic main universe
deb http://archive.ubuntu.com/ubuntu bionic-security main universe 
deb http://archive.ubuntu.com/ubuntu bionic-updates main universe
````
then run:

```
sudo apt update
```

##### 1. Download the script:
```
sudo wget https://raw.githubusercontent.com/onesteinbv/InstallScript/13_os_20.04/odoo_install.sh
```
##### 2. Modify the parameters as you wish.
There are a few things you can configure, this is the most used list:<br/>
```OE_USER``` will be the username for the system user.<br/>
```INSTALL_WKHTMLTOPDF``` set to ```False``` if you do not want to install Wkhtmltopdf, if you want to install it you should set it to ```True```.<br/>
```OE_PORT``` is the port where Odoo should run on, for example 8069.<br/>
```OE_VERSION``` is the Odoo version to install, for example ```13.0``` for Odoo V13.<br/>
```IS_ENTERPRISE``` will install the Enterprise version on top of ```13.0``` if you set it to ```True```, set it to ```False``` if you want the community version of Odoo 13.<br/>
```OE_SUPERADMIN``` is the master password for this Odoo installation.<br/>

#### 3. Make the script executable
```
sudo chmod +x odoo_install.sh
```
##### 4. Execute the script:
```
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo dpkg-reconfigure locales
sudo ./odoo_install.sh
```
