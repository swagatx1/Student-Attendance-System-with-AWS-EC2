# Student-Attendance-Management-System
This PHP attendance system project is primarily concerned with dealing with students' attendance and records. In addition, the system displays all available data, such as instructor and student information, as well as their individual attendance. Admin Panel, Student Panel, and Teacher's Panel are the three sections of the project. In this web app's overview, the administrator has the ability to create users as well as insert student and teacher data. In terms of the project, the administrator has access to all student and teacher records. The teacher's account allows him or her to filter student data and keep track of his or her attendance for a certain subject. Aside from that, the student has access to just records and attendance reports.

-- Admin Login Details --

* Email   : admin@mail.com
* Password: Password@123

--Teacher Login Details--

* Email   : teacher@mail.com
* Password: pass123

Teacher Login - 

![Screenshot 2023-06-29 183453](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/43477b42-55a2-4bcd-8c27-ff49c95d6617)

Admin Login - 

![Screenshot 2023-06-29 183715](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/7be3f8e3-e1af-478c-98f5-fa0537f81cad)

Running AWS EC2 instance - 

![Screenshot 2023-06-29 183308](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/8d95efa9-3e04-4a63-b612-c0874d9f59f4)

Class teacher dashboard-

![Screenshot 2023-06-29 183629](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/19be7b48-c167-46c6-b2f0-721ce96e309a)

View student -

![Screenshot 2023-06-29 183519](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/dc484c3d-bd14-4835-9203-f80fa53374ee)

View student attendance - 

![Screenshot 2023-06-29 183551](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/eba8128a-6d36-4a83-b8d1-3fce34296483)

My SQL database dashboard - 

![Screenshot 2023-06-29 184141](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/e7f1ac90-b76f-4dec-843d-d09aae537bae)
![Screenshot 2023-06-29 184222](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/cf5c41e7-4cd7-4a9e-875e-5047cb45f6cb)

Admin dashboard - 

![Screenshot 2023-06-29 183806](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/099f8deb-17b3-4991-ac64-51a2478ee958)

Create class teacher - 

![Screenshot 2023-06-29 184305](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/5ab9f552-fee2-4b43-9664-de1ed13e4215)

Create new students - 

![Screenshot 2023-06-29 184338](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/72c414d5-24ac-4766-895a-62fa13459128)

Create session terms - 

![Screenshot 2023-06-29 184355](https://github.com/swagatx1/STUDENT-ATTENDANCE-SYSTEM/assets/113201534/9a9fb724-d246-4ee1-9867-c9b2953c1e5b)


STEPS-->

INSTALL LAMP STACK ON AWS - UBUNTU 18

Step 1 — Installing Apache and Updating the Firewall

	sudo apt update
	sudo apt upgrade
	sudo apt install apache2

	sudo ufw app list

	sudo ufw app info "Apache Full"

	sudo ufw allow in "Apache Full"

APACHE INSTALLED SUCCESFULLY TILL HERE, YOU CAN CHECK BY ENTERING YOUR PUBLIC IP OR PUBLICK DNS ADDRESS - http://your_server_ip

==================================================

Step 2 — Installing MySQL

	sudo apt install mysql-server
	sudo mysql_secure_installation
	sudo mysql
	
	SELECT user,authentication_string,plugin,host FROM mysql.user;
	
	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';    // please note here replace the "password" with yours.
	
	FLUSH PRIVILEGES;
	
	SELECT user,authentication_string,plugin,host FROM mysql.user;
	exit
	
At this point, your database system is now set up and you can move on to installing PHP, the final component of the LAMP stack.


=========================================================


Step 3 — Installing PHP

	sudo apt install php libapache2-mod-php php-mysql
	
In most cases, you will want to modify the way that Apache serves files when a directory is requested. Currently, if a user requests a directory from the server, Apache will first look for a file called index.html. We want to tell the web server to prefer PHP files over others, so make Apache look for an index.php file first.

	sudo nano /etc/apache2/mods-enabled/dir.conf
	
Move the PHP index file (highlighted above) to the first position after the DirectoryIndex specification, like this:

	<IfModule mod_dir.c>
	    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
	</IfModule>	

-----------------------------------

	sudo systemctl restart apache2
	sudo systemctl status apache2

	Press Q to exit this status output.
	
	Check PHP Version by entering 
	php -v

	Install the commonly required php modules by using the below commands - do remeber replace the php version number with your by checking the php -v command 
	For Example if the php -v command shows 7.4 version installed then you have to replace the 7.2 with 7.4 in the below command
	
	sudo apt install php7.2-common php7.2-mysql php7.2-xml php7.2-xmlrpc php7.2-curl php7.2-gd php7.2-imagick php7.2-cli php7.2-dev php7.2-imap php7.2-mbstring php7.2-opcache php7.2-soap php7.2-zip php7.2-intl -y
	
	sudo systemctl restart apache2
	
==================================================
	
Step 4 — Testing PHP Processing on your Web Server

	sudo nano /var/www/html/info.php
	
This will open a blank file. Add the following text, which is valid PHP code, inside the file:
	<?php
	phpinfo();
	?>

	
The address you will want to visit is:

	http://your_ip/info.php
	
You will get the php info page

===========================


PHPMYADMIN INSTALL STEPS BELOW

Step 1 — Installing phpMyAdmin

  sudo apt update
  sudo apt install phpmyadmin php-mbstring php-gettext

Warning: When the prompt appears, “apache2” is highlighted, but not selected. If you do not hit SPACE to select Apache, the installer will not move the necessary files during installation. Hit SPACE, TAB, and then ENTER to select Apache.

  sudo phpenmod mbstring
  sudo systemctl restart apache2

===================================================

http://your_domain_or_IP/phpmyadmin


====================================PERMISSIONS ADJUSTMENT================================

Step 2: Locate the PHP configuration file

Determining the right PHP configuration file can be very confusing especially because the ‘php.ini’ file can be located on a different folder depending on the PHP version.

The correct php.ini file should be in the Apache directory (e.g. ‘/etc/php/7.1/apache2/php.ini’). This will depend on the version of PHP. For instance, in Php7.2, the configuration file is located on ‘/etc/php/7.2/apache2/php.ini’

==============================================================

Step 3: Edit the Php Configuration file

  sudo nano /etc/php/7.1/apache2/php.ini


Standard ‘php.ini’ settings file - Change the INI settings according to the below values:

  memory_limit  = 128M           
  upload_max_filesize   = 50M                       
  post_max_size = 50M    
  max_execution_time = 120

  sudo service apache2 restart
  
Step 4: Verify the php.ini settings
  
  Refreshing the info.php page should now show your updated settings. Remember to remove the info.php when you are done changing your PHP configuration.
  
=========================================================================

Important Notes - Common Issues during/after PHP Install

MOST IMPORTANT
PERMISSION - YOU SHOULD OWN THE FILE BEFORE YOU CAN EDIT - YOU SHOULD KNOW THE USERNAME OF THE OPERATING SYSTEM.

=====================
Issues: Website pages not visible, not able to edit the files/folder , permsission denied issue, .htaccess not able to rewrite links.

Execute the Comands below to set proper file permissions on  Directories and files.

sudo chown -R ubuntu:root /var/www/html
sudo find html -type d -exec chmod 775 {} \;
sudo find html -type f -exec chmod 664 {} \;

