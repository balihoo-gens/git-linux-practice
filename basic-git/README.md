# Basic Git

'Git' is the Source Control Management (SCM) system we use at Balihoo to allow everyone to work on the same code together while maintaining a history of everything we change.
To work effectively, it is important to know it well. To get to know it, you'll need to use it a lot, and it makes most sense to get to try thing out in a test repository.
The best way to get answers on how to use git is the official documentation:

    $ man git

to get out of that, just hit 'q'. These 'man' pages exist for almost any linux command and will be the quickes way to get information on a command.
Man works with any of git's subcommands as well. Try the below and skim the description (don't bother reading all the rest right now)

    $ man git branch
    $ man git checkout

Make a note of any often mentioned terms that are not clear right here in this file:

branch = represents independent line of development--to request brand new working directory
repository = where history of work is stored
fork = take source from someone's repository and apply own changes (create a copy, do work, commit or store changes)
commit = stores the contents of the index in a new commit w log messages describing changes
local vs remote = 
checkout = navigate branches created by git branch, updates files in directory
merged = join development histories together
tarball = 
master = the default head in every repository
commit messages = to communicate with the rest of the team
remote tracking branches = 
HEAD = current snapshot
the current HEAD = the current head, commit object

And ask me about them. I can tell you about things like 'remote tracking branches' and what "the current HEAD" means.
Once you understand them, add the notes to this file as well. Do this whenever you have a question about anything in here;
 - put your question in this file in the relevant section
 - get an answer from a man page, me, google or someone else (in that order)
 - put the answer here with the question.

1. Create a branch for yourself using 'git branch'
    - what command can you use to show all the branches ?
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-a shows all branches
    - how does it indicate the current branch ?
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;current branch is highlighted with an asterix
1. enter this new branch using 'git checkout'
    - how can you use 'git checkout' to create AND enter a new branch at the same time?
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git checkout -b <new-branch> 
		(The -b instructs to run new branch before)
1. save this file
    - explain what you see with 'git status'
		Changes not staged for commit and untracked files in branch new-branch aka shows state of the project
    - explain what you see with 'git diff'
		shows changes to (this) file
1. commit this file to your branch using 'git add' followed by 'git commit'.
    - what does the -a option of git commit do?
		tells command to automatically stage files that have been modified/deleted
    - what does the -m option of git commit do?
		lists changes not staged and untracked files
    - save this file again with the answers to the above two questions, but now using 'git commit' with the a and m options
    - note the 7 digit number git gives you when you commit. This is the commit id, also known as the SHA. The SHA is used to identify specific commits.
    - why do you always need to 'git add' new files ?
		must add a file for it to be committed--needs to get to staging area to be committed
1. use 'git log' to see the commit history.
    - what does the --oneline option do ?
		displays a condensed version of the information, showing only the SHA and the commit message
    - what does the -n option do ?
    - insert the output of 'git log --oneline -n 3' below
		fatal: unrecognized argument: --online
    - save this file
1. use 'git diff' to show your uncommitted changes
    - what are lines starting with + and - ?
		lines starting with a + are highlighted green and include uncommitted changes
    - use git log and pick the SHA of some commit from the list.
    - what does 'git diff <SHA>..HEAD' tell you? Try it with several SHAs
		shows updates before/after commit at that particular time??
    - what is HEAD ?
		the current branch
    - also try the diff between two SHAs
		git diff d35be19 5d075ef
1. commit these changes with the message "before first push"
1. push your branch up to github using 'git push'
    - what is 'origin' ?
		remote repository URL distinguished by keyword origin
    - what is the -u option for when using 'git push'
		set upstream; adds tracking reference

