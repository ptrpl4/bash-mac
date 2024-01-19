# 🦄 UNIX based OS

## OS

What is operation system?

* Kernel
* Shell
* Preinstalled apps (including system GUI)
* File System

## Kernel

What the kernel does&#x20;

* manages processes (start, pause, stop, context switch)&#x20;
* handles system calls&#x20;
* manages memory&#x20;
* works with hardware (via drivers)

<figure><img src="../../.gitbook/assets/изображение (17).png" alt=""><figcaption></figcaption></figure>



### POSIX

POSIX stands for Portable Operating System Interface. It defines the application programming interfaces (APIs), along with command line shells and utility interfaces, for software compatibility with variants of Unix and other operating systems.&#x20;

Compliance with POSIX is voluntary, and while many operating systems, including Linux, are mostly POSIX-compliant, systems such as macOS, AIX, HP-UX, and Solaris, are certified.

## File System

For Linux everything is file. Folder - file with list of inner files/folders.

<figure><img src="../../.gitbook/assets/изображение (18).png" alt=""><figcaption></figcaption></figure>

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

<table><thead><tr><th width="200.33333333333331">Number</th><th>Permission Type</th><th>Symbol</th></tr></thead><tbody><tr><td>0</td><td>No Permission</td><td>---</td></tr><tr><td>1</td><td>Execute</td><td>--x</td></tr><tr><td>2</td><td>Write</td><td>-w-</td></tr><tr><td>3</td><td>Execute + Write</td><td>-wx</td></tr><tr><td>4</td><td>Read</td><td>r--</td></tr><tr><td>5</td><td>Read + Execute</td><td>r-x</td></tr><tr><td>6</td><td>Read + Write</td><td>rw-</td></tr><tr><td>7</td><td>Read + Write + Execute</td><td>rwx</td></tr></tbody></table>

`-` - no permission\
`r` - read\
`w` - write\
`x` -  execute

Permission set `-rwxrw-r--`

the first **`-`** implies that we have selected a certain file. If it were a directory, `d` would have been used instead of the first `-`.&#x20;

3 triplets of symbols. Each of them defines permissions for owner, group, and other users correspondingly. So, in the example, the owner can read, write and execute the file. The group can read and write, while the other can only read the file.

The most common sets presented as octal numbers are as follows:

* **755** is commonly used by web servers. The owner has all the permissions to read, write and execute it. Everyone else can read and execute but cannot make changes to the file.
* **644** means only the owner can read and write. Everyone else can only read. No one can execute this file.
* **655** means only the owner can read and write and cannot execute the file. Everyone else can read and execute and cannot modify the file.
* **777** means every user can read, write, and execute. Because it grants full permission, it should be used with caution. However, in some cases, you will need to set the 777 permissions before you can upload any file to the server.

|             | **File**                                | **Directory**                                                 |
| ----------- | --------------------------------------- | ------------------------------------------------------------- |
| **Read**    | One can open a file and see its content | One can view files in directories without opening these files |
| **Write**   | One can change the contents of the file | One can rename files                                          |
| **Execute** | One can run a file                      | One can have access to files                                  |
