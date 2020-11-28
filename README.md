# Bash Commands Cheatsheet

- In Linux everything is a file and there are no extensions. 
- They are just different files that take different formats.

Linux is case-sensitive

Avoid spaces in making names etc.
```
$ mkdir my documents
$ mkdir "my documents"
```
1. The first line will create two folders: my and documents

2. The second line will create a single folder called `my documents`

Hidden files start with a:
-  . 
- 
- e.g. .git is hidden. To view them --> ls -a

Use rm -rf to remove files or directories. -rf will remove them forcibly (-f) and recursively (-r removes the folder and all of it's subdirectories and contents)
```
ll = ls -al - shows files and their permissions
```
Flags for bash commands are options

Check the user manual
``` 
man <command>
```
- You can find detailed information on each command using them.

# Head Tail Sort

Head prints the first 10 lines out of the file by default
```
head <filename>
```
With the addition of -n flag we can specify how many lines we would like to see
```
head -n 2 <filename>
```
Tail works the same way as head but instead prints the bottom lines of the file
```
tail <filename>
tail -n 2 <filename>
```
Sort is used to alphabetically or numerically sort the content by each line.
```
sort <filename>
```

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
If it does exists it's content is overriden and no warning is given.
```
Example
```
head -n 2 file1txt > file2.txt
```

# Wildcards
- Used to define some pattern for searching or matching text/string
- Wildcards include: *, ? and []
1. * is used to search for certain characters that occur 0 or more times
2. ? is used to search for a fixed numer of characters, each ? indicates each character
3. [] is used to match the characters of a defined range or group of characters

- Examples:
```
ls *.md
```
 - shows all files that have the extension .md
```
ls *_file.*
```
- shows all files that contain _file in it's name
```
ls ???.md 
```
- shows all files that have a name 3 characters long and ends with .md
```
ls *.?? 
```
- returns any file whose extension is 2 characters long (e.g. .md)

# GREP
- It's used to search for strings/text from a file or from the output of another command
- It returns the lines where it finds a match
- We can also use grep to return the lines where it doesn't match, using grep -v

- Examples:
```
grep "Jax" text.txt 
```
- returns every line that contains Jax in the file text.txt
```
grep -i "hello" text.txt 
```
- returns every line that contains hello in whatever combination of upper or lowercase letters (e.g. "hellO", "hElLO", "HELLO")

# Streams
- Every program that runs on the command line automatically has three data streams connected to it
1. STDIN - this is the data fed into the program
2. STDOUT - data printed by program, will default to terminal
3. STDERR - data printed in case of error, will default to terminal

# Piping
- Using the character | we can feed the the output from the left program as input to the right program
- You can pipe as many times as needed and it follows intuitively

- Examples:

```ls | head -n 3
```
- will output just the first 3 files/directories from the ls command (the order will follow the order ls lists them)
```
ls | head -n 3| tail -n 1
```
- it will output the last item in the list from above

# ps aux

- ps shows only the processes running under the logged in user from current terminal
```
ps -a - shows the processes from all users
ps -u - shows the processes alongside the users
ps -x - shows the processes not attached to the current terminal
```

# ps aux and grep

- We can combine these two commands to look for processes that have a specific string/text

Examples:
```
ps aux | grep "vagrant"
```
- returns all the processes that contain vagrant in the columns (so will return all processes that have vagrant as a user or vagrant in command)
```
ps aux | grep 21:00 
```
- returns all processes that contain this time, useful if you want to see processes started at a certain time

## Starting processes and sending to background
- Usually foreground processes interact with terminal, so when they are executing it stops us from using the command line
- We can solve this by sending processes to the background.
```
1. We can make a process to run in the background initially by adding - & 
to the end of it
2. We can stop a process that is running with 
- <CTRL> + Z 
and then type 
- bg 
(background) to start it again but this time in the background
```
## Finding processes
- When there are processes being executed in the background, we can type jobs in the command line to list all the processes happening in the background
- To find the process id and it's name, we can use 
- pgrep <text-to-match>
This will return a list of process id's and the corresponding names that were matched

## Stopping processes
- To stop a background process from executing, we can use the command. 
```
kill 
```

Type in 
- jobs 
to list all processes with their jobid and then type in 
- kill %<jobid>
```
kill
```
- Command in general will stop the process given it's process id.
We can stop processes in general with pkill which kills processes based on it's name
Example:
```
kill %1
```
- this will kill the first background process
