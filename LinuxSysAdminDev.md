Linux System Administrator/DevOps Interview Questions
====================================================

A collection of linux sysadmin/devops interview questions. Feel free to contribute via pull requests, issues or email messages.


## <a name='toc'>Table of Contents</a>

  1. [Contributors](#contributors)
  1. [General Questions](#general)
  1. [Simple Linux Questions](#simple)
  1. [Medium Linux Questions](#medium)
  1. [Hard Linux Questions](#hard)
  1. [Expert Linux Questions](#expert)
  1. [Networking Questions](#network)
  1. [MySQL Questions](#mysql)
  1. [DevOps Questions](#devop)
  1. [Fun Questions](#fun)
  1. [Demo Time](#demo)
  1. [Other Great References](#references)


#### [[⬆]](#toc) <a name='contributors'>Contributors:</a>

* [moregeek](https://github.com/moregeek)
* [typhonius](https://github.com/typhonius)
* [schumar](https://github.com/schumar)
* [negesti](https://github.com/negesti)
* peter
* [andreashappe](https://github.com/andreashappe)
* [quatrix](https://github.com/quatrix)
* [biyanisuraj](https://github.com/biyanisuraj)
* [pedroguima](https://github.com/pedroguima)
* Ben
* [bharatnc](https://github.com/bharatnc)


#### [[⬆]](#toc) <a name='general'>General Questions:</a>

* What did you learn yesterday/this week?
* Talk about your preferred development/administration environment. (OS, Editor,
  Browsers, Tools etc.)  
Answer: Windows, NotePad++, Visual Studio Code, Chrome. 
* Tell me about the last major Linux project you finished.
* Tell me about the biggest mistake you've made in [some recent time period] and how you would do it differently today. What did you learn from this experience?
* Why we must choose you?
* What function does DNS play on a network?
Answer: Domain Name System, is used to convert host name to ip address. 
* What is HTTP?  
Answer: Hyper Text Transfer Protocol

* What is an HTTP proxy and how does it work?  
Answer: An http proxy forwards http requests from an http client to an http
server, and receives responses from server and forwards back to the http
client.

* Describe briefly how HTTPS works.
Answer: Hypertext Transfer Protocol Secure.

* What is SMTP? Give the basic scenario of how a mail message is delivered via
  SMTP.
Answer: Simple mail transfer protocol.
Basic steps to send a mail message
HELO: Respond to server with its identify of FQDN (full qualified domain name)
MAIL FROM: Specify the originating email address. 
RCPT TO: Speficy a recipient. 
DATA: Transter the email body. End of data sequence is a new line, a single
period and another new line. 
QUIT: end the session
https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol

* What is RAID? What is RAID0, RAID1, RAID5, RAID10?  
Answer: RAID is Redundant Array of Inexpensive/Independent Disks.   
RAID 0, stripping without parity  
RAID 1, mirroring.  
RAID 5: one parity drive.  When one drive failed, rebuild needs to read from
all other drivers. 
RAID 10: Raid 1+0. Multiple RAID 1 form a RAID0. Top level is RAID0, sublevel
is RAID 1. Requires at least 4 drives. When a drive failed, rebuild only needs
to read from its mirror drive. 

* What is a level 0 backup? What is an incremental backup?  
Answer: level 0 backup is a full backup with meta data created. tar can do
level 0 and incremental backup.  
--listed-incremental=file or -g file option can create an incremental backup.
To do level 0 backup, we can remove the snapshot file before running the tar or 
by supplying the '--level=0' option.  
When use -g option first time to do tar dump, we have level 0 update. And meta
data, the snapshot file, will be created.  When use -g option again, we have 
incremental backup which will only dump the changed files. And the meta data
will be updated.   
Incremental dumps depend crucially on time stamp. Results will be unreliable if
you modifiy a file's time stamps or if you set the clock backwards.  
a. https://www.gnu.org/software/tar/manual/html_node/Incremental-Dumps.html  
b. man tar

* Describe the general file system hierarchy of a Linux system.
Answer:   
/: root directory
/dev: hold device files
/bin: essential user binaries
/sbin: system binaries
/mnt: mounted filesystem
/lib: shared libraries
/etc: system configuration files
/home: user home directories.
/boot: boot loader, grub files
/usr: User utilities and applications
/tmp: temporary files

* Which difference have between public and private SSH key?  
Answer: Two pairs of public and private keys are used by SSH. Host
private/public keys are created when ssh server is setup. User private/public
keys are created by user on cient machine. Pubic keyes are shared to peer while 
private keys are ketp secret. Public key is used to encrypt data and private key
is used to decrypt data. Ssh clients use host public key to encrypt data and the 
ssh server use host private key to decrypt data recieved. The ssh server uses the 
user public key to encrypt data and send to the ssh client. And the ssh client uses 
the user private key to decrypt data received.  
ssh used public and private keys for authentication. Symmetrical encryption is used
during a session for communication. The symmetrical encryption key is created by a key
exchange algorithm.  
https://hackernoon.com/ssh-keys-a-primer-7ac8b790e849
https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process
#### [[⬆]](#toc) <a name='simple'>Simple Linux Questions:</a>

* What is the name and the UID of the administrator user?  
Answer: the name is root and the UID is 0.
* How to list all files, including hidden ones, in a directory?  
Answer: ls -a  
* What is the Unix/Linux command to remove a directory and its contents?  
Answer: rm -rf
* Which command will show you free/used memory? Does free memory exist on Linux?
Answer: top, free and /proc/meminfo. free shows the memory of a snapshot. 
* How to search for the string "my konfu is the best" in files of a directory recursively?
* How to connect to a remote server or what is SSH?
* How to get all environment variables and how can you use them?  
Answer: printenv or env can print out all environment variables. The env
command can be used to run a command in a modified environment. The usage is
below:  
env [NAME=VALUE] [COMMAND] [ARG]
* I get "command not found" when I run ```ifconfig -a```. What can be wrong?
Answer: 
1. The corresponding package is not found. 
2. ifconfig is not in the PATH, try /sbin/ifconfig.
* What happens if I type TAB-TAB?
* What command will show the available disk space on the Unix/Linux system?
Answer: df command.
* What commands do you know that can be used to check DNS records?  
Answer: nslookup can be used. An example is below.
nslookup www.yahoo.com
* What Unix/Linux commands will alter a files ownership, files permissions?
* What does ```chmod +x FILENAME``` do?  
Answer: make the file executable.
* What does the permission 0750 on a file mean?
Answer: 4-read, 2-write, 1-executable
* What does the permission 0750 on a directory mean?
* How to add a new system user without login permissions?

* How to add/remove a group from a user?
Answer:  
To add a group to a user  
usermod -a -G groupname username  
To remove a group from a user  
gpasswd -d username groupname

* What is a bash alias?  
Answer: Alias is an abbreviation of a long command sequence. 

* How do you set the mail address of the root/a user?

* What does CTRL-c do?  
Answer: Send SIGINT, usually abort the program

* What does CTRL-d do?  
Answer: Send EOF or exit() for terminal program. 

* What does CTRL-z do?  
Answer: Send SIGSTP to the current process, make the process stopped and
become a background process. bg command can send SIGCONT to the process. If
the process is not waiting for standard input, it will run in the background.
If the process is waiting for standard input, it will remain stopped because bg
will not reconnect standart input to the process. To make the process enter
into running state, we can use fg command, which will connect the process to
standard input. 

https://superuser.com/questions/746350/stopped-process-doesnt-continue-to-work-after-sending-sigcont

* What is in /etc/services?

* How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)  
Answer:   
a. Redirect STDOUT and STDERR to the file of err.txt.
man -k hello > err.txt 2>&1  
Here the error info will be redirect to the file of err.txt.  
b. Redirect STDERR to STDOUT, and redirect STDOUT to err.txt  
man -k hello 2>&1 >err.txt  
Here err.txt will have nothing. Error info will still be printed on the
terminal.

* What is the difference between UNIX and Linux.
Answer: 
1. Code bases are different.
2. Unix  
* What is the difference between Telnet and SSH?

* Explain the three load averages and what do they indicate. What command can be used to view the load averages?
* Can you name a lower-case letter that is not a valid option for GNU ```ls```?
Answer: letter e
* What is a Linux kernel module?
Answer: a piece of codes that can be loaded into the kernel to extend kernel's
functionality. THe codes can also be unloaded from the kernel.  
* Walk me through the steps in booting into single user mode to troubleshoot a
  problem.
Answer: Edit grub menu entry, add "single" booting parameter and boot the entry.
* Walk me through the steps you'd take to troubleshoot a 404 error on a web
  application you administer.  
Answer:  
a. Retry the URL  
b. Check for errors in URL  
c. Move one directory at a time in the URL until you get something.  
d. Clear cache.  
e. Try a different browser and on a different machine.

* What is ICMP protocol? Why do you need to use?  
Answer: ICMP is Internet Control Message Protocol.
Ping utility is implemented using ICMP echo request and echo reply messages. 

https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol
#### [[⬆]](#toc) <a name='medium'>Medium Linux Questions:</a>

* What do the following commands do and how would you use them?
 * ```tee```  
 Answer: read from standard input and write to standard output and files.  
 Example 1. ls | tee file1 file2 file2  
 Example 2. program | tee file1 file2
 
 * ```awk```  
 Answer: a prwerful program to analyze and proces files. 
 Example 1. awk -F: '{print $1}' /etc/passwd
 * ```tr```  
 Answer: tr stands for translate.  
 Example 1. to replace all white places of a file to tab.  
 cat file1 | tr [:space:] '\t'
 * ```cut```  
 Answer: the command cuts sections of from each line of files and writing the
 result to standard output.  
 Example: print out the first field of file name.csv using delimiter of ":".  
 cut -d ":" -f 1 name.csv
 * ```tac```  
 Answer: the command concatenates and prints files in reverse.
 * ```curl```
 Answer: the command can used to transfer a url. It supports many protocols
 like FTP, HTTP, HTTPS, SCP, SFTP, SMBS, TELNET, TFTP etc... It supports login
 and cookie. It offers upload and send capabilities.
 See examples below.  
 Example:  
 curl --user user:pass --cookie-jar ./somefile https://xyz.com/a  
 curl --cookie ./somefile https://xyz.com/b
 
 * ```wget```
 Answer: Compare to curl, wget is able to download recursively. It supports
 FTP, HTTP and HTTPS. Support only HTTP POST, no upload and send capabilities.
 * ```watch```  
Answer: The command execute a program periodically, showing results full
screen.  
Example:   
a. run date command every 2 second.  
watch -n 2 date  
b. run df command every second  
watch -n 1 df
 * ```head```
Answer: display first part of a file  
Example:
head -n 10 /etc/passwd
 * ```tail```  
Answer: display last part of a file. When specify -f, output appended data as
the file grows.    
Example: tail -f -n 10 /var/log/messages 
 * ```less```
Answer: The command allows you to view the contents of a file and navigaet
through file. "less" tool is faster than "more" because it does not load the
entire file at once. F command for the tool will keep trying to read when the
end of file is reached. Can monitor the tail of a file like "tail -f".  
Example 1: less /var/log/autho.log  

 * ```cat```
Answer: The command concatenates files and prints out on the standard output.  
Example: cat file1 file2 file3 > file4  # concatates file1, file2, file3 to
file 4. 
 * ```touch```
Answer: The command can update the access and modification time of a file.  
Example 1: touch -c -t 201603051015 a.txt  
-c creates a file only when the file does not exist.  
Example 2: touch -a file1  # only change the access time of file1.  
Exapmle 3: touch -m file1  # change both the access and modification time of
file1.  
 * ```sar```
Answer: System Activity Reportor, sar, is a utitility from sysstat package.
Can monitor different activities include CPU, memory, swap, IO and kernel.  
Example 1: sar -P 1 2 3 # show cpu 1 usage 3 times with interval of 2 seconds.  
Example 2: sar -r 2 3  # report memory utilization statistics.

 * ```netstat```  
Answer: The command means network statistics.  
Example 1: netstat -rn  # show routing table
Example 2: netstat -au  # show all udp connections. -a means both listening and non-listening.
Example 2: netstat -at  # show all tcp connections

 * ```tcpdump```
 Answer: a packet sniffer tool. Can capture tcp, udp, icmp packets.
 Example 1: tcpdump -w 001.pcap -i eth0 
 Example 2: tcpdump -r 001.pcap  

 * ```lsof```  
Answer: lsof means list open files.
Example 1:  lsof   #list all open files
Example 2:  lsof -u $user   #list all files opened by $user
Example 3:  lsof -t $filename #list IDs of processes that opened a file
Example 4:  lsof -i 4tcp@bar:80  
The above command means list tcp specific files based on ipv4, tcp port 80 at host bar. 
4 - ipv4, tcp - tcp protocol, bar - host, :80 - port 80 

https://www.howtoforge.com/linux-lsof-command/
* What does an ```&``` after a command do?
Answer: start the command to run it at background
* What does ```& disown``` after a command do? 
Answer: the command will run at background and removed from the current shell.
Exit the current shell will not send SIGHUP to the command to kill it. 
More info about disown is below:  
disown -a remove all jobs from the current shell
disown -r remove running jobs from the current shell. 
disown %1 remove only job 1 from the current shell
Jobs removed from the current shell will not recieve SIGHUP when the current
shell exit. 
disown -h %1 will only mark the job 1 such that SIGHUP sent to the shell will
not be sent to the job 1. When list jobs using "jobs" command, we can still
see it. 
disown will not block SIGHUP signal from other processes.

* What is a packet filter and how does it work?  
Answer: Packet filtering is a firewall technique used to control network
access by mornitoring outgoing and incoming packets and allowing them to pass
or halt based on the source and destination IP addresses, protocols and ports.  
A packet filter is a program in software firewall that examines the headers of
each packet based on a specific rules to decide to prevent it from
passing(called DROP) or
allow it to pass(called ACCEPT)
  
* What is Virtual Memory?


* What is swap and what is it used for?  
Answer: swap is a space on a disk that is used when the amount of physical RAM
full. When a Linux system runs out of physical RAM, inactive pages are moved
from the RAM to the swap spae.

* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
   
Answer: The meanings of the records are below.
A record: map domain names to IPv4 addresses. An example is below.  
www.farsightsecurity.com. 3600 IN A 104.244.13.104
NS record: specify the name servers used by a domain. For example:  
ucla.edu. 3600 IN NS ns3.dns.ucla.edu.
ucla.edu. 3600 IN NS ns2.dns.ucla.edu.
ucla.edu. 3600 IN NS ns1.dns.ucla.edu.
ucla.edu. 3600 IN NS ns4.dns.ucla.edu.
CNAME record: make it possible for one domain name to point to another domain
name. For example:  
admissions.uoregon.edu. 300 IN CNAME drupal-cluster3.uoregon.edu.
MX record: defines the Mail eXchange records for a domain, or where inbound
email for a domain should be directed:  
farsightsecurity.com. 3600 IN MX 10 mail.fsi.io.  
In this case, mail intended for farsightsecurity.com email addresses get sent
via host mail.fsi.io.  

* Are there any other RRs and what are they used for?  
Answer: Here are some other DNS resource records. 
AAAA record: map domain name to IPV6 addresses
PTR record: Pointer record, maps IPv4 or IPv6 addresses to domain names. 
TXT record: Hold descriptive text, which is general information about a domain
name such as who is hosting it, contact person, phone number.  
SOA record: Start of Authorization Record, include properties for the zone
like name of the primary DNS server, email address of responsible person,
retry interval, etc...

* What is a Split-Horizon DNS?  
Answer: Split-Horizon DNS, Split-View DNS, or Split DNS is a facility of a DNS
implemation that provide different sets of DNS information, selected by the
source address of the DNS request. For example, seperate DNS servers can be
provided for internal and external networks 

* What is the sticky bit?  
Answer: Sticky bit is a user ownership access right flag that can be assigned to
files and directories.  
When a sticky bit is set for a directory, the files in the directory can only
be renamed or removed by the owner of the file or the super user.
To add a sticky bit, use chmod +t $file or chmod +t directory.
To remoev a sticky bit, use chmod -t $file or chmod -t directory.  
Sticky bit corresponds to the lowest bit of the special bits. For a permission of
1666, 1 means the sticky bit set and 666 means rw bits are set for ugo.
Two other special special permission bits are setuid bit and setguid bit.
setuid corresponds to 4(bit 2) of the special bits. 
An example of setuid is /usr/bin/passwd. The executable has setuid set and is
owned by root , when any user run the executable, the process will have
priviledge of root to update /etc/shadow to change the user's password.  
setgid correpsonds to 2(bit 1) of the special permission bits. when set on a
file and any user run the file will have the priviledge of the file's group. 
When setgid is set for a directory, the new files and subdirectories created
within it will inherit its group id.  
https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits   
https://en.wikipedia.org/wiki/Setuid  
https://en.wikipedia.org/wiki/Sticky_bit  

* What does the immutable bit do to a file?  
Answer: A file with immutable bit cannot be 
a. modified.  
b. renamed.  
c. removed. 
d. no hard link created by anyone including root.
Only root(superuser) or a process with  CAP_LINUX_IMMUTABLE capability can
set/clear the immutable bit to a file.  
To set the attribute
chattr +i /path/to/filename
To secure a directory 
chattr -R +i /path/to/folder
To clear the attribute
chattr -i /path/to/filename
To check the attribute, we can use the command of lsattr.  

* What is the difference between hardlinks and symlinks? What happens when you
  remove the source to a symlink/hardlink?  
Answer: A hard link points directly to the i-node of the files. A symbolic link
is an indirect pointer to a file. Hard links normally require that the link
and the file reside in the same file system. Only the superuser can create a
hard link to a directory (when supported by the underlying filesystem). On
Linux, ext2/ext3/ext4 does not support hard link to a directory. A symbolic link
does not have such a limit.  
When the source to a symlink is removed, the content of the file is deleted
and the symbolic link will become invalid. When the source to a hardlink is
removed, the content of the file will not be deleted, only the link count in
the inode will be decreased by 1. The hard link will not be affected. Renaming
the source will not affect the hard link as well.  

* What is an inode and what fields are stored in an inode?  
Answer: inode is a data structure that stores all information of a file on
Linux and other Unix-like operating systems except its name and its actual
data.    
* How to force/trigger a file system check on next reboot?  
Answer:   
a. for root partition, we can create an empty file of /forcefsck to trigger
file system check on the next reboot by "touch /forcefsck" 
b. 
* What is SNMP and what is it used for?
* What is a runlevel and how to get the current runlevel?  
Answer: A runlevel is a mode that a linux operating system will run in.   
0 - halt  
1 - single user text mode  
3 - multi-user text mode  
5 - multi-user graphical mode  
6 - reboot  
The command to get the current runlevel is "runlevel". 
* What is SSH port forwarding?
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?  
Answer: The MAJOR number of a special file specifies the driver associated
with the device. The MINOR number is used only by the driver specified by the
MAJOR number. Other part of the kernel don't use it. It is common for a driver
to control several devices and the minor number provides a way for the driver
to differerentiate among them. The MAJOR and MINOR numbers applies to both
character and block devices.
From *Linux Device Drivers* 

* Describe the mknod command and when you'd use it.
Answer: mknod is originally used to create char and block devices that
populate /dev. With introduction of udev, this is seldomly used in recent
Linux. 

* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being
  freed.
Answer: 
* Describe how 'ps' works.
Answer: We can use "strace ps" to find out how 'ps' works. On Linux, the
command will read /proc filesystem to find out process info. The info of
process with PID is under /proc/PID
  
* What happens to a child process that dies and has no parent process to wait
  for it and what’s bad about this?
Answer: The process will become a Zombie process. Zombie process released most
resources it taken and only consumes very little memory for keeping its entry
in the resource table. So if there are only few Zombie processes, it does not
affect Linux system much. There is a limit of maximum number of processes that
can run in Linux, which is shown in /proc/sys/kernel/pid_max. If there are too
many zombie processes, new processes cabe started. So if there are too many
zombie processes, then no new processes can be started.  
To claim a zombie process, we can send SIGCHLD to its parent. If it is not
working, we can kill its parent. There is also a trick to use gdb to attach
the zombie process's parent process to it, call waitpid for the zombie process
and then detach the parent process.  
https://serverfault.com/questions/575162/remove-a-zombie-process-from-the-process-table
https://askubuntu.com/questions/1118894/how-much-is-too-many-zombies-bad
 
* Explain briefly each one of the process states.
Answer: In Linux, we can use top or ps to find out the state of a process is
in. 
R: Running or runnable
D: Uninterruptible sleep (usually IO)
S: Interruptible sleep (waiting for a event to complete)
Z: defunct/zombie, terminated but not reaped by its parent. 
T: stopped, either by a job control signal or because it is traced. 
  
* How to know which process listens on a specific port?
Answer: 
1. lsof -i :80  
2. netstat -ltnp | grep -w ':80'  #-l listening, -t tcp, -n numeric, -p process id.
https://www.cyberciti.biz/faq/unix-linux-check-if-port-is-in-use-command/
https://www.tecmint.com/find-out-which-process-listening-on-a-particular-port/
* What is a zombie process and what could be the cause of it?
Anwer: A zombie process is a process which completed execution while its entry
is still in the process table to allow the parent to read the child's exit
status. The reason the process is a zombie is because it is "dead" but not yet
"reaped" by it's parent. Parent processes normally issue the wait system call
to read the child's exit status and removed the zombie. The kill command will
not work on zombie process. When a child dies, the parent will receives a
SIGCHLD signal.  
https://en.wikipedia.org/wiki/Zombie_process

* You run a bash script and you want to see its output on your terminal and save
  it to a file at the same time. How could you do it?
Answer: Use pipe to redirect the output to tee command and specify the file to
write to for the tee command. 
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.  
Answer: This command will enable ip forwarding on Linux so that a machine can
act as a router. A similar command that does the same is sysctl -w
net.ipv4.ip_forward=1. We can also set it permanently by writing to
/etc/sysctl.conf with the following entry.  
net.ipv4.ip_forward=1.  
IP forwarding is a concept to make Linux machine to send data from one network
to other. It can be enabled on a linux machine with two nics on two different
networks respectively.  
https://www.linuxnix.com/how-to-implement-ip-forwarding-in-linux/

* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* Can you have several HTTPS virtual hosts sharing the same IP?
* What is a wildcard certificate?
* Which Linux file types do you know?
* What is the difference between a process and a thread? And parent and child processes after a fork system call?
* What is the difference between exec and fork?
* What is "nohup" used for?  
Answer: Simiar to disown -h. A command that runs using nohup will not receive
SIGHUP when the current shell exits. Standard output will be redirected to
nohup.out by default if standnot specified. The reference below seems not
correct on Ubuntu when it mention that "One of the effects (the naming one) is that the
process won't receive any sent SIGHUP". I've tried on Ubuntu 19.04 and found
still we can use kill -SIGHUP pid to terminate the process that started using
hup.  
https://unix.stackexchange.com/questions/3886/difference-between-nohup-disown-and

* What is the difference between these two commands?
 * ```myvar=hello```
 * ```export myvar=hello```  
Answer: export make the variable visible to any process running from the
shell. A variable exported can be seen by the "env" command. If the variable
is not exported, we cannot see in the "env" command.  Also, the variable is
only visible to the shell.  

* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you get Host, Channel, ID, LUN of SCSI disk?
* How can you limit process memory usage?
* What is bash quick substitution/caret replace(^x^y)?
* Do you know of any alternative shells? If so, have you used any?
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
* How can you tell if the httpd package was already installed?
* How can you list the contents of a package?
* How can you determine which package is better: openssh-server-5.3p1-118.1.el6_8.x86_64 or openssh-server-6.6p1-1.el6.x86_64 ?
* Can you explain to me the difference between block based, and object based storage?

#### [[⬆]](#toc) <a name='hard'>Hard Linux Questions:</a>

* What is a tunnel and how you can bypass a http proxy?
* What is the difference between IDS and IPS?
* What shortcuts do you use on a regular basis?
* What is the Linux Standard Base?
* What is an atomic operation?
* Your freshly configured http server is not running after a restart, what can you do?
* What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?
* I've added my public ssh key into authorized_keys but I'm still getting a
  password prompt, what can be wrong?  
  Answer: Permission of the directory .ssh and the file authorized_keys could be
  wrong.

* Did you ever create RPM's, DEB's or solaris pkg's?
Answer: Use rpmbuild to build RPMs.

* What does ```:(){ :|:& };:``` do on your system?
* How do you catch a Linux signal on a script?
Answer: use trap in bash script.  
trap [COMMANDS] [SIGNALS]
An example to print a mesage when SIGINT or SIGTERM is caught is below:  
trap "echo Booh!" SIGINT SIGTERM

* Can you catch a SIGKILL?
Answer: SIGKILL(9) and SIGSTOP(17, 19, 23) cannot be caught, blocked or
ignored.  
* What's happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?
* Describe the linux boot process with as much detail as possible, starting from
  when the system is powered on and ending when you get a prompt.

* What's a chroot jail?  
Answer: chroot changes the apparent root directory of a process and its children. A
protgram that runs in such a modified environment cannot access files outside
the designated directory. The modified environment is callled a chroot jail.  
https://en.wikipedia.org/wiki/Chroot
* When trying to umount a directory it says it's busy, how to find out which PID
  holds the directory?
Answer: lsof $directory
* What's LD_PRELOAD and when it's used?
Answer: LD_PRELOAD is an optional environmental variable containing one or
more paths to shared libraries. It can be used to preload a shared library of
your own before other share libraries are loaded. 

* You ran a binary and nothing happened. How would you debug this?
* What are cgroups? Can you specify a scenario where you could use them?
* How can you remove/delete a file with file-name consisting of only non-printable/non-type-able characters?
* How can you increase or decrease the priority of a process in Linux?
Answer: renice 


#### [[⬆]](#toc) <a name='expert'>Expert Linux Questions:</a>

* A running process gets ```EAGAIN: Resource temporarily unavailable``` on reading a socket. How can you close this bad socket/file descriptor without killing the process?
* What do you control with swapiness?
* How do you change TCP stack buffers? How do you calculate it?
https://www.cyberciti.biz/faq/linux-tcp-tuning/
* What is Huge Tables? Why isn't it enabled by default? Why and when use it?
* What is LUKS? How to use it?


#### [[⬆]](#toc) <a name='network'>Networking Questions:</a>

* What is localhost and why would ```ping localhost``` fail?  
Answer: localhost corresponding to host address 127.0.0.1. Two factors that
could cause ```ping localhost``` fail.   
1. firewall blocked it. 
2. /proc/sys/net/ipv4/icmp_echo_ignore_all has value 1.  
* What is the similarity between "ping" & "traceroute" ? How is traceroute able to find the hops.
* What is the command used to show all open ports and/or socket connections on a machine?
* Is 300.168.0.123 a valid IPv4 address?  
Answer: No, 300 is larger than 256.
* Which IP ranges/subnets are "private" or "non-routable" (RFC 1918)?
* What is a VLAN?
* What is ARP and what is it used for?
* What is the difference between TCP and UDP?
* What is the purpose of a default gateway?
* What is command used to show the routing table on a Linux box?
* A TCP connection on a network can be uniquely defined by 4 things. What are those things?
* When a client running a web browser connects to a web server, what is the source port and what is the destination port of the connection?
* How do you add an IPv6 address to a specific interface?
* You have added an IPv4 and IPv6 address to interface eth0. A ping to the v4 address is working but a ping to the v6 address gives you the response ```sendmsg: operation not permitted```. What could be wrong?
* What is SNAT and when should it be used?
* Explain how could you ssh login into a Linux system that DROPs all new incoming packets using a SSH tunnel.
* How do you stop a DDoS attack?
* How can you see content of an ip packet?
* What is IPoAC (RFC 1149)?
* What will happen when you bind port 0?



#### [[⬆]](#toc) <a name='mysql'>MySQL questions:</a>

* How do you create a user?  
Answer: Use CREATE USER command.

* How do you provide privileges to a user?
* What is the difference between a "left" and a "right" join?
* Explain briefly the differences between InnoDB and MyISAM.
* Describe briefly the steps you need to follow in order to create a simple master/slave cluster.
* Why should you run "mysql_secure_installation" after installing MySQL?
* How do you check which jobs are running?
* How would you take a backup of a MySQL database?

#### [[⬆]](#toc) <a name='devop'>DevOps Questions:</a>

* Can you describe your workflow when you create a script?
* What is GIT?
Answer: It's a free and open-source distributed version control system developed by Linus.
* What is a dynamically/statically linked file?  
Answer: A file linked to dynamic library/static libary.  
dynamic library: The library code is position independent. Needs to be available
during compiling and running time. The library codes is only linked but not in
the executable file. 
static libary: The library object codes will be linked and become part of the
executable.  
There are two ways to use the dynamic library.  
a. Dynamically linked at run time.  
b. Dynamically loaded/unloaded and linked during execution using the dynamic
linking loader system calls such as dlopen, dlsym and dlclose.   
http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html  
* What does "./configure && make && make install" do?
* What is puppet/chef/ansible used for?
* What is Nagios/Zenoss/NewRelic used for?
* What is Jenkins/TeamCity/GoCI used for?  
  Answer: They are used for continuous integration. When developers integrate
  into a shared repository, the integration will be verified by an automated
  build and automated tests. This way, we can detect errors quickly and locate
  them more easily.

* What is the difference between Containers and VMs?  
Answer: VMs emulate a hardware system. Within each virtual machine runs a
guest operating system. Each VM has its own binaries, libraries and
applications that it services and may consume many gigabytes.  
Containers sit on top of a physical server and its host OS. Each contrainer
shares the host OS kernel and usually binaries and libraries too. Containers
are light, only megabytes in size and just take seconds to start. 
  
* How do you create a new postgres user?
* What is a virtual IP address? What is a cluster?
* How do you print all strings of printable characters present in a file?  
Answer: strings /path/to/filename  
* How do you find shared library dependencies?
Answer: use command "ldd $executable"
* What is Automake and Autoconf?  
Answer: Autoconf and Automake are executables of the autotools.  
Autoconf is used to generate the configure script, from a template named
configure.ac. The configure script will check all characteristics of the host
system and generate the makefiles from Makefile.in templates.  
Autocmake is used to generate complete Makefile.in templates, following GNU
standards from very simple Makefile.am templates.  
https://developer.gnome.org/anjuta-build-tutorial/stable/create-autotools.html.en
* ./configure shows an error that libfoobar is missing on your system, how could
  you fix this, what could be wrong?  
Answer: Configuration cannot find the libfoobar in LD_LIBRARY_PATH or the
packagnot instaslled. To fix it, we can install the package or build it from
its source. If libfoobar is already is installed, we can check /etc/ld.so.conf
and add the library into it.  
* What are the advantages/disadvantages of script vs compiled program?
Answer: Advantages of script vs compiled program  
a. No need to compile.  
b. Faster to develop and size is small.
c. Can be more portable.   
Disadvantages of script vs compiled program  
a. Execution is slower.  
b. Source code is open and cannot be hided from end user.  
* What's the relationship between continuous delivery and DevOps?
* What are the important aspects of a system of continuous integration and deployment?
* How would you enable network file sharing within AWS that would allow EC2 instances in multiple availability zones to share data?

#### [[⬆]](#toc) <a name='fun'>Fun Questions:</a>

* A careless sysadmin executes the following command: ```chmod 444 /bin/chmod ``` - what do you do to fix this?  
Answer: use some other way to call chmod system call to fix the /bin/chmod.  
a. use install command with option -m 
b. use pyhon or perl script to call chmod function. For python, we can use os.chmod function.

* I've lost my root password, what can I do?
Answer: 
Approach 1: use a live CD (a Knoppix CD or some other live CD).
1. Boot into the live CD.
2. Mount the partition of the drive that contains /etc/passwd.
3. Run chroot 
4. Run passwd to change root password and then reboot. 
Approach 2. Change grub2 entry 
1. Change grub boot entry and boot the entry
a. change ro to rw for root partition
b. add init=/bin/bash
2. After booting, run passwd to change password.

* I've rebooted a remote server but after 10 minutes I'm still not able to ssh into it, what can be wrong?  

* If you were stuck on a desert island with only 5 command-line utilities, which
  would you choose?      

* You come across a random computer and it appears to be a command console for the universe. What is the first thing you type?
* Tell me about a creative way that you've used SSH?
* You have deleted by error a running script, what could you do to restore it?
Answer: Since the script is running, its contents is not removed from the file
system, we can still restore it.  
Let's say we have a bash script named myscript.sh running. We can run "ps aux
| grep myscript.sh". It will show a process with command line of "/bin/bash
myscript.sh" and its pid is PID. The script will be opened by the process.
Then we can search in /proc/PID/fd/ to find the file descriptor FD. Then we
can do cat FD > /tmp/myscript.sh to restore the file.  

* What will happen on 19 January 2038?  
  Answer: A signed integer was used to represent the number of seconds passed
  since 1 January 1970. The implementation will not be able to encode the time
  correctly after some time on 19 January 2038.

* How to reboot server when reboot command is not responding?  
  Answer: If the sysrq is enabled, /proc/sys/kernel/sysrq has a value of 1. We
  can use the magic SysReq commands to do perform a safe reboot using the
  sequence of "reisub".  
  reisub- Raising Elephant Is So Utterly Boring.  
  They represent unRaw, Terminate, Kill, Sync, Unmount, Reboot.

  https://en.wikipedia.org/wiki/Magic_SysRq_key




#### [[⬆]](#toc) <a name='demo'>Demo Time:</a>

* Unpack test.tar.gz without man pages or google.  
Answer:  
To unpack   
tar -xzvf test.tar.gz   
To pack  
tar -czvf test.tar.gz test_dir  
* Remove all "*.pyc" files from testdir recursively?
* Search for "my konfu is the best" in all *.py files.
* Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files.
* Test if port 443 on a machine with IP address X.X.X.X is reachable.

* Get http://myinternal.webserver.local/test.html via telnet.
* How to send an email without a mail client, just on the command line?
* Write a ```get_prim``` method in python/perl/bash/pseudo.
* Find all files which have been accessed within the last 30 days.
* Explain the following command ```(date ; ps -ef | awk '{print $1}' | sort |
  uniq | wc -l ) >> Activity.log```  
Answer: date; will print out the current system date and time.
ps -ef will show all processes in full format. awk '{print $1}' will print out
the first field, which is UID. sort will further sort the UID. And
uniq will only show the different UIDs. wc -l will count the number of
different users.  
So this script will append the current system date and time and then the
number of active users to the file of Activity.log.  
* Write a script to list all the differences between two directories.  
Answer: diff -Naur dir1 dir2

* In a log file with contents as ```<TIME> : [MESSAGE] : [ERROR_NO] - Human readable text``` display summary/count of specific error numbers that occurred every hour or a specific hour.


#### [[⬆]](#toc) <a name='references'>Other Great References:</a>

Some questions are 'borrowed' from other great references like:

* https://github.com/darcyclarke/Front-end-Developer-Interview-Questions
* https://github.com/kylejohnson/linux-sysadmin-interview-questions/blob/master/test.md
* http://slideshare.net/kavyasri790693/linux-admin-interview-questions