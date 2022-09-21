
**My very first PBL Project**
# Software Development Life Cycle (SDLC)
1. I have documented my research on SDLC and saved the file in Google Drive. You can access it by clicking on this link 	[SDLC](https://docs.google.com/document/d/1JdCA-DxQSVqaUybwD0bQUlkJ2IcsJUSf/edit?usp=sharing&ouid=106659470577486106602&rtpof=true&sd=true)

# Install Apache using Ubuntu’s package manage
1. update a list of packages in package manager
	`sudo apt update`

Here are the steps I took before installing apache on ubuntu

1. Created an instance in EC2 in AWS
2. Edited the inbound rules of the  security group to allow all trafic and changed the source to anywhere IPV4 
3. Ran this command `ssh -i "tammyta.pem" ubuntu@ec2-3-83-97-237.compute-1.amazonaws.com`  to change the directory to ubuntu

# To install Apache using Ubuntu

1. update a list of packages in package manager
`sudo apt update`
2. run apache2 package installation
`sudo apt install apache2`
3. To verify that apache2 is running as a Service in our OS, use following command
`sudo systemctl status apache2`

# To allow any traffic to our web server
1. I edited the inbound rules
2. added another rule; HTTP with the cdr blocks 0.0.0.0/0
Then I ran this command on ubuntun shell curl `http://localhost:80`

# To access Apache HTTP server on the web browser
1. we need to open this on the web browser http://http://3.83.97.237/
2. To check the public IP Address 
I ran the below command on ubuntu shell
`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`
[Apache HTTP server](http://3.83.97.237/)


# STEP 2 - INSTALLING MYSQL
1. I ran the following command to install MySql
`sudo apt install mysql-server`
2. To log in to the MySQL console
`sudo mysql`
3. I ran a security script that comes pre-installed with MySQL
`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
4. To exit mysql
`mysql> exit`
5. Start the interactive script by running:
`sudo mysql_secure_installation`
6. test if you’re able to log in to the MySQL
`sudo mysql -p`
7. To exit the MySQL console, type:
`exit`

# STEP 3 — INSTALLING PHP
1. To install these 3 packages at once, run:
`sudo apt install php libapache2-mod-php php-mysql`
2. Once the installation is finished, you can run the following command to confirm your PHP version:
`php -v`

# STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
**Setting up a domain called projectlamp**
1. Create the directory for projectlamp using ‘mkdir’ command as follows:
`sudo mkdir /var/www/projectlamp`

2. Next, assign ownership of the directory with your current system user:
`sudo chown -R $USER:$USER /var/www/projectlamp`
3. Create and open a new configuration file in Apache's directory using vi command line editor
`sudo vi /etc/apache2/sites-available/projectlamp.conf`
4. Command to show the new file in the sites-available directory
`sudo ls /etc/apache2/sites-available`
5. The output shows 
`000-default.conf  default-ssl.conf  projectlamp.conf`
6. Using a2ensite command to enable the new virtual host
`sudo a2ensite projectlamp`
7. To disable the default website that comes installed with Apache
`sudo a2dissite 000-default`
8. To make sure your configuration file doesn’t contain syntax errors, run:
`sudo apache2ctl configtest`
9. Finally, reload Apache so these changes take effect:
`sudo systemctl reload apache2`
10. Creating an index.html file from the web root /var/www/projectlamp
`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`
11. Now go to your browser and try to open your website URL using IP address:
http://54.162.92.213:80
12. Now go to your browser and try to open your website URL using DNS

http://ec2-54-162-92-213.compute-1.amazonaws.com:80

# STEP 5 — ENABLE PHP ON THE WEBSITE
1. To create a directory index 
`sudo vim /etc/apache2/mods-enabled/dir.conf`
To reload apache so that the changes can take effect
`sudo systemctl reload apache2`
2. Create a new file named index.php inside your custom web root folder:
`vim /var/www/projectlamp/index.php`
3. This will open a blank file. Add the following text, which is valid PHP code, inside the file:
`<?php
phpinfo();`




