# My-SQL

This file will help to create a MY SQL Database in Raspberry PI

## Setup a Raspberry Pi MYSQL Database
In this Raspberry Pi MYSQL tutorial, we will be showing you how to install and configure the MySQL server on your Pi.

MySQL is one of the world’s most popular relational database system and is a common inclusion in most LAMP ( Linux, Apache, MYSQL, and PHP) stacks.
It is one of the pieces of technology that helps drive the modern web.

A database such as MYSQL is often a key component of dynamic websites and is one of the best ways of storing data for web applications.

If you’re unfamiliar with MySQL, it is a relational database management system and allows you to store and maintain large amounts of data easily.
Setup something like PHPMyAdmin if you want a graphical user interface rather than the command line. It does make managing a database slightly easier.

## Equipment List
Below are the pieces of equipment that I made use of for this Raspberry Pi MySQL tutorial.

Recommended:
* Raspberry Pi
* Micro SD Card
* Power Supply
* Ethernet Cord or WiFi dongle (The Pi 3 has WiFi inbuilt)

Optional:
* Raspberry Pi Case

## Setting up MYSQL on a Raspberry Pi
As with this code, we will be utilizing the Raspbian operating system.
If you’re using something different, then the steps may differ slightly.

**1.** Before we get started with installing MySQL to our Raspberry Pi, we must first update our package list and all installed packages.
We can do this by running the following two commands.
````
sudo apt update
sudo apt upgrade
````

**2.** The next step is to install the MySQL server software to your Raspberry Pi.
Installing MySQL to the Raspberry Pi is a simple process and can be done with the following command.
````
sudo apt install mariadb-server
````

**3.** With the MySQL server software installed to the Raspberry Pi, we will now need to secure it by setting a password for the **root** user.
By default, MySQL is installed without any password set up meaning you can access the MySQL server without any authentication.
Run the following command to begin the MySQL securing process.
````
sudo mysql_secure_installation
````
Just follow the prompts to set a password for the root user and to secure your MySQL installation.
For a more secure installation, you should answer **Y** to all prompts when asked to answer **Y** or **N**.

These prompts will remove features that allows someone to gain access to the server easier.
Make sure you write down the password you set during this process as we will need to use it to access the MySQL server and create databases and users for software such as WordPress or PHPMyAdmin.

**4.** Now if you want to access your Raspberry Pi’s MySQL server and start making changes to your databases, you can enter the following command.
````
sudo mysql -u root -p
````

**5.** You will be prompted to enter the password that we just created in step 3 for MySQL’s root user.
Note: Like most Linux password inputs, the text will not show up as you type.

**6.** You can now enter MYSQL commands to create, alter, and delete databases. 
Through this interface, you can also create or delete users and assign them the rights to manage any database.

**7.** There are two different ways you can quit out of the MYSQL command line, the first of those is to type `quit;` into the MySQL interface.
The other way of quitting out of the MYSQL command line is to press `CTRL + D`.

**8.** At this point, you will now have successfully setup MySQL on your Raspberry Pi. 
Our next few sections will go into making better use of this database.

## Creating a MySQL Database and User
**1.** Before we proceed to create a MySQL user and database on our Raspberry Pi, we must first log back into the MySQL command-line tool.
Run the following command to log in to the MySQL command line. 
You will be prompted to enter the password for the “root” account that you set up earlier.
````
sudo mysql -u root -p
````

**2.** Let’s start by creating a MySQL database using the following command.
This command is super simple and is just “CREATE DATABASE” followed by the name that you want to give the database.
In our example, we will be calling this database `exampledb`.
````
CREATE DATABASE exampledb;
````

**3.** Next, we will create a MySQL user that we will assign to our new database.
We can create this user by running the following command.
For this example, we will be calling the user `exampleuser` and giving it the password `exampleuser`.
When creating your own, make sure you replace both of these.
````
CREATE USER 'exampleuser'@'localhost' IDENTIFIED BY 'exampleuser';
```` 

**4.** With the user created, we can now go ahead and grant all privileges to the user so that it can interact with the database.
This command will grant all permissions to our `exampleuser` for all tables within our `exampledb` database.
````
GRANT ALL PRIVILEGES ON exampledb.* TO 'exampleuser'@'localhost';
````

**5.** The final thing we need to do for both our MySQL database and user to be finalized is to flush the privilege table.
Without flushing the privilege table, the new user won’t be able to access the database.
We can do this by running the following command.
````
FLUSH PRIVILEGES;
````
If you rather not use the command line to administrate your databases then you can always install PHPMyAdmin instead.

## Installing the PHP MySQL Connector
**1.** If you intend on using a MySQL database from PHP, you will need to make sure that you have the module installed.
You can install the MySQL connector for PHP to your Raspberry Pi by running the following command.
````
sudo apt install php-mysql
````

As I mentioned earlier, there are many projects where a database will come in handy. Most modern websites will require a database to be able to function correctly.
At this point of the tutorial you should now have a MySQL server up and running on your Raspberry Pi. 
If you have ran into any issues feel free to drop a comment in the comments section below.

## Installing the MySQL Connector for Python
You need to first install the mysql connector for Python before trying to use it.
You can do this by running one of the following commands.
**Python 2**
````
sudo pip install mysql-connector-python
````

**Python 3**
````
sudo pip3 install mysql-connector-python
````

## Example
Example code are present in the [example]() folder.
