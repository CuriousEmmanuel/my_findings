we# basic git commands

#  create a new repo from command line


### git init
### git add Readme.md 
### git commit -m "first commit"
### git branch -M main // setting branch to main (use capital M(-M))
### git remote add origin https://
### git push -u origin master

# push existing repository from the command line

### git remote add origin https://
### git branch -M main
### git push -u originain
# connecting git with github
### note. While entering username/email and password always use an ssh key as your password

## merging branchs
## open for any suggestions
# About open source
### contribution to other projects
## 1. create pull request
## 2. wait for it to be merged 

# common errors in php
## The "White Screen of Death"
### in PHP typically occurs when there is a fatal error that prevents PHP from executing any further code, causing the web server to stop processing and display a blank page instead.
## Here's what you can do to troubleshoot and fix it:
1. check error logs
2. enanle error reporting
Set display_errors to On and error_reporting to E_ALL in your php.ini file.
3. syntax errors
4. memory exhaustion
You can increase PHP's memory limit by setting memory_limit in your php.ini file.
5.check server configuration
6. debugging tools
var_dump() or error_log()
7. check server logs
8. update or rollback changes you made
and sometimes it jusst dont work no matter what you try,,,,, any suggestions?
re installing and reconfiguring the server is the best option so far it worked for me i dont know for your case

# second encounter with white screen of death
## solution as per my discovery on 17/7/2024
### go to 127.0.0.1/phpmyadmin
![phpinfo](https://github.com/user-attachments/assets/4b9c0ebe-db7d-467b-82c6-294e001c9007)



### click to open the phpinfo in nav bar

![phpinfoopen](https://github.com/user-attachments/assets/569b4713-c06d-4115-8e0d-5901b0c34496)


### scroll down to error logs

![displayerrors](https://github.com/user-attachments/assets/f632728b-9c73-4c39-8b7a-99a6fddb61c3)



### check report_errors off
### then go to your phpdirectory and locate the php configuration files and check php.ini file
### open the file for editing the  change error_reporting On
### save and close the file



# mounting a flash drive disk on kali linux 
# flash drive not displaying in kali linux

### I recently had a challenge with my kali linux usb lash drive not displaying and therefore can not mount 
### after a long hours of research I found the best way to mount a flash drive using terminal it's so simple makes me feels stupid  how easy it is
## steps


1. Find what the drive is called

You'll need to know what the drive is called to mount it. To do that fire off one of the following (ranked in order of my preference):

lsblk
sudo blkid
sudo fdisk -l

You're looking for a partition that should look something like: /dev/sdb1. The more disks you have the higher the letter this is likely to be. Anyway, find it and remember what it's called.
2. Create a mount point (optional)

This needs to be mounted into the filesystem somewhere. You can usually use /mnt/ if you're being lazy and nothing else is mounted there but otherwise you'll want to create a new directory:

sudo  mkdir /media/usb

3. Mount!

sudo mount /dev/sdb1 /media/usb

When you're done, just fire off:

sudo umount /media/usb

### 8/11/2024:1152hrs
# LARAVEL
### FIRST ERROR
SQLSTATE[HYOOO]: General error:1 no such table: sessions(....)
SOLUTION
### php artisan migrate
This should create all the necessary tables for your application, including the session table.
### then clear cache
php artisan config:cache
php artisan cache:clear
restart your server and you are ready to go

## nov 27 2024

### After installation bof laravel woth intention of creating a new project you realize you cannot connect to your local database on xammp or wammp because mybe the default connection is sqlite and you are using mysql or vice versa, try changing and when you change on the .env file make sure you update the congig/database.php file too on the laravel directory. it worked for me 
## detailed report

Laravel Database Connection Issue: Solution Report


Problem Overview

While setting up a Laravel project, an error occurred stating:

> "Database 'laravel' does not exist on the 'mysql' connection."

![laravel](https://github.com/user-attachments/assets/4f49dcbd-be8d-4a6c-9b76-4f531bd93f19)

This error persisted even after updating the .env file with the correct database name and credentials. Laravel was still trying to connect to the default database (laravel) or using SQLite as the default connection, causing the application to fail.


---

Root Cause Analysis

The issue arose due to two misconfigurations:
after updating the .env file you need to also update the config/database.php file on the laravel directory
mostly ocures when laravel sets sqlite as default and you are using mysql
![sqlitetomysql](https://github.com/user-attachments/assets/dcf0da30-b786-4500-9f7e-06034187850a)



1. Incorrect Default Database Connection:
The default database connection in config/database.php was set to sqlite, which does not match the required mysql connection.


2. Unapplied Configuration Changes:
Laravel was caching old environment settings, causing it to ignore updates made to the .env file.




---

Solution Steps

1. Update the Database Name

In the config/database.php file, the database name was hardcoded to ensure Laravel connected to the correct database.

File: config/database.php

'database' => 'your_actual_db_name', // Replaced 'env('DB_DATABASE', 'forge')' with the database name


---

2. Set the Default Connection to MySQL

To ensure Laravel uses MySQL as the default database connection, the following change was made in config/database.php:

Before:

'default' => env('DB_CONNECTION', 'sqlite'),

After:

'default' => env('DB_CONNECTION', 'mysql'),


---

3. Clear Laravel Cache

Laravel caches configurations to improve performance. The following Artisan commands were executed to clear the cache and reload the updated configurations:

php artisan config:clear
php artisan cache:clear
php artisan config:cache


---

4. Verify the Database Connection

To ensure the application connects to the correct database:

Verified the database exists in MySQL:

SHOW DATABASES;

Confirmed the application connects properly with the updated settings.



---

Outcome

After applying the above changes, Laravel successfully connected to the mysql database named your_actual_db_name, and the application resumed functioning without errors.


---

Lessons Learned

1. Always verify both .env and config/database.php settings to avoid discrepancies.


2. Clear Laravel's configuration cache after making changes to ensure updates are applied.


3. Document any manual configuration changes for future reference.


## after changes now you can migrate without any problems
![laravel solution](https://github.com/user-attachments/assets/8186a961-d2c8-49cf-be28-d478ce370b7a)


---

Future Improvements

To avoid hardcoding the database name in config/database.php, revisit the .env setup and ensure Laravel correctly pulls the database credentials from the environment file.

some dedails are not necessary 

# NB
### after editing your .env file editing the connection type and database name check also your config/database.php on the same directory change also the database name and connection type for example mine was sqlite and i needed to change to mysql
stay safe
