# Git merging and conflicts

Making changes in a git repo and pushing them to github is mostly something you can do without too many issues. However, when more people use the same repository, you can run into conflicts.
In this section we're going to create some situations where this is the case, and resolve those conflicts without losing any changes

## conflicts with someone else's code in the same branch

1. Open another terminal and clone this repository into a different directory:

    $ git clone https://github.com/balihoo-gens/git-linux-practice.git the-other-git-linux-practice

1. enter this repo
    cd the-other-git-linux-practice
1. checkout your branch
1. open the file called 'conflict' in your editor
1. add a sentence of your choosing to the bottom of the file
1. save and close the file
1. commit your changes
1. push your changes to github (origin)
1. cd to the directory of your other repository (called git-linux-practice)
1. use 'git branch' to make sure you are on your branch
1. open up the file called 'conflict' in your editor
1. note that the sentence you typed in your other clone is *not* here. (if it is, you are not in the right repo)
1. add a *different* sentence to the bottom of this file
1. save and close the file
1. commit your changes
1. Try to push your changes to github (origin)
  * why does this fail ?
1. use 'git pull' to get any changes from github
  * see that git complains about conflicts
1. open the file 'conflict' in your editor
  * notice that the changes you made are both in this file, surrounded by '<<<<<<<HEAD', '==========' and '>>>>>>>>>>>>'
  * Where does the section between HEAD and ===== come from ?
  * Where does the section between ====== and >>>>>> come from ?
1. Edit the file such that both of your sentences are in the file, but remove the lines git added
1. save and close this file and commit the changes with the message "resolved conflict"

## local conflicts across multiple files

## rebasing

## tree conflicts

