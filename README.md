# Permissions
## General
Using the ls -l command. (-l is for lonf format)


### Using Letters
On each line, 

1st character —> identifies the type of entry listed. 
```
- dash (-) it is a file. 
- d it is a directory.
```

Next 9 characters —> represent the settings for the three sets of permissions.
```
The characters are indicators for the presence or absence of one of the permissions. They are either a dash (-) or a letter.
The first three characters show the permissions for the user who owns the file 
(user permissions).

The middle three characters show the permissions for members of the file’s group 
(group permissions).

The last three characters show the permissions for anyone not in the first two categories
(other permissions).
```

The letters represent:
```
r: Read permissions. The file can be opened, and its content viewed.
w: Write permissions. The file can be edited, modified, and deleted.
x: Execute permissions. If the file is a script or a program, it can be run (executed).
```

For example:
```
 --- means no permissions have been granted at all.
 rwx means full permissions have been granted. The read, write, and execute indicators are all present.
```
#### Practical
```
chmod u=rw, og=r <filename>
- set the permission for user is rw and for other and group is simply r
```
```
chmod a+x <filename>
=
chmod +x <filename>
- if we want to add permission for everyone
```
```
chmod o-r *.txt
- remove the r permission for the others group
```
```
chmod -R o-r *.page
- remove the r permission for the other group and include files in subdirectories
- for subdir use the -R (recursive) option.
```

### Using Binary
Quick Lesson on Binary
```
If you don’t know binary its actually quite easy. It goes from right to left like this:
128 64 32 16 8 4 2 1
```

The digits you can use and what they represent are listed here:
```
0: (000) No permission.
1: (001) Execute permission.
2: (010) Write permission.
3: (011) Write and execute permissions.
4: (100) Read permission.
5: (101) Read and execute permissions.
6: (110) Read and write permissions.
7: (111) Read, write, and execute permissions.
```

### Using binary
To change the permissions of a file you use chmod.
chmod 644 test.txt
```
- "6" is 1st digit --> user permission
- "4" is 2nd digit --> group permission
- "4" is 3rd digit --> othe perrmission
```

Common chmod values
```
777 - readwrite by all 
755 - Read by Owner + Write by Owner + Execute by Owner + Read by Group + Execute by Group + Read by anyone (common for files in user’s home directory) 
644 - Everyone read, only owner can write.
```
# Streams

There are 3 types of streams in bash. Standard Output, Error and Input stream. These streams are used to receive and send sequences of characters into and out of bash.
```
stdout a standard output stream which displays output from commands.
stderr a standard error stream which displays error output from commands.
strdin a standard input stream which provides input to commands.
```
# Redirects

Redirection is used to send and redirect the output of one command to another command / file etc.
```
n> this redirect the output from file n to another file or command.
If the file does not exist it is created.
```
If it does exists it's content is overriden and no warning is given.
