<<<<<<< HEAD
# Linux file systemq
=======
# Linux file system
>>>>>>> master

In Linux, everything is a file, or at least can be treated like one. It is important to know how to navigate the file system effectively and interact with files.

## Navigation
1. create the following directory structure here: this/is/a/directory
<<<<<<< HEAD
  - what are the commands you used?  
mkdir this  
mkdir is  
mkdir a  
mkdir directory  
cd this/is/a/directory
  - read the mkdir man page to find out which switch to use to create those directories in one command
mkdir -p this/is/a/directory
  - change into the new directory. note the command you use here
cd this/is/a/directory  
1. type "cd -"
  - What did that do?  
yielded: "/home/balihoo.local/edanthinne/git-linux-practice/file-system", the file where the list directory is located
1. type "cd ~"
  - What did that do?  
changed directory back to home directory
  - go back to the directory containing this file. note the command you use.  
"cd git-linux-practice/file-system/this/is/a/directory/"
1. copy the output of the command "history" below.
  - what are the numbers before the commands?  
command numbers--can be used to reference the commands
  - what happens when you use the command "!<number>" ?  
will execute the command respective to the number
  - if you ended up away from this directory, get back to the one containing this file
  - copy the output of the 'pwd' command here. What does that do?  
output: "cd git-linux-practice/file-system/this/is/a/directory/";  
shows my current location
1. use the 'ls' command to list the contents of the current directory
  - what does 'ls ~' show you  
shows the contents of the home directory
  - what does 'ls .' show you  
shows the contents of the current directory
  - what does 'ls ..' show you  
shows the contents of the parent directory
  - what does 'ls /' show you?  
"bin  boot  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  vmlinuz"  
references the primary directory ("edanthinne@edanthinne-t1600:/")
  - what does 'ls this/../this/is/../is/' show you? explain why.  
shows the content of the 'is' directory  
navigates to this, then parent folder file-system, then this, then is, then parent file this, then is
  - skim the man page
  - what switch do you use for the long listing  
use -l switch for long listing format
  - what do the columns mean?  
1: who has access to what (users, group, others to read, write, execute)
2: user
3: group
4: size
5: date/time last modified
6: name of file or directory
  - how to sort by date ascending / descending  
ls -t
## creating files
1. use 'touch somefile' to create a new file
  - what are the contents of this file ?  
file is empty--no contents
  - what is the size of this file ?  
0 bytes
  - read the description of touch in the man file
1. create another file using 'echo hello > anotherfile'
  - what are the contents of this file ?  
"hello"
  - what is the size of this file ?  
6 bytes
1. list the contents of the current directory ordered by date/time below  
-rw-r--r-- 1 edanthinne domain users 5354 Jun  5 15:32 README.md  
-rw-r--r-- 1 edanthinne domain users 5313 Jun  5 15:32 README.md~  
-rw-r--r-- 1 edanthinne domain users    6 Jun  5 15:29 anotherfile  
-rw-r--r-- 1 edanthinne domain users    0 Jun  5 15:25 somefile  
drwxr-xr-x 3 edanthinne domain users 4096 Jun  5 14:37 this  
1. touch somefile again
  - which file was last modified now?  
somefile was last modified after touch somefile
1. touch anotherfile
  - which file was last modified now?  
anotherfile
  - did the contents or size change at all?  
no, size and contents remained constant
1. what does 'cat anotherfile' do?  
shows the contents of anotherfile
1. what does 'echo more stuff >> anotherfile' do ?  
adds "morestuff" to the content of anotherfile
  - cat the file again
1. try 'echo clean slate > anotherfile'
  - what is the difference between > and >> ?q  
the > replaces the contents of the file, while >> simply adds content to existing content
1. copy anotherfile to the 'this' directory using cp, but name it file2
  - copy the command you used here  
cp anotherfile this  
mv anotherfile file2  
in one command: cp anotherfile this/file2
  - skim the man page for cp. What does -r do?  
the -r copies directories recursively--means that it copies the contents of directories and its subdirectories, so that cp doesn't skip directories
1. use 'mv' to move somefile to 'this'
  - list the contents of the 'this' dir here  
file2  is  somefile
1. copy all files from the 'this' dir to the 'this/is/a/directory' dir in one command.
  - show that command here  
cp this/* this/is/a/directory
  - explain what each term doesthi  
cp = copy; this = the source; this/is/a/directory = the destination
1. copy everything (including directories) from the this directory into a 'that' directory
  - show your command here  
cp -r this that
  - explain what each term does  
cp = copy; -r = recursively (to ensure that cp command does not skip directories); this = source; that = destination
1.  brace expansion is the use of curly braces '{' and '}' to repeat this for every term between the braces:
  - what does "cp this/is/a/directory/{somefile,copyofsomefile}" do ?  
it creates a copy of somefile called copyofsomefile (located in this/is/a/directory directory)
=======
  - what are the commands you used?
  - read the mkdir man page to find out which switch to use to create those directories in one command
  - change into the new directory. note the command you use here
1. type "cd -"
  - What did that do?
1. type "cd ~"
  - What did that do?
  - go back to the directory containing this file. note the command you use.
1. copy the output of the command "history" below.
  - what are the numbers before the commands?
  - what happens when you use the command "!<number>" ?
  - if you ended up away from this directory, get back to the one containing this file
  - copy the output of the 'pwd' command here. What does that do?
1. use the 'ls' command to list the contents of the current directory
  - what does 'ls ~' show you
  - what does 'ls .' show you
  - what does 'ls ..' show you
  - what does 'ls /' show you?
  - what does 'ls this/../this/is../is/' show you? explain why.
  - skim the man page
  - what switch do you use for the long listing
  - what do the columns mean?
  - how to sort by date ascending / descending

## creating files
1. use 'touch somefile' to create a new file
  - what are the contents of this file ?
  - what is the size of this file ?
  - read the description of touch in the man file
1. create another file using 'echo hello > anotherfile'
  - what are the contents of this file ?
  - what is the size of this file ?
1. list the contents of the current directory ordered by date/time below
1. touch somefile again
  - which file was last modified now?
1. touch anotherfile
  - which file was last modified now?
  - did the contents or size change at all?
1. what does 'cat anotherfile' do?
1. what does 'echo more stuff >> anotherfile' do ?
  - cat the file again
1. try 'echo clean slate > anotherfile'
  - what is the difference between > and >> ?
1. copy anotherfile to the 'this' directory using cp, but name it file2
  - copy the command you used here
  - skim the man page for cp. What does -r do?
1. use 'mv' to move somefile to 'this'
  - list the contents of the 'this' dir here
1. copy all files from the 'this' dir to the 'this/is/a/directory' dir in one command.
  - show that command here
  - explain what each term does
1. copy everything (including directories) from the this directory into a 'that' directory
  - show your command here
  - explain what each term does
1.  brace expansion is the use of curly braces '{' and '}' to repeat this for every term between the braces:
  - what does "cp this/is/a/directory/{somefile,copyofsomefile}" do ?
>>>>>>> master
  - here is [a good link](http://linuxcommand.org/lc3_lts0080.php) that explains it better than I can

## basic utilities
There are a number of basic utilities that you will encounter commonly on a linux system commandline. There are a million useful ones, but I will just go through a couple.
1. type 'less README.md'. use 'q' to quit
<<<<<<< HEAD
  - what is the advantage of 'less' over 'cat'  
less begins at the top of the document and allows the user to scroll from the top
  - when in 'less', type '/touch' followed by 'n' and 'N'. what does this all do?  
says "pattern not found" 
finds/highlights all occurences; 'n' skips forward and 'N' skips backwards
1. what does the output of 'ls | sort' represent?  
the output lists the files/directories in file system in sorted, alphabetical order
  - the '|' is called a pipe and takes the output of ls and sends it into the sort command. This is one ofthe most powerful concepts of the Linux commandline. You can chain piped commands together to do all kinds of useful things.
1. what does 'find .' do ?  
finds all files in current directory and all subdirectories
1. what does 'find . | grep "rf"' do?q  
finds instances in directory or subdirectory with an occurence of "rf" (located "./anotherfile")
1. what does the ps command do? What do you see when you do 'ps aux'  
ps = process system  
provides information on currently running processes  
you see the process identification numbers, TTY or computer terminal, CPU time the process has been running, and CMD or name of command that launched the process
 - what about 'ps aux | grep root' ?  
finds all process owned by yser, or root
 - what about 'ps aux | grep bash' ?  
finds all processes started within bash.
1. what does 'grep -rin hello .' do?  
locates all instances of "hello" in this file
the -i signifies ignore case  
the -r signifies recursively  
the -n shows the line number within the input file of the output
1. type 'dmesg'. what is all this stuff?  
shows kernal messages, or messages that show hardware devices the OS can detect and configure
 - type 'dmesg | tail'   what is different?  
the output is shorter because it only displays the bottom part of the total dmesg content
 - type 'dmesg | tail -f'   what is different?  
this worked the same for me as dmesg | tail. In theory, I believe, the addition of -f should make the output display as it goes along
 - before quitting the above command, unplug and replug in your mouse. Did any new lines appear?  
1. type 'netstat'
 - how would you use grep to see only tcp connections ?  
netstat | grep tcp
=======
  - what is the advantage of 'less' over 'cat'
  - when in 'less', type '/touch' followed by 'n' and 'N'. what does this all do?
1. what does the output of 'ls | sort' represent?
  - the '|' is called a pipe and takes the output of ls and sends it into the sort command. This is one ofthe most powerful concepts of the Linux commandline. You can chain piped commands together to do all kinds of useful things.
1. what does 'find .' do ?
1. what does 'find . | grep "rf"' do?
1. what does the ps command do? What do you see when you do 'ps aux'
 - what about 'ps aux | grep root' ?
 - what about 'ps aux | grep bash' ?
1. what does 'grep -rin hello .' do?
1. type 'dmesg'. what is all this stuff?
 - type 'dmesg | tail'   what is different?
 - type 'dmesg | tail -f'   what is different?
 - before quitting the above command, unplug and replug in your mouse. Did any new lines appear?
1. type 'netstat'
 - how would you use grep to see only tcp connections ?
>>>>>>> master
