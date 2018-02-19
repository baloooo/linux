# Medium Linux Questions

* What do the following commands do and how would you use them?
* ```tee``` : command is used to store and view (both at the same time) the output of any other command.
```shell
   ls -1 *.txt | wc -l | tee count.txt
   # In this example the `ls` command lists all files in the current directory that have the filename extension .txt, one file per line; this output is piped to `wc`, which counts the lines and outputs the number; this output is piped to tee, which writes the output to the terminal, and writes the same information to the file "count.txt".
```
* ```awk``` : Short for "Aho, Weinberger, and Kernighan," It was designed to execute complex pattern-matching operations on streams of textual data. It makes heavy use of strings, associative arrays, and regular expressions, and is immensely useful for parsing system data and generating automatic reports.
```shell
    $ awk 'length($0) > 72' text.txt 
    # Print only lines of the file text.txt that are longer than 72 characters.
    $ awk '{ print $2, $1 }' data.txt
    # Print first two fields of data in oppeosite order.
```
* ```tr``` : The tr utility copies the standard input to the standard output with substitution or deletion of selected characters.
```shell
    $ tr "[:lower:]" "[:upper:]" < file1
    # Translates file1 content lowercase to uppercase
```
* ```cut``` : Remove or "cut out" sections of each line of a file or files.
```shell
    $ cut -f 1 -d ':' /etc/passwd
    # which will display username of all user in system
```
* ```tac``` : Concatenate and print files in reverse. reverse of cat
* ```curl``` : curl is a tool to transfer data from or to a server, using one of the supported protocols (HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, DICT, TELNET, LDAP or FILE). The command is designed to work without user interaction. 
```shell
    # Fetch the file index.html from www.domain.com using the HTTP protocol, and redirect data into index.html local file
    $ curl http://www.domain.com/index.html > index.html
```
* ```wget``` : wget is a free utility for non-interactive download of files from the web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies.
```shell
    # To download the file http://website.com/files/file.zip into local current directory.
    $ wget http://website.com/files/file.zip
```
* ```watch``` : watch is used to run any designated command at regular intervals. It highlight text which changed as compare to previous output.
```shell
    # which exectue "df -h" command every 10 seconds and highlight difference
    $ watch -d -n 10 df -h
```
* ```head``` : head, by default, prints the first 10 lines of each FILE to standard output.
* ```tail``` : tail, by default, prints the last 10 lines of each FILE to standard output. ```tail -f file.txt``` will display last lines of file and execute and update output periodically.
* What does an ```&``` after a command do?  What does ```& disown``` after a command do?
```shell
    https://unix.stackexchange.com/questions/3886/difference-between-nohup-disown-and
```
* What is a packet filter and how does it work?
> Packet filtering is a firewall technique used to control network access by monitoring outgoing and incoming packets and allowing them to pass or halt based on the source and destination Internet Protocol (IP) addresses, protocols and ports.

* What is Virtual Memory?
> It is a memory management technique that provides an "idealized abstraction of the storage resources that are actually available on a given machine" which "creates the illusion to users of a very large (main) memory.
> https://www.youtube.com/watch?v=qlH4-oHnBb8
> https://www.geeksforgeeks.org/virtual-memory-operating-systems/
```
* What is swap and what is it used for?
> Swapping is the process whereby a page of memory is copied to the preconfigured space on the hard disk, called swap space, to free up that page of memory. The combined sizes of the physical memory and the swap space is the amount of virtual memory available.

> Swapping is necessary for two important reasons. First, when the system requires more memory than is physically available, the kernel swaps out less used pages and gives memory to the current application (process) that needs the memory immediately. Second, a significant number of the pages used by an application during its startup phase may only be used for initialization and then never used again. The system can swap out those pages and free the memory for other applications or even for the disk cache.

> However, swapping does have a downside. Compared to memory, disks are very slow. Memory speeds can be measured in nanoseconds, while disks are measured in milliseconds, so accessing the disk can be tens of thousands times slower than accessing physical memory. The more swapping that occurs, the slower your system will be. Sometimes excessive swapping or thrashing occurs where a page is swapped out and then very soon swapped in and then swapped out again and so on. In such situations the system is struggling to find free memory and keep applications running at the same time. In this case only adding more RAM will help
```
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
```A record ```: Address record, Returns a 32-bit IPv4 address, most commonly used to map hostnames to an IP address of the host
```NS record ```: Name server record, Delegates a DNS zone to use the given authoritative name servers.
```PTR record ```: Pointer record, Pointer to a canonical name. Unlike a CNAME, DNS processing stops and just the name is returned. The most common use is for implementing reverse DNS lookups.
```CNAME ```: Canonical name record, Alias of one name to another: the DNS lookup will continue by retrying the lookup with the new name.
```MXRecord```: Mail exchange record, Maps a domain name to a list of message transfer agents for that domain
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
> Split DNS is a concept that allows a hostname to resolve to one IP address on the internal network, and another on the external network.Implementation of split-horizon DNS can be accomplished with hardware-based separation or by software solutions. Hardware-based implementations run distinct DNS server devices for the desired access granularity within the networks involved. Software solutions use either multiple DNS server processes on the same hardware or special server software with the built-in capability of discriminating access to DNS zone records. The latter is a common feature of many server software implementations of the DNS protocol (cf. Comparison of DNS server software) and is sometimes the implied meaning of the term split-horizon DNS, since all other forms of implementation can be achieved with any DNS server software.
* What is the sticky bit?
> https://unix.stackexchange.com/questions/79395/how-does-the-sticky-bit-work
* What does the immutable bit do to a file?
> used with ```chattr``` command. A file with the +i attribute cannot be modified.
It cannot be deleted or renamed, no link can be created to this file and no data can be written to the file.  When set, prevents, even the superuser, from erasing or changing the contents of the file.
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
> Underneath the file system files are represented by inodes (or is it multiple inodes not sure)
A file in the file system is basically a link to an inode.
A hard link then just creates another file with a link to the same underlying inode.
When you delete a file it removes one link to the underlying inode. The inode is only deleted (or deletable/over-writable) when all links to the inode have been deleted.
A symbolic link is a link to another name in the file system.
Once a hard link has been made the link is to the inode. deleting renaming or moving the original file will not affect the hard link as it links to the underlying inode. Any changes to the data on the inode is reflected in all files that refer to that inode.
Note: Hard links are only valid within the same File System. Symbolic links can span file systems as they are simply the name of another file.
* What is an inode and what fields are stored in an inode?
> The inode is a data structure in a Unix-style file system that describes a filesystem object such as a file or a directory. Each inode stores the attributes and disk block location(s) of the objects data. Filesystem object attributes may include metadata (times of last change,[2] access, modification), as well as owner and permission data.
[udacity short video](https://www.youtube.com/watch?v=tMVj22EWg6A)
* How to force/trigger a file system check on next reboot?
[Link](https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)
* What is SNMP and what is it used for?
[askubuntu explanation](https://askubuntu.com/questions/141564/what-is-snmp-used-for)
[digital ocean](https://www.digitalocean.com/community/tutorials/an-introduction-to-snmp-simple-network-management-protocol)
* What is a runlevel and how to get the current runlevel?
> A runlevel is one of the modes that a Unix -based operating system will run in. Each runlevel has a certain number of services stopped or started, giving the user control over the behavior of the machine. Conventionally, seven runlevels exist, numbered from zero to six.
> [See or change runlevels](https://askubuntu.com/questions/86483/how-can-i-see-or-change-default-run-level)
* What is SSH port forwarding or ssh tunneling?
> https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?
* Describe the mknod command and when you'd use it.
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
> https://unix.stackexchange.com/questions/182077/best-way-to-free-disk-space-from-deleted-files-that-are-held-open
> https://serverfault.com/questions/232525/df-in-linux-not-showing-correct-free-space-after-file-removal
* Describe how 'ps' works.
> https://unix.stackexchange.com/questions/262177/how-does-the-ps-command-work
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
> https://stackoverflow.com/questions/20688982/zombie-process-vs-orphan-process
* Explain briefly each one of the process states.
* How to know which process listens on a specific port?
* What is a zombie process and what could be the cause of it?
* You run a bash script and you want to see its output on your terminal and save it to a file at the same time. How could you do it?
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.
* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* Can you have several HTTPS virtual hosts sharing the same IP?
* What is a wildcard certificate?
* Which Linux file types do you know?
* What is the difference between a process and a thread? And parent and child processes after a fork system call?
* What is the difference between exec and fork?
* What is "nohup" used for?
* What is the difference between these two commands?
 * ```myvar=hello```
 * ```export myvar=hello```
* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you get Host, Channel, ID, LUN of SCSI disk?
* How can you limit process memory usage?
* What is bash quick substitution/caret replace(^x^y)?
* Do you know of any alternative shells? If so, have you used any?
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
