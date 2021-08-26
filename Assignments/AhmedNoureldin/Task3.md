

### Create a user account 
with the following attribute
  - username: islam
  - Fullname/comment: Islam Askar
  - Password: islam
  
  ```
  sudo useradd --create-home islam --comment "Islam Asker" --password islam --shell /bin/bash
  ```
  with the following attribute 
  
  - Username: baduser 
  - Full name/comment: Bad User 
  - Password: baduser 

  
  ```
  sudo useradd --create-home baduser --comment "Bad User" --password baduser --shell /bin/bash
  ```
  
-------------------  
### Create a supplementary (Secondary) group
* called pgroup with group ID of 30000

```
sudo groupadd pgroup --gid 30000
```

* called badgroup

```
sudo groupadd badgroup 
```

--------------------
### Add islam user to the pgroup group as a supplementary group

```
sudo usermod --groups pgroup islam  
```
--------------------
### Modify the password of islam's account to password

```
sudo passwd islam
```
--------------------
### Modify islam's account so the password expires after 30 days

```
sudo chage islam --expiredate 2021-09-26
```
--------------------
###  Lock bad user account so he can't log in

**lock the password** 
```
sudo usermod --lock baduser 
```
**Expire the user account**
```
sudo chage --expiredate 0 baduser 
```
**changing the shell to  non-interactive shell ( lock shell )**

```
sudo usermod -s /sbin/nologin baduser
```

**Checking**
```
grep ^root /etc/passwd  // Check if the user shell has been changed 
chage -list baduser // chack if user expire 
```

--------------------


### Delete bad user account

```
sudo userdel baduser 
```
--------------------

### Delete the supplementary group called badgroup.
```
sudo groupdel badgroup 
```
--------------------

### Create a folder called myteam in your home directory and change its permissions to read only for the owner.
```
mkdir myteam
ls -l 
chmod u=r myteam 
ls -l 
```

--------------------

### Log out and log in by another user

```
su - islam
exit // or ctrl + d 
```

### Try to access (by cd command) the folder (myteam)
--------------------
![image](https://user-images.githubusercontent.com/44178039/131020233-5525d0f0-52b3-4bfe-bbfa-f2af206ba40a.png)

--------------------
## Using the command Line

* Change the permissions of oldpasswd file to give owner read and write permissions
and for group write and execute  and execute only for the others (using chmod in 2 different ways)
```
sudo chmod u=rw,g=wx,o=x oldpasswd 
or 
sudo chmod 631 myteam
```
 
### What is the maximum permission a file can have, by default when it is just created? 
   
   **2 permissions** 
  
### And what is that for directory  ? 
   
   **3 permissions** 
  
### Change your default permissions to be no permission to everyone then create a directory and a file to verify.

```
umask 0777
mkdir tempdic
touch tempfile
ls -l 
```

  
### What are the minimum permission needed for:

* Copy a directory (permission for source directory and permissions for target parent directory)

  source : rx  
  parent : wx 

* Copy a file (permission for source file and and permission for target parent directory)

  source : r
  parent : w

* Delete a file : x 
* Change to a directory  : x
* List a directory content (ls command) : x
* View a file content (more/cat command) : r
* modify a file content : w


------------

### Create a file with permission 444. Try to edit in it and to remove it? Note what happened.

![image](https://user-images.githubusercontent.com/44178039/131027534-ec933538-4a82-431f-b6d7-d8d05eff947e.png)
----------------
### the difference between the “x” permission for a file and for a directory?

* Execute permission on files means the right to execute them, if they are programs. 

Example
![image](https://user-images.githubusercontent.com/44178039/131028789-6453afcc-49fa-4634-91eb-b48ce372357f.png)

**after give permissions** 

![image](https://user-images.githubusercontent.com/44178039/131028904-5efba9d3-e207-4c5c-acd1-ffbac9f1a080.png)


* For directories, execute permission allows you to enter the directory (i.e., cd into it), and to access any of its files.

![image](https://user-images.githubusercontent.com/44178039/131029294-ada09445-2f51-439d-a0d7-562b58303055.png)

