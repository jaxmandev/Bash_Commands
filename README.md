Letters

Using the ls -l command. (-l is for lonf format)

Syntax
On each line, 

1st character —> identifies the type of entry listed. 
dash (-) it is a file. 
d it is a directory.

Next 9 characters —> represent the settings for the three sets of permissions.
The characters are indicators for the presence or absence of one of the permissions. They are either a dash (-) or a letter.
The first three characters show the permissions for the user who owns the file 
(user permissions).

The middle three characters show the permissions for members of the file’s group 
(group permissions).

The last three characters show the permissions for anyone not in the first two categories
(other permissions).

For example:
 --- means no permissions have been granted at all.
 rwx means full permissions have been granted. The read, write, and execute indicators are all present.
If the character is an r, w, or an x, that permission has been granted.
If the character is a dash, it means that permission is not granted.

The letters represent:
r: Read permissions. The file can be opened, and its content viewed.
w: Write permissions. The file can be edited, modified, and deleted.
x: Execute permissions. If the file is a script or a program, it can be run (executed).

Binary
Quick Lesson on Binary
If you don’t know binary its actually quite easy. It goes from right to left like this:
… 128 64 32 16 8 4 2 1

The digits you can use and what they represent are listed here:
0: (000) No permission.
1: (001) Execute permission.
2: (010) Write permission.
3: (011) Write and execute permissions.
4: (100) Read permission.
5: (101) Read and execute permissions.
6: (110) Read and write permissions.
7: (111) Read, write, and execute permissions.

Making changes
Syntax 
To use chmod to set permissions, we need to tell it:
Who: Who we are setting permissions for.
What: What change are we making? Are we adding or removing the permission?
Which: Which of the permissions are we setting?

Change permissions with letters

Step1
ls -l <filename>

Step2
chmod u=rw, og=r <filename>

If we want to add permission for everyone

chmod a+x <filename>
=
chmod +x <filename>

- Remove the r permission for the others group
chmod o-r *.txt

If we had wanted to include files in subdirectories, we could have used the -R (recursive) option.


Changing permissions win binary:

Quick Lesson on Binary
If you don’t know binary its actually quite easy. It goes from right to left like this:
… 128 64 32 16 8 4 2 1

Change permissions
To change the permissions of a file you use chmod. For example:
chmod 644 test.txt

Common chmod values
777 - readwrite by all 
755 - Read by Owner + Write by Owner + Execute by Owner + Read by Group + Execute by Group + Read by anyone (common for files in user’s home directory) 
644 - Everyone read, only owner can write.
