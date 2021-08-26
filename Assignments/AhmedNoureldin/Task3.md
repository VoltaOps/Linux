

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

### Modify islam's account so the password expires after 30 days

```
sudo chage islam --expiredate 2021-09-26
```
