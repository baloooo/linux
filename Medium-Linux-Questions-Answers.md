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
* What does an ```&``` after a command do?
* What does ```& disown``` after a command do?
* What is a packet filter and how does it work?
> Packet filtering is a firewall technique used to control network access by monitoring outgoing and incoming packets and allowing them to pass or halt based on the source and destination Internet Protocol (IP) addresses, protocols and ports.

* What is Virtual Memory?
* What is swap and what is it used for?
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
* What is the sticky bit?
* What does the immutable bit do to a file?
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
* What is an inode and what fields are stored in an inode?
* How to force/trigger a file system check on next reboot?
* What is SNMP and what is it used for?
* What is a runlevel and how to get the current runlevel?
* What is SSH port forwarding?
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?
* Describe the mknod command and when you'd use it.
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
* Describe how 'ps' works.
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
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
