---
description: base for Linux kernel
---

# 🦄 UNIX

## File modes and permissions

### **Authorization levels**

**Ownership**

* A **user** is the owner of the file. By default, the person who created a file becomes its owner. So, the user can sometimes be called an owner.
* A **group** contains several users. All of them have the same access permissions to the file. The group is useful when you have a project where a number of people require access to a file. Instead of manually assigning permissions to each user, you could add all the users to a group, and assign group permission to a file so that only the members of this group and no one else can read or modify the file.
* Any **other** user who has access to a file is the one who did not create this file and also does not belong to a group. Practically, it means everybody else. Hence, when you set the permissions for others, it is also referred to as set permissions for the world.

**Permission**

* **Read** **permission** gives users the authority to open and read a file. Read permission on a directory provides users with the list of its content.
* **Write permission** gives users the authority to modify the contents of a file. The write permission on a directory gives users the authority to add, remove, and rename files stored in the directory. Imagine you have a write permission on a file but do not have a write permission on the directory where the file is stored. You will be able to modify only the contents of the said file. However, you will not be able to rename, move, or remove the file from the directory.
* **Execute permission** lets users run a program. If the execute permission is not set, they might still be able to see/modify the program code (provided read and write permissions are set), but not run it.
* **No permission** means users can't do anything with a file.

**Table**

| Number | Permission Type        | Symbol |
| ------ | ---------------------- | ------ |
| 0      | No Permission          | ---    |
| 1      | Execute                | --x    |
| 2      | Write                  | -w-    |
| 3      | Execute + Write        | -wx    |
| 4      | Read                   | r--    |
| 5      | Read + Execute         | r-x    |
| 6      | Read + Write           | rw-    |
| 7      | Read + Write + Execute | rwx    |

`-` - no permission\
`r` - read\
`w` - write\
`x` -  execute

Permission set `-rwxrw-r--`

the first **`-`** implies that we have selected a certain file. If it were a directory, `d` **** would have been used instead of the first `-`.&#x20;

3 triplets of symbols. Each of them defines permissions for owner, group, and other users correspondingly. So, in the example, the owner can read, write and execute the file. The group can read and write, while the __ other can only read the file.

The most common sets presented as octal numbers are as follows:

* **755** is commonly used by web servers. The owner has all the permissions to read, write and execute it. Everyone else can read and execute but cannot make changes to the file.
* **644** means only the owner can read and write. Everyone else can only read. No one can execute this file.
* **655** means only the owner can read and write and cannot execute the file. Everyone else can read and execute and cannot modify the file.
* **777** means every user can read, write, and execute. Because it grants full permission, it should be used with caution. However, in some cases, you will need to set the 777 permissions before you can upload any file to the server.
