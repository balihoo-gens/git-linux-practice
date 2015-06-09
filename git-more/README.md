# Git. More Branching, Merging and Resolving Conflicts

Conflicts with changes from others are not really different from local conflicts, because most of the time feature development happens in a user specific branch. In other words, when you are actually changing code, you are almost never doing it in the same branch as someone else. The below exercises will cover the essentials of git branches to be comfortable working on a shared git repository without losing work or bothering your coworkers. Please make sure to copy any commands you use as well as (the first couple of lines) of the output. If you run into unexpected results, or anything that doesn't go right, go ahead and copy the bad output into a new file and try to commit that file to the repository.

## local branching
Making lots of local branches is an essential skill to using git effectively. Initially, it may help you to keep a pen and paper handy and maintain a drawing of the git tree.

1. Create a branch called GLP-001-AwesomeFeature
    - we use this naming convention here at Balihoo. GLP-001 would be your Jira story number, followed by a descriptive term
    - it is also convention to add the branch name to every commit message, in this form: "git commit -am "GLP-001-AwesomeFeature: fixed function foo, returning an empty array rather than null on error"
1. On this new branch, create a file called foofunc.js
1. Add this code into it

```
function foo() {
  //TODO: implement this
}
```

## local conflicts across multiple files

## rebasing

## tree conflicts

## reverting

# cherry-picking
