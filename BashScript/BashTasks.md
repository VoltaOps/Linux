## Using sed utility
1- Display the lines that contain the word “lp” in /etc/passwd file.

```
sed -n '/lp/p' /etc/passwd
```

2- Display /etc/passwd file except the third line.

```
sed -n '3!p' /etc/passwd
```

3- Display /etc/passwd file except the last line.

```
sed '$d' /etc/passwd
```

4- Display /etc/passwd file except the lines that contain the word “lp”.

```
sed  '/lp/d' /etc/passwd
```

5- Substitute all the words that contain “lp” with “mylp” in /etc/passwd file.
```
sed 's/lp/mylp/g' /etc/passwd
```


## Using awk utility
1- Print full name (comment) of all users in the system.  ***

```
awk -F: '{print "FullName : " ,$5}' /etc/passwd
```

2- Print login, full name (comment) and home directory of all users.( Print each line preceded by a line number)

```
awk -F: '{print " login : ",$1,"\n", "FullName : ",$5,"\n","HomeDirectory : ",$6,"\n","line Number:",NR,"\n"}' /etc/passwd
```
![image](https://user-images.githubusercontent.com/44178039/131699804-684ed140-27e4-4f42-b7d9-7dad2669e1fc.png)

3- Print login, uid and full name (comment) of those uid is greater than 500

```
awk -F: '{ if ($3 > 500)
print $1,$3,$5 }' /etc/passwd
```

4- Print login, uid and full name (comment) of those uid is exactly 500

```
awk -F: '{ if ($3 == 500)
print $1,$3,$5 }' /etc/passwd
```

5- Print line from 5 to 15 from /etc/passwd
```
awk '{if ( NR >= 5 && NR <= 15 ) print$0 }' /etc/passwd
```

6- Get the sum of all accounts id’s.
```
awk -F: '{sumIds += $3 } END { print sumIds }' /etc/passwd
```


---------------------------------------

1. Write a script called mycase, using the case utility to checks the type of character entered by a user:
	a. Upper Case.
	b. Lower Case.
	c. Number.
	d. Nothing.
  ```
 #! /bin/bash

case $1 in
[a-z] )
echo "Lower case"
;;
[A-Z] )
echo "Upper case"
;;
[0-9] )
echo "Number"
;;
*  )
echo "None"

esac
  ```
  
  
  
2. (Optional, Can be skipped)Enhanced the previous script, by checking the type of string entered by a user:
	a. Upper Cases.
	b. Lower Cases.
	c. Numbers.
	d. Mix.
	e. Nothing.
	

3. Write a script called mychmod using for utility to give execute permission to all files and directories in your home directory.

```
#! /bin/bash
cd ~  # go to home directory 
chmod u+x *  # give all execute permission 
```
![image](https://user-images.githubusercontent.com/44178039/131716852-aa13fc4f-ffb9-4f3a-8bc6-999f0948bc0d.png)



5. Write a script called mybackup using for utility to create a backup of only files in your home directory.
```
#!/bin/bash

# What to backup. 
backup_files="/home/ahmednr"

# Where to backup to.
dest="/home/backup"

# Create archive filename.
archive_file="backupFiles.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files

# Print end status message.
echo
echo "Backup finished"
```

7. Write a script called mymail using for utility to send a mail to all users in the system. Note: write the mail body in a file called mtemplate.
```
#! /bin/bash
# subject of Mail 
subject="Hello Users !"
# Message Body file 
mtemplate="/home/ahmednr/mtemplate"


# Loop through every login name, but skip the first 17 accounts ( root + system account)
for user in `awk -F: '{ print $1 }' /etc/passwd | tail +17`;
do
    # Mail the file
    echo Mailing to $user
    mail -s "$subject" $user < $mtemplate
done

```


9. Write a script called chkmail to check for new mails every 10 seconds. Note: mails are saved in /var/mail/username.
10. Create the following menu:
	a. Press 1 to ls
	b. Press 2 to ls –a
	c. Press 3 to exit
Using select utility then while utility.
8. Write a script called myarr that ask a user how many elements he wants to enter in an array, fill the array and then print it.
9. Write a script called myavg that calculate average of all numbers entered by a user. Note: use arrays
