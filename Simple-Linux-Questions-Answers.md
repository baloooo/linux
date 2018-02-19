# Simple Linux Interview Questions:</a>
* What is /dev?
```shell
This is the name of the directory in which all device files reside. Since partitions reside on hard disks, and hard disks are devices, the files representing all possible partitions reside in /dev/.
```
* How are device partitions named?
```shell
https://unix.stackexchange.com/questions/3158/hard-drive-device-partition-naming-convention-in-linux
```
* What is the name and the UID of the administrator user?
```shell
	root# echo $UID
	0
	root# cat /etc/passwd | grep ^root
	root:*:0:0:System Administrator:/var/root:/bin/sh
```
* How to list all files, including hidden ones, in a directory?
```shell
	$ ls -la ./
	total 4656
	drwxr-xr-x@ 19 paras.patel	679754705			646 Aug 16 19:11 .
	drwxr-xr-x+ 94 paras.patel	679754705		 3196 Sep	3 23:12 ..
	-rw-r--r--@	1 paras.patel	679754705		 6148 Sep	3 22:56 .DS_Store
	-rw-r--r--	 1 paras.patel	679754705			268 Apr 19 16:18 .dockeralias
	-r--------@	1 paras.patel	679754705		 1696 Jan 16 Prog_Practice
	drwxr-xr-x	 8 paras.patel	679754705			272 Apr 26 13:59 Dockerfile
```
* What is the Unix/Linux command to remove a directory and its contents?
```shell
	$ rm -r	$file_directory_path
```
* Which command will show you free/used memory? Does free memory exist on Linux?
```shell
	$cat /proc/meminfo
	MemTotal:				8120568 kB
	MemFree:				 2298932 kB
	Cached:					1907240 kB
	SwapCached:						0 kB
	SwapTotal:			15859708 kB
	SwapFree:			 15859708 kB
	$ free -m (free output in MB or free -h for human readable)
	total			 used			 free		 shared		buffers		 cached
	Mem:					 750				625				125					0				 35				335
	-/+ buffers/cache:				254				496
	Swap:					956					0				956
	$ top
	$ htop #also useful to check memory usage try it by yourself
```
* How to search for the string "my konfi is the best" in files of a directory recursively?
```shell
	grep -r "my konfi is the best" ./
```
* How to connect to a remote server or what is SSH?
```shell
	$ ssh remote_username@remote_host
```
* How to get all environment variables and how can you use them?
```shell
	$ env # will list all environmental variables
	$ echo $SHELL	# $SHELL is system variables
	/bin/bash
```
Also you can add it to your ~/.profile or ~/.bashrc file.
```shell
	$ export PATH=$PATH:/path/to/dir
```
 
* I get "command not found" when I run ```ifconfig -a```. What can be wrong?
```shell
	# if system is windows you need to use ipconfig some time $PATH variable missing ifconfig PATH
	$ /sbin/ifconfig
```
* What happens if I type TAB-TAB?
```shell
	# [TAB]-[TAB] is also know as tab completion is common feature of command line interpreters in which the program automatically fills in partially typed commands. It behaves according to command in prefix.
	e.g.
	$ write [TAB][TAB]
	balaji			raju
	jason		 rando
	john			ritu
	paras		 www-data

	$ telnet [TAB][TAB]
	localhost	dev-db	fileserver
```
* What command will show the available disk space on the Unix/Linux system?
```shell
	# df command use to check disk space
	$ df -h
	Filesystem			Size	 Used	Avail Capacity	iused		ifree %iused	Mounted on
	/dev/disk1		 233Gi	143Gi	 90Gi		62% 37488174 23497168	 61%	 /
	devfs					328Ki	328Ki		0Bi	 100%		 1134				0	100%	 /dev
	map -hosts			 0Bi		0Bi		0Bi	 100%				0				0	100%	 /net
	map auto_home		0Bi		0Bi		0Bi	 100%				0				0	100%	 /home
	map -fstab			 0Bi		0Bi		0Bi	 100%				0				0	100%	 /Network/Servers
	# free command is simple and easy to use command to check memory usage on Linux
	$ free -m
							 total			 used			 free		 shared		buffers		 cached
	Mem:					7976			 6459			 1517					0				865			 2248
	-/+ buffers/cache:			 3344			 4631
	Swap:				 1951					0			 1951
	$ cat /proc/meminfo
	MemTotal:				8167848 kB
	MemFree:				 1409696 kB
	Buffers:					961452 kB
	Cached:					2347236 kB
	SwapCached:						0 kB
	Active:					3124752 kB
	Inactive:				2781308 kB
	Active(anon):		2603376 kB
	Inactive(anon):	 309056 kB
	Active(file):		 521376 kB
	Inactive(file):	2472252 kB
	Unevictable:				5864 kB
	Mlocked:						5880 kB
	SwapTotal:			 1998844 kB
	SwapFree:				1998844 kB
	Dirty:							7180 kB
	Writeback:						 0 kB
	AnonPages:			 2603272 kB
	Mapped:					 788380 kB
	Shmem:						311596 kB
	Slab:						 200468 kB
	SReclaimable:		 151760 kB
	SUnreclaim:				48708 kB
	KernelStack:				6488 kB
	PageTables:				78592 kB
	NFS_Unstable:					0 kB
	Bounce:								0 kB
	WritebackTmp:					0 kB
	CommitLimit:		 6082768 kB
	Committed_AS:		9397536 kB
	VmallocTotal:	 34359738367 kB
	VmallocUsed:			420204 kB
	VmallocChunk:	 34359311104 kB
	HardwareCorrupted:		 0 kB
	AnonHugePages:				 0 kB
	HugePages_Total:			 0
	HugePages_Free:				0
	HugePages_Rsvd:				0
	HugePages_Surp:				0
	Hugepagesize:			 2048 kB
	DirectMap4k:			 62464 kB
	DirectMap2M:		 8316928 kB
	$ vmstat -s
	$ top
	$ htop
```
* What commands do you know that can be used to check DNS records?
```shell
    Complete list: https://blog.dnsimple.com/2015/04/common-dns-records/
    Noteworthy:
        https://support.dnsimple.com/articles/a-record/
	$ nslookup www.google.com
	Server:		172.20.10.1
	Address:	172.20.10.1#53

	Non-authoritative answer:
	Name:	www.google.com
	Address: 172.217.25.228
	$ dig www.google.com +nostats +noquestion

	; <<>> DiG 9.8.3-P1 <<>> www.google.com +nostats +noquestion
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20876
	;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

	;; ANSWER SECTION:
	www.google.com.		192	IN	A	172.217.25.228

	# Find out domain IP
	$ host -t a	github.com	 (-t is query type, a is A record)
	github.com has address 192.30.253.112
	github.com has address 192.30.253.113
	# Find out domain mail Server
	$ host -t mx github.com
	github.com mail is handled by 5 ALT2.ASPMX.L.GOOGLE.com.
	github.com mail is handled by 10 ALT4.ASPMX.L.GOOGLE.com.
	github.com mail is handled by 10 ALT3.ASPMX.L.GOOGLE.com.
	github.com mail is handled by 5 ALT1.ASPMX.L.GOOGLE.com.
	github.com mail is handled by 1 ASPMX.L.GOOGLE.com.
	# Find Out the Domain Name Servers
	$ host -t ns github.com
	github.com name server ns1.p16.dynect.net.
	github.com name server ns2.p16.dynect.net.
	github.com name server ns4.p16.dynect.net.
	github.com name server ns3.p16.dynect.net.

	# Find Out the Domain TXT Recored
	$ host -t txt github.com
	github.com descriptive text "docusign=087098e3-3d46-47b7-9b4e-8a23028154cd"
	github.com descriptive text "v=spf1 ip4:192.30.252.0/22 include:_spf.google.com include:esp.github.com include:_spf.createsend.com include:mail.zendesk.com include:servers.mcsv.net ~all"

	# Find out cname and soa record
	$ host -t cname github.com
	github.com has no CNAME record
	# Find out start of authority (SOA) record which is information stored in a domain
	$ host -t soa github.com
	github.com has SOA record ns1.p16.dynect.net. hostmaster.github.com. 1472666705 3600 600 604800 60
```
* What Unix/Linux commands will alter a files ownership, files permissions?
```shell
	$ chown options owner-user:owner-group file/directory
```
* What does ```chmod +x FILENAME```do?
		* ``+x`` means we are adding file execution permission for all user, group and others
* What does the permission 0750 on a file mean? or What does the permission 0750 on a directory mean?
```
	->	1st bit(0) sticky-bit (This bit is commonly set to directories and means that you may only remove file in such a directory that are owned by you. The filesystem /tmp is commonly set with that bit)
	->	2nd bit(7) file-owner may read(4) + write(2) + execute(1) file
	->	3rd bit(5) file-group may read(4) and execute(1) file
	->	4th bit(0) other-user can't do anything with this file
```
* How to add a new system user without login permissions?
```shell
	# create system user without home directory
	$ adduser --system --no-create-home
```
* How to add/remove a group from a user?
```shell
	$ usermod -G "" username
```
* What is a bash alias?
	* Bash allows us to create our own shortcuts and time-savers through the use of aliases and shell functions. e.g. ```$ alias alias_name="command_to_run"```
* How do you set the mail address of the root/a user?
	* Simply create /root/.forward and place your email address in this file. It will be forwarded to your external mail address. ```myaddress@example.com, root@thisserver.com ```
* What does CTRL-c do?
	* ```Ctrl + C``` is used to kill a process with signal ```SIGINT``` , by other words it is a polite kill . ```Ctrl + Z``` is used to suspend a process by sending it the signal ```SIGSTOP```.
* What is in /etc/services?
	* The configuration file /etc/services maps port numbers to named services. Key point: Its role in life is so that programs can do a ```getportbyname()``` sockets call in their code in order to get what port they should use.
* How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)
	* The file descriptors for stdin, stdout, and stderr are 0, 1, and 2, respectively.
	```shell
			1>filename
			# Redirect stdout to file "filename."
			1>>filename
			# Redirect and append stdout to file "filename."
			2>filename
			# Redirect stderr to file "filename."
			2>>filename
			# Redirect and append stderr to file "filename."
			&>filename
			# Redirect both stdout and stderr to file "filename."
			2>&1
			# Redirects stderr to stdout.
	```
* What is the difference between UNIX and Linux.
	* Linux is an open source, free to use operating system widely used for computer hardware and software, game development, tablet PCS, mainframes etc. Unix is an operating system commonly used in internet servers, workstations and PCs by Solaris, Intel, HP etc.
	*	Linux kernel is developed by the community. Linus Torvalds oversees things. hree bigest distributions are Solaris (Oracle), AIX (IBM) & HP-UX Hewlett Packard. And Apple Makes OSX, an unix based os.
	*	e.g. Linux : Ubuntu, Fedora, Red Hat, Debian, Archlinux, Android etc.	UNIX : HP-UX, IBM AIX, Sun Solairs, Mac OS X, IRIX
* What is the difference between Telnet and SSH?
	* SSH and Telnet commonly serves the same purpose
	* SSH and Telnet runs on port 22 and 23 respectively
	* SSH is more secure compared to Telnet
	* SSH encrypts the data while Telnet sends data in plain text
	* SSH uses a public key for authentication while Telnet does not use any authentication
	* SSH adds a bit more overhead to the bandwidth compared to Telnet
	* Telnet has been all but replaced by SSH in almost all uses
* Explain the three load averages and what do they indicate
	```shell
	$ uptime
	20:29	up 34 days, 11:04, 5 users, load averages: 1.05, 0.7, 5.09

	# load average over the last 1 minute: 1.05
	# load average over the last 5 minutes: 0.7
	# load average over the last 15 minutes: 5.09

	# In case assume you have single-core proecessor then pridiction is like this
	# over the last 1 minute: The computer was overloaded by 5% on average. On average, .05 processes were waiting for the CPU. (1.05)
	# over the last 5 minutes: The CPU idled for 30% of the time. (0.70)
	# over the last 15 minutes: The computer was overloaded by 409% on average. On average, 4.09 processes were waiting for the CPU. (5.09)
	```
* Can you name a lower-case letter that is not a valid option for GNU ```ls```?
	* lower-case letter ```z``` is not a valid option for GNU e.g.
	```shell
	$ ls -z
	ls: illegal option -- z
	usage: ls [-ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1] [file ...]
	```
