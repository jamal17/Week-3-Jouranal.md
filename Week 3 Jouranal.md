#How Linux Works: What Every Superuser Should Know Chapter's 2 & 3 “Commands, Directory Hierarchy, and Devices”


                                                          **Chapter 2**

shell /bin/sh: it’s very important on unix system. it’s the one run the commands.

Shell script it’s a text file that have a sequence of shell commands, and it’s very powerful.

The good think about shell when we make a mistake it will be very easy to see what we typed wrong.



**Shell command**:

cat. it’s simply outputs the contens of on or more files.

Ctrl-d to terminale cat and return to the shell prompt.

ls: it’s the contents of directory. Use ls-l for a detaild(long) and ls -F to disply file type information.

cp: to copy file example to copy file1 to file2. Command is $ cp file1 file2.

mv: (moved) command is like cp it is renames a file. Like rename file1 to file2.

Commands is $ mv file1 file2.

touch: to creates a file if the file is exist the touch does not change it, but does update the file.

Command is $ touch file.  Then run ls -l on that file we will see the output like the user name date and time with

**file name**.

rm: (remove) a file to delete. The command of rm with out -i it will delete and removed the file from the system.

echo: it is printed its arguments to the standard output like. $ echo Hello again.

Output willl be  Hello again.

 

                                                               **Note**.

All command, option file name etc. are case sensitive.

                                                               **Note**.

On computer system is stored everything in the file, so this file will have it is own data and filenames.

 
Navigation Directories: in Linux has a directory hierarchy that start at /, some time called root directory.

it’s separator is the slash(/), not the back slash(\).

One dot(.) refer the shell’s current working directory.

Two dote(..) it is for a path component.

cd: to change the shell’s current working directory.

mkdr: to creat a new directory dir.

pwd: print working directory.

rmdir: removes the directory dir.

Shell globbing(wildcards): the shell can match simple pattern to file and directory names. This process known at globbing.

at* expands to all filenames that start with at .

*at expands to all filenames that end with at.

*at* expand to all filenames that contain at.


**Intermediate Commands**:

grep:  print the line from the file.

Commands type is $ grep root /etc/*

the most important grep option are -i(for case-insensitive matches) and -v(inverts the serch,print all lines do not match).

*matches any number of characters(like the * in wildcards). match one arbitrary character.

less: it’s come in handy when a file is really big or when a commands output is long.

diff:  $ diff file1 file2 text file. To see the different between two text file.

Most programmers prefer the output from diff -u when they need to send the output to someone else because automated
tools can make better use of it.

file: it is use to see if the system can guess.

Find and locate: run find to find file in dir. $ find dir -namefile-print.

Head and tail: to quickly show a portion of a file or stream of data.

$head/etc/passwd it will show the first 10 line of the passwd file, and tail/etc/passwd it show the last 10 line.

The -n option is use to change the number of line examp. Head -5/etc/passwd.

Sort:  to sort the line of text file in alphanumeric order.

Dot file: (change to home directory).$ ls -a it will show the output all file that start with dot.

**Command path**:

$ echo $ path. It’s tell the shell to look in more place for programs, change the path environment variable.

Shell Input and Output: to send the output of command to a file not to teminal, we use the ( $ command) file.

Killing processes: ( to terminate a process). $ kill pid.

Also we can to freeze a process instead of terminating, we can use stop signal. $ kill_stop pid.

To continue to running the process again. $ kill-CONT pid.


**File and permissions**: all file in UNIX has a set of permissions.

-rw-r--r

To modifying permissions, we use a command $ chomd.

$ chomd g+r file.  Add group(g)

$ chomd o+r file.  Add world(o)

or all in one $ chomd go+r file.

To remove all these permissions.

$ chomd go-r file.


**Archiving and Compressing**:  

gzip :( it is standard UNIX compression program). Any file end with gzip is a GNU zip archive.

tar: ( to create an archive) unlike the gzip. $ tar cvf arachive. Tar file1 file2.

zcat: ( it is a pipeline unpacks) it is the same as gunzip -dc. The -d its process and -c sends the result to the standard output.

$ tar file. Tar -gz| tar xvf.

$ tar ztvf file -tar.gz.

 

                                                               **Chapter 3**

Driver File: Linux it’s all files. Kernel it’s present many of the devices to the user of files, and the called(device nodes).


                                                                **Notes**
                                                                
we do not have to be a programmer to use a devices, because some device are accessible to standard programmer
like cat, but there is a limit to what we can to do with file interface, so not all devices are accessible with
standard file I/O.

Device file are in the /dev directory and running ls/dev .

To start with device we have to consider with this command.

$ echo bla bla > /dev/null

in the case of /dev/null, the kernel simply ignores the input and throws a way the data.

To identify a device and view its permission. We use  $ ls -l 

Block device: It’s the room for the programmer to access data in fixed chunks.

The disk device is a type of block device.

The disk can be easily to split up into block of data, because a block device it’s fixed and easy to index, and the user
processor they have a random access to any block device using a help of the kernel.

Character device: It’s work with data streams, so character device is only read character by character like a keyboard, printer.


                                                               **Notes**.

during character device interaction, the kernel can not back up the data stream after it has passed data to a device or process.

Pipe device: It’s just like a character device. Is used in linux and other UNIX-like OS to send
the output of one program to another program.

Socket device: they are a special-purpose interface are frequently used for inter process communication.

The socket device they are often found outside of the /dev directory.

 

                                                                **Note**.

Not all device in Linux have a device file, because the block and character devices I/O interfaces are not Appropriate
in all case. The good example, the network device because the network device does not have device files. 

The sysfs device path: this device it’s a feature of the Linux kernel that makes kernel information available to the user processes, 
but there is a problem is that the kernel assigns device in order in which they are found, so a device may have a different name 
between reboots.

dd and device:  it’s very useful when is working for block and character devices, because is read from an

input file or stream and write to an output file or stream.

The command is $ dd if=/dev/zero of=new_file bs=1024 count=1

We should to know. We have to becarful when we run dd file we have to know what we are doing.

It’s very easy to crash the file and data on devices by making any mistake.

Hard disk:  /dev/sd*

most hard disk attached to Linux system correspond to device names with sd prefix, the sd portion of the name stand
for SCSI disk. Small computer system interface(SCSI).

To list the SCSI device in the system.

$ lssci

CD and DVD /dev/sr*:

the Linux recognize most optical storage drive as the SCSI device/dev/sro, /dev/srl.

udevd operation and configuration: it’s operates as follows.

kernel sends udevd a notification event, called a uvent if these devices are add or removed from the system.

udev rules.

When a rule matching event information is found it can be used:

1. to define the name and path of device file.

2. to define the owner group and permissions of a device file.

3. to execute a specified program.

udevadm: it’s the tool that expects a command and command specific option for udevd. It’s a powerful feature

of udevadm are the ability to search for and explore system device and the ability to monitor uevent as udevd receives
them from kernel.

For device such as  /dev/sda, run the following commands.

$ udevadm info – query=all—name=/dev/sda.

**Monitoring device**: to monitor uevent with udevadm, we will use the monitor command.

$ udevadm monitor

the output message will be two copies, because the default behavior is to print both the incoming message from

the kernel and the message that udevd send out to other programs after finished processing and filtering the event.

 

                                                                **Note**.

To see only kernel events we have to add kernel option.

$ udevadm monitor—kernel—subsystem-match=SCSI.




R.1– 1 pt

Debian 7.7 Manual Page [1]



1.Torbjorn Granlund, David MacKenzie, and Paul Eggert "man page for df (debian section 1)" GNU coreutils 8.12.197-032bb., 
September 2011. Accessed September 5, 2017. url:www.unix.com/man-page/debian/1/df/

 
2.Ward, Brian. How Linux Works: What Every Superuser Should Know. No Starch Press, 2015.

 

