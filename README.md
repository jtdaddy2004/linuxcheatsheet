# linuxcheatsheet


List block devices

```
lsblk -f
NAME   FSTYPE LABEL     UUID                                 MOUNTPOINT
sda                                                          
├─sda1 ntfs   Windows 7 9E4A5AFE4A5AD31F                     
└─sda2 ext4             3329d6bf-09b3-4af5-8b02-c2b41dc22480 /
sdb                                                          
└─sdb1 ntfs   Data      6E86D5F486D5BD31                     
sr0 
```


<------------------------------------------------Commands---------------------------------------------------------------------->


<------File Managment CMD------>

rm "name"              -to remove file	
					   -r - removes directories recursively including the contents
					   -f -replaces file without prompting
					   -i -prompt before replaying file

mkdir "name"           -to make a directory
					   -m -set permissions on new directory
					   -p -create parent directories if they don't exist				   

rmdir "name"           -to remove directory 
					   -p -removes empty parent directories

cp 					   -copy files and directories
					   -a -archive recursively, preserving permissions, ownership, links and not following symbolic links
					   -R or -r -copies directories recursively

mv 					   -moves or renames files and directories
					   -u -overwrites ony if destination is older than the source
					   -f -replaces file without prompting
					   -i -prompt before replaying file

touch "name"           -to make a blank file

~                      -is used to refer to home

cd                     -takes you to home

cd .                   -takes you back to parent directory

cd ..                  -moves you one folder up

df -h 				   -displays disk space available on the file system containing each file name argument

Pipe command 		   -this is used to seperate a chain of commands 
	"|" (shift \)	   -EX: ls -al | less


	

<------Mangage local users and groups------>

useradd				   -create a new user or update default new user information

userdel				   -delete a user account and related files

newusers			   -update and create new users in batch

usermod				   -modify a user account
					   -d -move a user to a new home directory
					   -L -lock an account
					   -l rename an account 



<------Processes------>


Chgrp                  -change group

grpadd "group name"    -how to add a group

useradd "user name"    -how qto add a user

top                    -shows the top processes that are running

ps aux                 -displays information about a selection of the active processes

                        a = show processes for all users
                        u = display the process's user/owner
                        x = also show processes not attached to a terminal

pstree                 -display a tree of processes

ps auxwef              -gives and extreme view of the process tree

pgrep                  -look up or signal processes based on name and other attributes

cd /proc               -window into the kernel

cat cpuinfo            -gives a very detailed print out of the CPU

cat meminfo            -gives a very detailed print out of the memory

uptime                 -just gives uptime of the server

nice                   -a particular priority, giving the process more or less CPU time than other processes

lastb                  -gives a list of bad logins, use sudo to get the root level showing all bad logins, not only your users

killall                -sends signals to process by name

pkill                  -manage processes by terminal, group, username, PID, or command name





<------Permissions------>


ls -lsa                -to list everything in the directory along with permissions

chmod                  -change mode allows to change permissions to file system directories and files

Chowmn                 -change owner




<------SSH------>


hostnamectl 		   -used to query and change the system hostname and related settings

	AllowUsers - IMPORTANT Root login is only allowed for users in this group

kill -HUP or (PID) 	   -tells the service to reread the config file 

SCP 				   -secure copy

nautilus 			   -is the gnome file browser, can be entered in command line and come up in the GUI



<------Analyzing and Storing Logs------>


journalctl -xe 		   -used to query the contents of the systemd to see what works slash fails

dmesg 				   -print or control the kernel ring buffer

cd	/var/log 		   -this is where we find most of our logs 

logrotate			   -rotates, compresses, and mails system logs





<------Networking------>


tracepatch 			   -traces path to a network host discovering MTU along this path

traceroute			   -tracks  the route packets taken from an IP network on their way to a given host

arp -a 				   -manipulates  or displays the kernel's IPv4 network neighbour cache

dig (can use -mx) 	   -tool for interrogating DNS name servers. Performs DNS lookups and displays the answers that are returned from the name serer




<------Copy files between systems------>

cpio 					-copy files to and from archives

Zipping
                        -z -gzip compression
                        -j -bip2 compression
                        -J -xz compression

gunzip					-decompresses the .gz or expands the file

tar 					-saves many files together into a single archive, and can restore individual files from the archive

zcat 					-compress or expand files into memory 

bzcat 					-decompresses in memory and decompressed file are sent to STDOUT

YUM						-rpm based, package manager

rpm - qa				-queries and verifies all the packages on the machine

rpm -qa | grep "name"	-this queries and verifies packages that you specifically name with "grep"

rpm -hiv 				-used by Rupe that allows to show the version instead of upgrading automatically

mount					-mount a filesystem

umount					-unmount a filesystem




<------Control Services and Daemons------>


systemd 			   -a service manager for Linux operating systems. It acts as init system that brings up and maintains userspace services

systemctl 			   -may be used to introspect and control the state of the "systemd" system and service manager

socat 				   -establishes two bidirectional byte streams  and  transfers  data  between  them




<------Random------>


umask  				   -file creation permission

man 				   -command you want to know about  EX:  man ps

cat 				   -concatenate files and print on the standard output

less 				   -gives a lesser view to show the most important items only

sudo 				   -execute a command as another user, usually used as a one time command from root

q 					   -is a way to quit when using a command that requires scrolling

su   				   -allows you to switch users.  If left blank it gives you root





<------------------------------------------------Ninja Tricks---------------------------------------------------------------------->


history - gives the history of the commands you've run
	! and the number will allow you to rerun that command
	!! and the number will allow you to rerun the last command
	EX: !84; !85 will allow you to run the first step and the second step
	EX: !84 && !85 will make sure step 1 worked and then runs the second

ctrl r - to search for a word in your history and places it in your line

ctrl l - to clear the command line

ctrl arrow left and right - moves between arguements

ctrl a - moves to the begginging of the command line

ctrl u - clears the entire line

ctrl k - this deletes the line from the position of teh cursor to the end of the line

ctrl w - this delets the word before the cursor only

tab - to auto complete words or files as long as the command doesn't have multiple of the name being used

Home - move to the begginging of the command line

End - moves to the end of the command line



linux cert book filetype:pdf - this is how we find books




<------------------------------------------------Good ISH---------------------------------------------------------------------->


Htop - an interactive process viewer

Zorin - a good distro for Linux

logwatch - log analysis system. Logwatch parses through your system's logs and creates a report analyzing areas that you specify

http://rpmfind.net/ - this is used to find repositories for programs


<------------------------------------------------VI---------------------------------------------------------------------->


i = insert
a = append
x = delete
u = undo
dd = delete
p = paste
Shift ZZ - Save and exit
:Q! - get me the hell out of VI