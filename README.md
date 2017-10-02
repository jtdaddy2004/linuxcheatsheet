# linuxcheatsheet




<------------------------------------------------Commands---------------------------------------------------------------------->




<------File Managment CMD------>

~                       -is used to refer to home, putting a ~/ allows you to quickly type the path from home and moving further

cd                      -takes you to home

cd .                    -takes you back to parent directory

cd ..                   -moves you one folder up

cp 					    -copy files and directories

cut
 						
		-d delimiter (whhat separates the rows? tabs, commas, spaces)
		-f fields you would like to select (first row, last row, rows 2-3, first 5 rows, last five rows)
		-c the number of characters you would like to select		

df -h 				    -displays disk space available on the file system containing each file name argument

		-h makes it a human readable allowing to see in bytes and gb
		-df -h | sort -k5,2 -h -r  (sort by columns -k = columns adding numbers sorts by specific column.  Adding a comma allows to sort first column first and then by the second number) 
		-r reverses the order

du -h 				    -shows disk usage in human format

		-a -archive recursively, preserving permissions, ownership, links and not following symbolic links
		-R or -r -copies directories recursively

ls 					    -shows a list of what is in a directory

	| xargs sudo 	    -is a command that takes stream of information and makes it an arugument 
	du -s -h 		    -is useful to show the disk usage in human form while working with xargs
	| sort -h  		    -is sorting in human format
					    -EX: ls | xargs sudo du -s -h | sort -h

mkdir "name"            -to make a directory

		-m -set permissions on new directory
		-p -create parent directories if they don't exist				   

mv 					    -moves or renames files and directories

		-u -overwrites ony if destination is older than the source
		-f -replaces file without prompting
		-i -prompt before replaying file

Pipe command 		    -this is used to seperate a chain of commands 
	"|" (shift \)	    -EX: ls -al | less

pwd				   	    -shows the current directory you in

rm "name"               -to remove file	
					    
		-r - removes directories recursively including the contents
		-f -replaces file without prompting
		-i -prompt before replaying file



rmdir "name"            -to remove directory 

		-p -removes empty parent directories

seq 10 					-returns a sequences of numbers 1 to 10

sudo find /var -type f -exec du -h {} \; | sort -h | head -20 

		-find = will find folders, directories and so much more
		-/var = shows looking in the VAR folder, if just / will look in root
		-type f = looking for a specic type of something   
		-d = dir 
		-f=file (look on man pages for more info)
		-exec = executing an aribtrary command on a file
		-head -20 = this just gives me the first 20 items I want to look at,  tail = gives me the last of the items

tar czvf file.tar.gz file1.txt file2.txt (example text file)

		-c create a tar archive
		-z compress it with gzip / alternatively replace -z with -j for bzip compression (bz2 output extension)
		-v show verbose output
		-f specify the archive will out an output file
		-file.tar.gz (output name)


tar xzvf file.tar.gz

		-x extract tar file
		-z decompress using gzip
		-v verbose output
		-f read from file ;s


touch "name"            -to make a blank file

tr 						-translate/delete characters

		-s squeeze repeated characters (compress multiple spaces into 1)
		-d delete characters


wc -l  					-(count number of lines in file) 
wc -c  					-(count number of characters in file)
wc -l 					-(count number of files and folders)

	


<------Mangage local users and groups------>

newusers			    -update and create new users in batch

useradd					-create a new user or update default new user information

userdel					-delete a user account and related files

usermod				    -modify a user account

		-d -move a user to a new home directory
		-L -lock an account
		-l rename an account 




<------Processes------>

cat cpuinfo             -gives a very detailed print out of the CPU

cat meminfo             -gives a very detailed print out of the memory

cd /proc                -window into the kernel

chgrp                   -change group

grpadd "group name"     -how to add a group

killall                 -sends signals to process by name

lastb                   -gives a list of bad logins, use sudo to get the root level showing all bad logins, not only your users

lsblk -f 			    -this gives information on drives or block devices

		NAME   FSTYPE LABEL     UUID                                 MOUNTPOINT
		sda                                                          
		├─sda1 ntfs   Windows 7 9E4A5AFE4A5AD31F                     
		└─sda2 ext4             3329d6bf-09b3-4af5-8b02-c2b41dc22480 /
		sdb                                                          
		└─sdb1 ntfs   Data      6E86D5F486D5BD31                     
		sr0 


nice                    -a particular priority, giving the process more or less CPU time than other processes

pgrep                   -look up or signal processes based on name and other attributes

pkill                   -manage processes by terminal, group, username, PID, or command name

ps aux                  -displays information about a selection of the active processes

		a = show processes for all users
		u = display the process's user/owner
		x = also show processes not attached to a terminal
		EX = ps aux | grep java -tells things that run in java

ps auxwef               -gives and extreme view of the process tree

pstree                  -display a tree of processes

top                     -shows the top processes that are running

uptime                  -just gives uptime of the server

useradd "user name"     -how qto add a user




<------Permissions------>

chmod                   -change mode allows to change permissions to file system directories and files

Chowmn                  -change owner

ls -lsa     			-to list everything in the directory along with permissions




<------SSH------>


hostnamectl 			-used to query and change the system hostname and related settings

	AllowUsers - IMPORTANT Root login is only allowed for users in this group

kill -HUP or (PID) 	    -tells the service to reread the config file 

SCP 				    -secure copy




<------Analyzing and Storing Logs------>

cd	/var/log 		    -this is where we find most of our logs 

dmesg 				    -print or control the kernel ring buffer

journalctl -xe 			-used to query the contents of the systemd to see what works slash fails

		ex = journalctl --no-pager --since=2017-09-25 -u polkit > ~/(add name).txt -this shows exact date a service stopped, outputs to a txt file   

logrotate			    -rotates, compresses, and mails system logs

Paging System

		-Shift + g 	-goes to the bottom
		-gg 		-goes to the top
		-/			-allows searching
		-ctrl d 	-takes you down a page
		-ctrl u 	-takes you up a page
		-grep		-allows to do an advanced search




<------Networking------>

arp -a 				    -manipulates  or displays the kernel's IPv4 network neighbour cache

dig (can use -mx) 	    -tool for interrogating DNS name servers. Performs DNS lookups and displays the answers that are returned from the name server

tracepatch 				-traces path to a network host discovering MTU along this path

traceroute			    -tracks  the route packets taken from an IP network on their way to a given host




<------Copy files between systems------>

bzcat 					-decompresses in memory and decompressed file are sent to STDOUT

cpio 					-copy files to and from archives

gunzip					-decompresses the .gz or expands the file

mount					-mount a filesystem
	mount UUID			-allows you to mount a drive by it's UUID  /mnt/(add the directory)

rpm - qa				-queries and verifies all the packages on the machine

rpm -qa | grep "name"	-this queries and verifies packages that you specifically name with "grep"

rpm -hiv 				-used by Rupe that allows to show the version instead of upgrading automatically

tar 					-saves many files together into a single archive, and can restore individual files from the archive

umount					-unmount a filesystem

YUM						-rpm based, package manager

zcat 					-compress or expand files into memory 

Zipping

		-z -gzip compression
		-j -bip2 compression
		-J -xz compression




<------Control Services and Daemons------>

systemctl 			    -may be used to introspect and control the state of the "systemd" system and service manager

		ex = systemctl --no -pager list -unit-files | grep service -this is an easy way to show all services enabled

systemd 				-a service manager for Linux operating systems. It acts as init system that brings up and maintains userspace services

		ex = ls /etc/systemd/system -this shows local services that have been installed

socat 				    -establishes two bidirectional byte streams  and  transfers  data  between  them




<------Random------>

cat 				    -concatenate files and print on the standard output

less 				    -gives a lesser view to show the most important items only

man 				    -command you want to know about  EX:  man ps

q 					    -is a way to quit when using a command that requires scrolling

su   				    -allows you to switch users.  If left blank it gives you root

sudo 				    -execute a command as another user, usually used as a one time command from root

umask  					-file creation permission




<------------------------------------------------Ninja Tricks---------------------------------------------------------------------->


history - gives the history of the commands you've run
	! and the number will allow you to rerun that command
	!! and the number will allow you to rerun the last command
	EX: !84; !85 will allow you to run the first step and the second step
	EX: !84 && !85 will make sure step 1 worked and then runs the second

ctrl a - moves to the begginging of the command line

ctrl arrow left and right - moves between arguements

ctrl k - this deletes the line from the position of teh cursor to the end of the line

ctrl l - to clear the command line

ctrl r - to search for a word in your history and places it in your line

ctrl u - clears the entire line

ctrl w - this delets the word before the cursor only

End - moves to the end of the command line

Home - move to the begginging of the command line

tab - to auto complete words or files as long as the command doesn't have multiple of the name being used

linux cert book filetype:pdf - this is how we find books




<------------------------------------------------Good ISH---------------------------------------------------------------------->

Htop - an interactive process viewer

http://rpmfind.net/ - this is used to find repositories for programs

logwatch - log analysis system. Logwatch parses through your system's logs and creates a report analyzing areas that you specify

Zorin - a good distro for Linux




<------------------------------------------------VI---------------------------------------------------------------------->

:Q! - get me the hell out of VI
a = append
dd = delete
i = insert
p = paste
shift zz - Save and exit
u = undo
x = delete