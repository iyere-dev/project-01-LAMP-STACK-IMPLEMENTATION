# LAMP STACK IMPLEMENTATION

# INSTALLING APACHE AND UPDATING FIREWALL

update a list of packages in package manager

`sudo apt update`

![updating list of packages](./images/installing_apache_updating_firewall/updating_packages.png)

`sudo apt install apache2`

![installing apache2](./images/installing_apache_updating_firewall/installing_apache2_page1.png)

![installing apache2](./images/installing_apache_updating_firewall/installing_apache2_page2.png)

`sudo systemctl status apache2`

![verifying apache2 is running](./images/installing_apache_updating_firewall/verifying_apache2_running.png)

open TCP port 80 in AWS console to allow web browsers access webserver

![opening TCP port 80](./images/installing_apache_updating_firewall/opening_TCP_port80.png)

curl http://localhost:80

![accessing server locally with curl command page1](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page1.png)

![accessing server locally with curl command page2](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page2.png)

![accessing server locally with curl command page3](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page3.png)

![accessing server locally with curl command page4](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page4.png)

![accessing server locally with curl command page5](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page5.png)

![accessing server locally with curl command page6](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page6.png)

![accessing server locally with curl command page7](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page7.png)

![accessing server locally with curl command page8](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page8.png)

![accessing server locally with curl command page9](./images/installing_apache_updating_firewall/accessing_server_in_ubuntu_shell_page9.png)

Test how apache http server can respond to requests from the internet

[testing how apache http server can respond to requests from the internet](http://3.121.76.119:80)

 curl -s http://3.121.76.119/latest/meta-data/public-ipv4

 ![testing apache http server using curl command](./images/installing_apache_updating_firewall/testing_apache_http_server.png)

## INSTALLING MYSQL

install mysql relational database managment system

`sudo apt install mysql-server`

![installing mysql-server](./images/installing_mysql_DBMS/installing_mysql-server.png)

log in to mysql console

`sudo mysql`

![log in to mysql database](./images/installing_mysql_DBMS/login_to_mysql_console.png)

 run script to remove some insecure default settings and lock down access to your database system (ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
) then exit

![running script](./images/installing_mysql_DBMS/running_script.png)

`exit`

![exiting mysql console](./images/installing_mysql_DBMS/exiting_mysql_console.png)

start interactive script

`sudo mysql_secure_installation`

![mysql secure installation interactive script](./images/installing_mysql_DBMS/mysql_secure_installation_interactive%20_script.png)

test if you’re able to log in to the MySQL console by running thge next command

`sudo mysql -p`

![testing log in to mysql console with password](./images/installing_mysql_DBMS/test_login_to_mysql_console.png)

`exit`

![exiting mysql console](./images/installing_mysql_DBMS/exiting_mysql_console2.png)

### INSTALLING PHP

Install 3 needed packages which are php, php-mysql, and libapache2-mod-php. Core packages are also installed as dependencies during this installation process.

`sudo apt install php libapache2-mod-php php-mysql`

![installing php, libapache-mod-php and php-mysql](./images/installing_php/installing_php_and_other_packages.png)

confirm php version by running the following command

`php -v`

![confirming php version](./images/installing_php/confirming_php_version.png)

CREATE A VIRTUAL HOST FOR THE WEBSITE USING APACHE

Set up a domain called "projectlamp" (By default Apache on UBUNTU 20.04 has one server block that is configured to serve documents from the /var/www/html directory)

Create a directory (projectlamp) in the /var/www/

`sudo mkdir /var/www/projectlamp`

![creating projectlamp directory](./images/creating_a_virtual_host_for_website_using_apache/creating_projectlamp_directory.png)

Assign ownership of the directory with your current system user

`sudo chown -R $USER:$USER /var/www/projectlamp`

![assigning ownership of directory](./images/creating_a_virtual_host_for_website_using_apache/changing_ownership_of_directory.png)

Create and open a new configuration file in Apache sites-available directory using vim editor

`sudo vi /etc/apache2/sites-available/projectlamp.conf`

paste barebones configuration with vim

![pasting barebones configuration](./images/creating_a_virtual_host_for_website_using_apache/pasting_barebones_config_in_vim.png)

Use ls command to show new file in the sites available directory

`sudo ls /etc/apache2/sites-available`

![showing new files in sites-available directory](./images/creating_a_virtual_host_for_website_using_apache/showing_new_files_in_sites-available_directory.png)

use a2ensite command to enable the new virtual host

`sudo a2ensite projectlamp`

![enabling new virtual host](./images/creating_a_virtual_host_for_website_using_apache/enabling_new_virtual_host.png)

You might want to disable the default website that comes installed with Apache. This is required if you’re not using a custom domain name, because in this case Apache’s default configuration would overwrite your virtual host. To disable Apache’s default website use a2dissite command

`sudo a2dissite 000-default`

![disabling default website that comes installed with apache](./images/creating_a_virtual_host_for_website_using_apache/disabling_default_website.png)

Make sure the configuration file doesnt contain any syntax errors

`sudo apache2ctl configtest`

![checking cnfiguration file for syntax errors](./images/creating_a_virtual_host_for_website_using_apache/checking_config_file_for_syntax_errors.png)

Reload Apache for changes to take effect

`sudo systemctl reload apache2`

![reloading apache2](./images/creating_a_virtual_host_for_website_using_apache/reloading_apache2.png)

The new website is now active, but the web root /var/www/projectlamp is still empty. Create an index.html file in that location so that we can test that the virtual host works as expected.

`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

![creating an index.html file in web root /var/www/projectlamp](./images/creating_a_virtual_host_for_website_using_apache/creating_index.html_file.png)

Open website url in browser

[opening website using public url](http://3.121.76.119/)

![opening website using public url](./images/creating_a_virtual_host_for_website_using_apache/website_url_page.png)

[opening website with public DNS](http://ec2-3-121-76-119.eu-central-1.compute.amazonaws.com/)

![opening website with public DNS](./images/creating_a_virtual_host_for_website_using_apache/opening_website_with_public_DNS.png)

ENABLE PHP ON WEBSITE

Change behaviour of index.html file taking precedence over index.php file by editing /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive

`sudo vim /etc/apache2/mods-enabled/dir.conf`

In the vim editor effect the changes stated below

<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>

![effecting changes in /etc/apache2/mods-enabled/dir.conf](./images/enabling_php_on_website/effecting_changes_with_vim.png)

Reload apache

`sudo systemctl reload apache2`

![reloading apache2](./images/enabling_php_on_website/reloading_apache2.png)

 create a PHP script to test that PHP is correctly installed and configured on your server

 first create a file named index.php inside the custom web root folder then add php code
 
 `vim /var/www/projectlamp/index.php`

![adding php code](./images/enabling_php_on_website/adding_php_code.png)

refresh web page

![refreshed webpage showing php is working as it should](./images/enabling_php_on_website/refreshed_webpage.png)

After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment and your Ubuntu server. 

`sudo rm /var/www/projectlamp/index.php`

![removing file created](./images/enabling_php_on_website/removing_file_created.png)

END OF PROJECT

