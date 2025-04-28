# Linux Tasks
# Contents
- [Managing file ownership](#managing-file-ownership)
- [Managing file permissions](#managing-file-permissions)
- [Managing file permissions using numeric values](#managing-file-permissions-using-numeric-values)

## Managing file ownership

Why is managing file ownership important?
: It ensures that only authorized users or groups can access, modify, 
or execute files, protecting sensitive data and maintaining system integrity

What is the command to view file ownership?
: ``` bash
ls -l filename
```
<br>
In my example i used an example file called text.txt

``` 
-rw-rw-r-- 1 htank htank 24 Apr 28 14:57 test.txt

```
This was the result after running the command where the first htank represents username and the second represents
the group owner

In my version it shows rw- Read and Write  meaning the owner and group has these permissions 
<br><br>
Others: r-- → Read only

Why does the owner, by default, not receive X permissions when they create a file?
:  Files are assumed to be data and not executable programs and in terms of security, if every file were automatically executable, users could accidentally run files that are not meant to be executed, 
leading to errors or even potential security risks

What command is used to change the owner of a file or directory?
:  ``` 
chown newowner filename
``` <br>
This changes who's in charge of the file and the permissions<br> <br>
Only root (or a user with sudo) can change file ownership: <br>
``` 
sudo chown username myfile.txt
```

## Managing file permissions

Does being the owner of a file mean you have full permissions on that file? 
:  No, file permissions are managed independently of ownership but the owner is capable of changing
their permissions 

If you give permissions to the User entity, what does this mean?
: 
Granting permissions to a User entity means assigning specific privileges or rights to that user, controlling 
what they can and cannot do within a system or application

If you give permissions to the Group entity, what does this mean?
: Granting permissions to a group entity means allowing a designated group 
of users to access or interact with a specific resource or system component. This access is defined by the permissions assigned to the group,
determining what actions they can perform, such as reading, writing, or managing the resource. <br><br> Instead of granting permissions individually to each user,
you can grant them collectively to a group, simplifying administration and ensuring consistency. 

If you give permissions to the Other entity, what does this mean?
: You are setting permissions for all users who are not the owner and 
not part of the group associated with the file.


You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.
: User permissions are read-only so i can only read the file due to those being the permissions for users.
That means i am unable to write or execute the file.


## Managing file permissions using numeric values

What numeric values are assigned to each permission?
: - **Read permission (r)** = 4 <br>
- **Write permission (w)** = 2 <br>
- **Execute permission (x)** = 1
<br> e.g 7 = 4+2+1 (read, write, execute) <br>
6  = 4+2 (read, write) <br> 777 represents full permissions for all entities (User, Group, and Others)


## Changing File Permissions

What command changes file permissions?
: ```
chmod permissions filename
``` <br><br>Example: <br>
```
chmod 755 myfile.txt    7 - User/Owner 5 - Group 5 - Others
```


To change permissions on a file what must the end user be? (2 answers)
: To change permissions on a file, the end user must be:

- **The owner of the file**  – The user who owns the file has the right to modify its permissions.

- **Root (or sudo)** – The root user (or a user with sudo privileges) can change the permissions of any file, regardless of ownership.

Set User to read, Group to read + write + execute, and Other to read and write only
: ```
chmod 476 test.txt
``` <br> <br> After checking permissions of the file the left of the below response represents the update permissions <br>
```
-r--rwxrw- 1 htank htank 24 Apr 28 14:57 test.txt
```

Add execute permissions (to all entities)
: ```
chmod 577 test.txt
``` <br> <br> After checking permissions of the file the left of the below response represents the update permissions <br>
```
-r-xrwxrwx 1 htank htank 24 Apr 28 14:57 test.txt
```


Take write permissions away from Group
: ```
chmod 557 test.txt
``` <br> <br> After checking permissions of the file the left of the below response represents the update permissions <br>
```
-r-xr-xrwx 1 htank htank 24 Apr 28 14:57 test.txt
```

Use numeric values to give read + write access to User, read access to Group, and no access to Other.
: ```
chmod 640 test.txt   0 - This means no access given
``` <br> <br> After checking permissions of the file the left of the below response represents the update permissions <br>
```
-rw-r----- 1 htank htank 24 Apr 28 14:57 test.txt
``` 

