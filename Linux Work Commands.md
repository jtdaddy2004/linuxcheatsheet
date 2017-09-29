<------------------------------------------------Commands---------------------------------------------------------------------->

<------Leaving and Joining realm------>

sudo realm leave -U <login.name> -v
sudo realm join -U <login.name> -v


<------Yum Update----->

sudo yum update
sudo yum update "repository looking for"



<------Getting system info----->

cat /etc/os-release



<------Get Hostname----->
uname -n or hostname -s or -d



<------Get help----->
man "command" or --help


<------------FileServerScript------------->
./robot_family_parser.sh SUPERFAMILY.INI <......machine names ..... > FileServerFamilyOutput.txt

(make sure superfamily.ini and the robot script are in the shared folder for Virtual Box, this allows you to call the script and parse the superfamily.ini.  Then use the file servers you want to parse out of the document.  The > FileServerFamilyOutput.txt is the name of the file I wanted created)

