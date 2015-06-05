# Linux file system

In Linux, everything is a file, or at least can be treated like one. It is important to know how to navigate the file system effectively and interact with files.

## Navigation
1. create the following directory structure here: this/is/a/directory
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
  - here is [a good link](http://linuxcommand.org/lc3_lts0080.php) that explains it better than I can

## basic utilities
There are a number of basic utilities that you will encounter commonly on a linux system commandline. There are a million useful ones, but I will just go through a couple.
1. type 'less README.md'. use 'q' to quit
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
