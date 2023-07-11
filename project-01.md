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

 