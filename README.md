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
