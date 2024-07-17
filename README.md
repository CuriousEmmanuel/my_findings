# basic git commands

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
then click on php.ini
scroll down to error logs
check report_errors off
then change to 
report_error On
