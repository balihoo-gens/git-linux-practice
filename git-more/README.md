# Git. More Branching, Merging and Resolving Conflicts

Conflicts with changes from others are not really different from local conflicts, because most of the time feature development happens in a user specific branch. In other words, when you are actually changing code, you are almost never doing it in the same branch as someone else. The below exercises will cover the essentials of git branches to be comfortable working on a shared git repository without losing work or bothering your coworkers. Please make sure to copy any commands you use as well as (the first couple of lines) of the output. If you run into unexpected results, or anything that doesn't go right, go ahead and copy the bad output into a new file and try to commit that file to the repository.

## local branching
Making lots of local branches is an essential skill to using git effectively. Initially, it may help you to keep a pen and paper handy and maintain a drawing of the git tree.


1. Create a branch called GLP-001-AwesomeFeature  
git branch GLP-001-AwesomeFeature
   - we use this naming convention here at Balihoo. GLP-001 would be your Jira story number, followed by a descriptive term
   - it is also convention to add the branch name to every commit message, in this form: "git commit -am "GLP-001-AwesomeFeature: fixed function foo, returning an empty array rather than null on error"
1. On this new branch, create a file called listfunc.js  
touch listfunc.js

1. Add this code into it

```
function listof(n) {
  //TODO: implement this function such
  //that it returns an array of 1 through n
}
```
1. commit this file with a well formatted commit message  
56f2ba8 GLP-001-AwesomeFeature: added and implemented function listof(n)
1. while on branch GLP-001-AwesomeFeature, create a new branch called GLP-001-AttemptOne  
git branch GLP-001-AttemptOne
1. on this new branch, add another function to this file, that adds two numbers.
   - save and commit this implementation
   - implement the listof using a for loop
	for(int i=1; i<=n; i++){  
		a[i] = i;}  
	return a;  
	}
   - save and commit with a good message  
39467bb GLP-001-AttemptOne: implementation of the listof using a for loop
   - use the --oneline and -n options of 'git log' to show the last 3 commits  
git log --oneline -n listfunc.js
   - insert that output here  
39467bb GLP-001-AttemptOne: implementation of the listof using a for loop  
039e14c GLP-001-AttemptOne: added a new function add(a,b) to listfunc.js that returns the sum of two numb  
56f2ba8 GLP-001-AwesomeFeature: added and implemented function listof(n)
1. switch to the GLP-001-AwesomeFeature  
git checkout GLP-001-AwesomeFeature
   - use cat to verify your implementation is not here
function listof(n) {
  //TODO: implement this function such
  //that it returns an array of 1 through n
	var a = new Array();
	for(int i=1; i<=n; i++){
		a[i] = i;}
	return a;
}
1. create a new branch off here called GLP-001-AttemptTwo  
git branch GLP-001-AttemptTwo
1. on this new branch, implement the function using recursion (google that a little. it means having a function call itself)  
function listof(var n) {  
if(n<=1)  
	return a;  
else{  
	return [n,listof(n--)];  
}}
   - don't worry about this working. just make one attempt; being able to use recursion is not important right now.
   - save and commit this implementation  
git commit listfunc.js -m "GLP-001-AttemptTwo: changed listof function from iterative to recursive"
1. Go back to the AwesomeFeature branch  
git checkout GLP-001-AwesomeFeature
   - what would have happened if you would have moved between branches without committing first?  
the changes would not correspond correctly--changes intended for other branches would carry over
1. Create a new branch called GLP-001-BothAttempts  
git branch GLP-001-BothAttempts
   - try to merge both Attempt branches into this branch  
git merge GLP-001-AttemptOne  
git merge GLP-001-AttemptTwo
   - Open the listfunc.js in your editor. Let's decide that this is too hard to deal with right now. We just want to go back!
   - use 'git merge --abort' to undo the partial merge
   - use cat to show the contents of the listfunc.js file
   - which changes are in here now?
the last changes I made--those implemented in AttemptTwo--are displayed
1. Luckily for us, we did this failed merge in another branch called "BothAttempts". Now we just want to get rid of it.
    - try to delete this branch with 'git branch -d GLP-001-BothAttempts'
    - why does this fail?  
fails because it is the branch I am currently on. 
    - go back to GLP-001-AwesomeFeature and try to delete it now.
    - why does it fail now? What is git trying to protect you from?  
claims that the branch is not fully merged
    - We know we want to get rid of it though, so try the suggested command with a capital -D  
git branch -D GLP-001-BothAttempts
    - insert the output of 'git branch' below  
  GLP-001-AttemptOne  
  GLP-001-AttemptTwo  
* GLP-001-AwesomeFeature  
  first-branch  
  master
g
## rebasing
Branching in git is very convenient and a nice way to keep all your work organized and separated. However, everyone that branches a lot ends up with a lot of branches and commits that need to be brought back together in a clean and organized manner. One of the best tools to do that is called 'rebase'. Rebasing is very powerful and can do many things, including some bad ones that can cost you work. So, best to learn well how it works.

It would not be surprising if something goes wrong during these exercises and things don't work as expected. When this happens, make a note of that here and paste in the last 5 commands from your command history.

1. Read the first page of the man page for 'git rebase'.
    - stop reading when overwhelmed or confused. It is ok if this is right at the beginning. What is important to understand about rebase is this: it takes your local commits and applies them one-by-one on top of the branch you specify.
    - go back to the man page and review the first 4 graphs
1. Create a new branch, once again called GLP-001-BothAttempts
git checkout -b GLP-001-BothAttempts
1. in this new branch, type 'git rebase GLP-001-AttemptOne'  
First, rewinding head to replay your work on top of it...  
Applying: creating a conflict  
Using index info to reconstruct a base tree...  
M	git-merge-and-conflict/conflict  
Falling back to patching base and 3-way merge...  
Auto-merging git-merge-and-conflict/conflict  
CONFLICT (content): Merge conflict in git-merge-and-conflict/conflict  
Failed to merge in the changes.  
Patch failed at 0001 creating a conflict  
The copy of the patch that failed is found in:  
   /home/balihoo.local/edanthinne/git-linux-practice/.git/rebase-apply/patch  

When you have resolved this problem, run "git rebase --continue".  
If you prefer to skip this patch, run "git rebase --skip" instead.  
To check out the original branch and stop rebasing, run "git rebase --abort".  

    - check git log to see what commits you now have here  
commits look the same:  
39467bb GLP-001-AttemptOne: implementation of the listof using a for loop  
039e14c GLP-001-AttemptOne: added a new function add(a,b) to listfunc.js that returns the sum of two n  
56f2ba8 GLP-001-AwesomeFeature: added and implemented function listof(n)  

1. now type 'git rebase GLP-001-AttemptTwo'  
First, rewinding head to replay your work on top of it...  
Applying: GLP-001-AttemptOne: added a new function add(a,b) to listfunc.js that returns the sum of two numbers  
Using index info to reconstruct a base tree...  
M	git-more/listfunc.js  
<stdin>:11: trailing whitespace.  
1. commit this file with a well formatted commit message  
warning: 1 line adds whitespace errors.  
Falling back to patching base and 3-way merge...  
Auto-merging git-more/listfunc.js  
Applying: GLP-001-AttemptOne: implementation of the listof using a for loop  

    - note the failure. How does 'git status' indicate what state your repository is in now?
    - do a 'git branch'. What branch are you on?  
on branch GLP-001-BothAttemps
    - abort the rebase.
        - what command did you use?
        - what does 'git status' show now?.  What is different between the previous status?
        - what branch are you on?
1. One more time. Rebase the AttemptTwo branch again.
    - Observe that it says "Patch failed at 0002". This 'patch' is the application of the second commit from the AttemptOne branch, to this Both branch.
    - Let's say that you really want this merged, but you don't really care for this patch that fails to apply. We can skip it! use 'git rebase --skip' to skip this last patch. The rebase should complete.
    - show the output of git status  
On branch GLP-001-BothAttempts  
Untracked files:  
  (use "git add <file>..." to include in what will be committed)  

	../basic-git/README.md~  
	../basic-git/TestEmailContent~  
	../file-system/README.md~  
	../file-system/anotherfile  
	../file-system/that/  
	../file-system/this/  
	../git-merge-and-conflict/README.md~  
	../git-merge-and-conflict/conflict~  
	../git-merge-and-conflict/the-other-git-linux-practice/  
	README.md~  
	listfunc.js~  
	md  

nothing added to commit but untracked files present (use "git add" to track)  

    - show the output of git branch
  GLP-001-AttemptOne
  GLP-001-AttemptTwo
  GLP-001-AwesomeFeature
* GLP-001-BothAttempts
  first-branch
  master

    - cat the contents of the js file
function listof(var n) {
  //TODO: implement this function such
  //that it returns an array of 1 through n
if(n<=1)
	return a;
else{
	return [n,listof(n--)];
}
}  

function add(var a, var b) {
//adds two numbers
return a+b;
}  

function add(var a, var b) {
//adds two numbers
return a+b;
}  

1. go back to the AwesomeFeature branch and delete the Both branch  
error: The branch 'GLP-001-BothAttempts' is not fully merged.  
If you are sure you want to delete it, run 'git branch -D GLP-001-BothAttempts'.  
git branch -D GLP-001-BothAttempts  
1. go to the AttemptOne branch  
git checkout GLP-001-AttemptOne
   - add another function, that takes a 'name' parameter and returns 'hello <name>'  
function name(var name){
return "hello "+ name;
}
   - save and commit
1. Create a new GLP-001-BothAttempts branch off AwesomeFeature
1. Merge AttemptTwo into BothAttempts.
   - Use rebase or merge. show here what you used  
git merge GLP-001-AttemptTwo
1. Rebase AttemptOne into BothAttempts  
First, rewinding head to replay your work on top of it...  
Applying: GLP-001-AttemptTwo: changed listof function from iterative to recursive  
Using index info to reconstruct a base tree...  
M	git-more/listfunc.js  
Falling back to patching base and 3-way merge...  
Auto-merging git-more/listfunc.js  
   - yup failed again. No big deal.
   - edit the script file to resolve the conflict. Prefer the implementation using recursion
   - now stage the script file using 'git add listfunc.js'. This is very important to record your changes. However, you should NOT commit the changes here, because that would create a new commit in the middle of a rebase, which is not what you want.
    - continue rebasing using 'git rebase --continue'
    - show the output of that command here.
    - show the contents of the script file.
    - does it contain what you expected?


Next time:

## local conflicts across multiple files

## tree conflicts

## reverting

# cherry-picking


