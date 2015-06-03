# git-linux-practice
practice repo to learn git and linux

## basic git
'Git' is the Source Control Management (SCM) system we use at balihoo to allow everyone to work on the same code together while maintaining a history of everything we change.
To work effectively, it is important to know it well. To get to know it, you'll need to use it a lot, and it makes most sense to get to try thing out in a test repository.
The best way to get answers on how to use git is the official documentation:

    $ man git

to get out of that, just hit 'q'. These 'man' pages exist for almost any linux command and will be the quickes way to get information on a command.
Man works with any of git's subcommands as well. Try the below and skim the description (don't bother reading all the rest right now)

    $ man git branch
    $ man git checkout

Make a note of any often mentioned terms that are not clear right here in this file:

And ask me about them. I can tell you about things like 'remote tracking branches' and what "the current HEAD" means.
Once you understand them, add the notes to this file as well. Do this whenever you have a question about anything in here;
 - put your question in this file in the relevant section
 - get an answer from a man page, me, google or someone else (in that order)
 - put the answer here with the question.

1. Create a branch for yourself using 'git branch'
    - what command can you use to show all the branches ?
    - how does it indicate the current branch ?
1. enter this new branch using 'git checkout'
    - how can you use 'git checkout' to create AND enter a new branch at the same time?
1. save this file
    - explain what you see with 'git status'
    - explain what you see with 'git diff'
1. commit this file to your branch using 'git add' followed by 'git commit'.
    - what does the -a option of git commit do?
    - what does the -m option of git commit do?
    - save this file again with the answers to the above two questions, but now using 'git commit' with the a and m options

