# Git. More Branching, Merging and Resolving Conflicts

Conflicts with changes from others are not really different from local conflicts, because most of the time feature development happens in a user specific branch. In other words, when you are actually changing code, you are almost never doing it in the same branch as someone else. The below exercises will cover the essentials of git branches to be comfortable working on a shared git repository without losing work or bothering your coworkers. Please make sure to copy any commands you use as well as (the first couple of lines) of the output. If you run into unexpected results, or anything that doesn't go right, go ahead and copy the bad output into a new file and try to commit that file to the repository.

## local branching
Making lots of local branches is an essential skill to using git effectively. Initially, it may help you to keep a pen and paper handy and maintain a drawing of the git tree.

1. Create a branch called GLP-001-AwesomeFeature
    - we use this naming convention here at Balihoo. GLP-001 would be your Jira story number, followed by a descriptive term
    - it is also convention to add the branch name to every commit message, in this form: "git commit -am "GLP-001-AwesomeFeature: fixed function foo, returning an empty array rather than null on error"
1. On this new branch, create a file called listfunc.js
1. Add this code into it

```
function listof(n) {
  //TODO: implement this function such
  //that it returns an array of 1 through n
}
```
1. commit this file with a well formatted commit message
1. while on branch GLP-001-AwesomeFeature, create a new branch called GLP-001-AttemptOne
1. on this new branch, add another function to this file, that adds two numbers.
    - save and commit this implementation
    - implement the listof using a for loop
    - save and commit with a good message
    - use the --oneline and -n options of 'git log' to show the last 3 commits
    - insert that output here
1. switch to the GLP-001-AwesomeFeature
    - use cat to verify your implementation is not here
1. create a new branch off here called GLP-001-AttemptTwo
1. on this new branch, implement the function using recursion (google that a little. it means having a function call itself)
    - don't worry about this working. just make one attempt; being able to use recursion is not important right now.
    - save and commit this implementation
1. Go back to the AwesomeFeature branch
    - what would have happened if you would have moved between branches without committing first?
1. Create a new branch called GLP-001-BothAttempts
    - try to merge both Attempt branches into this branch
    - Open the listfunc.js in your editor. Let's decide that this is too hard to deal with right now. We just want to go back!
    - use 'git merge --abort' to undo the partial merge
    - use cat to show the contents of the listfunc.js file
    - which changes are in here now?
1. Luckily for us, we did this failed merge in another branch called "BothAttempts". Now we just want to get rid of it.
    - try to delete this branch with 'git branch -d GLP-001-BothAttempts'
    - why does this fail?
    - go back to GLP-001-AwesomeFeature and try to delete it now.
    - why does it fail now? What is git trying to protect you from?
    - We know we want to get rid of it though, so try the suggested command with a capital -D
    - insert the output of 'git branch' below

## rebasing
Branching in git is very convenient and a nice way to keep all your work organized and separated. However, everyone that branches a lot ends up with a lot of branches and commits that need to be brought back together in a clean and organized manner. One of the best tools to do that is called 'rebase'. Rebasing is very powerful and can do many things, including some bad ones that can cost you work. So, best to learn well how it works.

It would not be surprising if something goes wrong during these exercises and things don't work as expected. When this happens, make a note of that here and paste in the last 5 commands from your command history.

1. Read the first page of the man page for 'git rebase'.
    - stop reading when overwhelmed or confused. It is ok if this is right at the beginning. What is important to understand about rebase is this: it takes your local commits and applies them one-by-one on top of the branch you specify.
    - go back to the man page and review the first 4 graphs
1. Create a new branch, once again called GLP-001-BothAttempts
1. in this new branch, type 'git rebase GLP-001-AttemptOne'
    - check git log to see what commits you now have here
1. now type 'git rebase GLP-001-AttemptTwo'
    - note the failure. How does 'git status' indicate what state your repository is in now?
    - do a 'git branch'. What branch are you on?
    - abort the rebase.
        - what command did you use?
        - what does 'git status' show now?.  What is different between the previous status?
        - what branch are you on?
1. One more time. Rebase the AttemptTwo branch again.
    - Observe that it says "Patch failed at 0002". This 'patch' is the application of the second commit from the AttemptOne branch, to this Both branch.
    - Let's say that you really want this merged, but you don't really care for this patch that fails to apply. We can skip it! use 'git rebase --skip' to skip this last patch. The rebase should complete.
    - show the output of git status
    - show the output of git branch
    - cat the contents of the js file
1. go back to the AwesomeFeature branch and delete the Both branch
1. go to the AttemptOne branch
    - add another function, that takes a 'name' parameter and returns 'hello <name>'
    - save and commit
1. Create a new GLP-001-BothAttempts branch off AwesomeFeature
1. Merge AttemptTwo into BothAttempts.
    - Use rebase or merge. show here what you used
1. Rebase AttemptOne into BothAttempts
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
