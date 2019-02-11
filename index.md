# ownCloud quickstart (work in progress)

ownCloud is client/server software for file syncing and sharing. It enables you to manage data on your own private cloud server, and share with 
multiple client users and devices in a safe and secure way. 

ownCloud is available as a server on-premises (Linux, Docker, or virtual appliance), or as a hosted Cloud service. ownCloud client options include desktop 
(MacOS, Windows, or Linux), or mobile app (iOS or Android). For more details, see <a href="https://owncloud.org/download/" target="_blank">installation options</a>.

This quickstart guide explains how administrators can install the free and open source ownCloud server (Community Edition) on Linux, and how users can connect 
to an ownCloud server on client devices. 

## Install and set up your ownCloud server
The free and open source ownCloud server manages your files and data and controls user access. 

### Before you begin

You must ensure that your web server host has the following software installed:
- Linux or Docker 
- Apache web server
- PHP runtime
- Database (for example, MySQL or SQLite)

For details on recommended software versions, see <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html#officially-recommended-supported-options" target="_blank">System Requirements</a>.

### Install and configure the ownCloud server
  1. Download the free server sofware from:
      https://owncloud.org/download/
  2. Unzip the tar file...
  3. Upload the following file to your web host...
  4. ...


For more details, see [installation instructions](https://doc.owncloud.org/server/10.0/admin_manual/installation/). 

### Enable users to connect using ownCloud server IP address and custom port
By default, ... You can change to the server IP address and custom port (for example, `8080`) by editing your Apache web server's configuration:
  1. Edit the following file: `/etc/apache2/ports.conf`.
  2. Find the `Listen 80` line.
  3. Change it to `Listen <IP_ADDRESS>:8080`  
  
For more details, see you Apache web server documentation.  
For more details, see https://www.ostechnix.com/how-to-change-apache-ftp-and-ssh-default-port-to-a-custom-port-part-1/


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
     https://owncloud.org/download/
  2. Run the ownCloud Setup Wizard to install.
  3. Enter the Server Address URL (for example, https://demo.owncloud.org), and click Next.
  4. Enter your Username/Password (in this case, demo/demo), and click Next.
  5. Click Connect and wait for a few seconds for your files to sync.
  6. Click the ellipsis button on the right to manage your files (for example, select Open folder, create a new Music folder, and select Force sync now).
  
  
Alternatively, on your desktop, you can also open a browser, and enter an ownCloud server URL address to connect. 


### Connect to an ownCloud server on a mobile app client
  1. Download the app from the Google Play Store or Apple App Store.
  2. Open the app, and enter your server URL address (for example, https://demo.owncloud.org)
  3. Enter your Username/Password (in this case, demo/demo).
  4. View the data available on the server (for example, Photos or Documents)
  5. Click + to upload a sample photo or file.  
  
For details on supported client platforms, see <a href="https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html#officially-recommended-supported-options" target="_blank">System Requirements</a>.

 