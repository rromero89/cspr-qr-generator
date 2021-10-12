# cspr-qr-generator
cspr-qr-generator Casper Currency

Prerequisites
Before starting these steps, you must have a regular user configured on your server, this must correspond to an account with sudo privileges, other than superuser (root). Additionally, you will need to enable a basic firewall that blocks non-essential ports. You can learn how to set up a regular user account and how to set up the firewall for your server by following our initial setup guide for Ubuntu 18.04 .

When you have an account available, log in with the user other than superuser that we mentioned above and you can start.

https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04

Step 1 - Install Apache
Apache is available within Ubuntu's default software repositories, making installation possible using conventional package management tools.

We will start by updating the index of local packages. This, to ensure that it reflects the most recent loads of the new versions of the packages.

$ sudo apt update

Then install the package apache2:

$ sudo apt install apache2

After confirming the installation, it will aptinstall Apache as well as all required dependencies.

Step 2 - Configure the firewall
Before testing Apache, it is necessary to modify the firewall settings in such a way that external access to the default web ports is guaranteed. 
Assuming you followed the prerequisite instructions, you will have a UFW firewall configured to restrict access to your server.

During the installation, Apache itself, registers in the UFW to provide the profiles that allow to enable or disable its access through the firewall.

List the application profiles inside by ufwtyping:

$ sudo ufw app list

A list of application profiles should be displayed:

Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
  
  As you may have noticed, there are three profiles available for Apache:

Apache - This profile enables only port 80 (normal, unencrypted web traffic).
Apache Full : This profile enables two ports: port 80 (normal, unencrypted web traffic) and port 443 (traffic encrypted using TLS / SSL).
Apache Secure - This profile enables only port 443 (traffic encrypted using TLS / SSL).
It is recommended that you always enable the profile with the most restrictions depending on the required traffic and how your machine has
been configured. As we have not yet configured SSL
for our server in this guide, we will only allow traffic through port 80:

$ sudo ufw allow 'Apache'

The change can be verified by typing:

$ sudo ufw status

As you can see, the profile has been activated, and access to the web server is allowed.

Step 3 - Verify the web server
At the end of the installation process, Ubuntu 18.04 starts Apache. Then the web server should be up and running.

Verify with the base system systemdthat the service is running by typing:

$ sudo systemctl status apache2

As can be seen from this output, the service has started successfully. However, the best test to perform this check is to request a page from the Apache server.

You can access Apache's default page to confirm that it is running correctly through your IP address. If you don't know the IP address of your server, you can get it in different ways from the command line.

Try typing the following in the command line of your server:

$ hostname -I

You will be returned some addresses separated by spaces. Try them all in your web browser to ensure they work.

Alternatively, you can type the following command, which should return the public IP address as it is perceived from an external place on the internet:

$ curl -4 icanhazip.com

When you have the IP address of your server, enter it in the address bar of your browser:

http://ip_your_server

Step 6 - Familiarize yourself with important Apache files and directories
Now that you know how to manage Apache's particular service, take a few minutes to familiarize yourself with some important files and directories.

Content
/var/www/html: is where the actual web content is located. By default, it consists only of the Apache default page you saw earlier, and is persisted in the directory /var/www/html. This can be modified in the Apache configuration files.

$ cd /var/www/

$ git clone git@github.com:rromero89/cspr-qr-generator.git

$ git checkout master

next:

Visit http://127.0.0.1

Enjoy..!!

