# Permissions

[TOC]

### File Permissions

![](D:\SEGURANCA\01_Apontamentos\Linux\img\file_permissions_1.png)

![](D:\SEGURANCA\01_Apontamentos\Linux\img\file_permissions_2.png)

#### Example

![](D:\SEGURANCA\01_Apontamentos\Linux\img\file_permissions_example.png)

The file **space.txt** in has the following permissions:

- The dash (-) means that this is a file. For directories, the first dash would be a “d”.
- The first set of characters is for user permission (**rwx**). The user, **analyst**, who owns the file can **R**ead, **W**rite and e**X**ecute the file.
- The second set of characters is for group permissions (**rw-**). The group, **staff**, who owns the file can **R**ead and **W**rite to the file.
- The third set of characters is for any other user or group permissions (**r--**). Any other user or group on the computer can only **R**ead the file.

The second field defines the number of hard links to the file (the number **1** after the permissions). A hard link creates another file with a different name linked to the same place in the file system (called an inode). This is in contrast to a symbolic link, which is discussed on the next page.

The third and fourth field display the user (**analyst**) and group (**staff**) who own the file, respectively.

The fifth field displays the file size in bytes. The **space.txt** file has 253 bytes.

The sixth field displays the date and time of the last modification.

The seventh field displays the file name

### Modifying Permissions

#### Numerical Format
```bash
# Adding permissions
chmod 751 <file>
```

#### Signal Format
```bash
# Adding permission bit on a file
chmod u+x <file>
 
# Removing permission bit on a file
chmod u-x <file>

# Adding multiple permission bits on a file
chmod ug+w <file>
```



### Ownership Permissions

```bash
# Modify user ownership
sudo chown <user> <file>

# Modify group ownership
sudo chgrp <group> <file>

# Modify both user and group ownership at the same time
sudo chown <user>:<group> <file>
```