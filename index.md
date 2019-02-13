# ownCloud quickstart (work in progress)

ownCloud is client/server software for file syncing and sharing. It enables you to manage data on your own private cloud server, and share with 
multiple client users on multiple devices in a safe and secure way. 

ownCloud is available in the following installation options: 

| Component      | Installation Option | 
| -------------- | ------------------- |
| Server         | Linux, Docker, virtual appliance, or hosted service |
| Desktop client | MacOS, Windows, or Linux | 
| Mobile app     | iOS or Android | 

This quickstart explains how administrators can install the open source ownCloud server (Community Edition) on Linux, and how users can connect 
to an ownCloud server from different client devices. 

## Install and configure your ownCloud server
The free and open source ownCloud server manages your files and data and controls user access. 

### Before you begin

You must ensure that your web server host has the following software installed:
- Linux or Docker 
- Apache web server
- Database (for example, MySQL or SQLite)
- PHP runtime

For details on recommended software versions, see <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html#officially-recommended-supported-options" target="_blank">System Requirements</a>.
For guidelines on deploying ownCloud in an open source LAMP stack, see <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/deployment_recommendations.html" target="_blank">Deployment Recommendations</a>. 

### Install the ownCloud server
  1. Ensure that all the prerequisites and required packages have been installed for your system:
   - <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#prerequisites-label" target="_blank">Prerequisites</a>
   - <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#install-the-required-packages" target="_blank">Install the Required Packages</a>
  2. Download the `.tar` or `.zip` archive of the latest ownCloud server version from https://owncloud.org/download. 
  3. Extract the archive contents on your machine. For example:
```
tar -xjf owncloud-x.y.z.tar.bz2
unzip owncloud-x.y.z.zip
```   
  4. Copy the `owncloud` directory to your the Apache root directory:
```
cp -r owncloud /var/www
``` 
     
### Configure your Apache web server
  1. Create the following file: 
```
/etc/apache2/sites-available/owncloud.conf
```
  2. Add the following content: 
  
    Alias /owncloud "/var/www/owncloud/"
     <Directory /var/www/owncloud/>
       Options +FollowSymlinks
       AllowOverride All
      <IfModule mod_dav.c>
        Dav off
      </IfModule>
      SetEnv HOME /var/www/owncloud
      SetEnv HTTP_HOME /var/www/owncloud
     </Directory>     
  3. Create a symlink to `/etc/apache2/sites-enabled`:
```
ln -s /etc/apache2/sites-available/owncloud.conf /etc/apache2/sites-enabled/owncloud.conf
```
  4. Restart your Apache web server when finished your configuration. For example:
```  
sudo service apache2 restart 
```    
For more details, see: 
 * <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#apache-configuration-label" target="_blank">Additional Apache configurations</a>
 * <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html#enable-ssl" target="_blank">Enable SSL</a>

 
### Run the ownCloud installation wizard or command
After restarting Apache, you must complete your installation by running the ownCloud graphical installation wizard or by using the `occ` command. 

To use the graphical Installation Wizard, see The Installation Wizard. To use occ, see Command Line Installation. 


### Enable users to connect to the ownCloud server on a custom port
By default, users connect to the ownCloud server IP address only. You can change this to use the server IP address and a custom port by editing your Apache web 
server's configuration:
  1. Edit the following file:
```
/etc/apache2/ports.conf
```  
  2. Find the following line:
```
Listen 80
```  
  3. Change it to use the IP address and port. For example:  
```
Listen 192.0.2.4:8080
```
  4. Restart your Apache web server. For example:
```  
sudo service apache2 restart 
```    
  5. Enter the server IP address and port in your browser to test the connection. For example: 
```  
http://192.0.2.4:8080
```    
  
For more details, see your Apache web server documentation.  


### Add a user account
When logged in as administrator, you can add new user accounts on the **User management** page in the ownCloud Web UI:
  1. Enter the new user name and initial password.
  2. Assign groups memberships (optional).
  3. Click **Create** to add the user account.
  
_**Note**: If you selected **Send email to new user** in the control panel in the left sidebar, you can enter the new user’s email address to 
automatically send an email with login details._

For more details, see <a href="https://doc.owncloud.org/server/10.0/admin_manual/configuration/user/user_configuration.html" target="_blank">User management</a>.  


## Connect to an ownCloud server from a client device
You can connect to an ownCloud server on multiple client devices (for example, mobile app, desktop client, or browser). 

### Connect to an ownCloud server on a desktop client
  1. Download the free client software for your platform from 
     https://owncloud.org/download
  2. Run the ownCloud Setup Wizard to install.
  3. Enter the **Server Address** URL (for example, https://demo.owncloud.org), and click **Next**.
  4. Enter your **Username**/**Password** (in this case, **demo**/**demo**), and click **Next**.
  5. Click Connect and wait for a few seconds for your files to sync.
  6. Click the ellipsis button on the right to manage your files (for example, select **Open folder**, create a new Music folder, and select **Force sync now**).
  
  
Alternatively, on your desktop, you can also open a browser, and enter an ownCloud server URL address to connect. 


### Connect to an ownCloud server on a mobile app client
  1. Download the app from the Google Play Store or Apple App Store.
  2. Open the app, and enter your server URL address (for example, https://demo.owncloud.org)
  3. Enter your **Username**/**Password** (in this case, **demo**/**demo**).
  4. View the data available on the server (for example, Photos or Documents)
  5. Click **+** to upload a sample photo or file.  
  
For details on supported client platforms, 
see <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html#officially-recommended-supported-options" target="_blank">System Requirements</a>.

 